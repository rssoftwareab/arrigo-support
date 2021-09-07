# Preface

This document describes the components and files included/needed for setting up subscriptions against (and receiving updates from) variables in the EXO2019 system using the Arrigo Local API.

# General information

## Content type

The endpoints in the API only accept payloads with the content type ```application/json```. Posting with other content types (or without one) returns ```415 UNSUPPORTED MEDIA TYPE```.

# Authentication

## Token based authentication

The API uses token based authentication and you obtain a token by [logging in](#Logging in).

Whenever you access an authorized endpoint you must provide a valid auth token in the ```Authorization``` header of the request. To be specific the API uses the "Bearer" authentication scheme, which means that the ```Authorization``` header value must start with the text ```Bearer``` followed by a single whitespace and then the auth token you get when logging in:

```
Authorization: Bearer [your auth token]

Example:
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJhYW4iLCJqdGkiOiIzMzk4NzFjNy1mNmFjLTQwNjctYmUwNC1lNDIwZTc0YTFlNmQiLCJuYmYiOjE1NzkyNjI5MzAsImV4cCI6MTU3OTI2MzUzMCwiaWF0IjoxNTc5MjYyOTMwfQ.rreDnZpEWXFV7is7pi0Xl3oJ29zxXLF2zbeeGcWaOfg
```

Any attempt to access an authorized endpoint without the ```Authorization``` header set or with the wrong scheme returns ```401 UNAUTHORIZED```.

## Logging in

You log in by posting your credentials (username and password) to the login endpoint:

```json
POST /login
{
    "username": "[the username]",
    "password": "[the password]"
}

Example:
{
	"username": "demouser",
	"password": "abc123"
}
```

A successful login returns an Auth Token (hereafter called **AT**), a Refresh Token (hereafter called **RT**) and the expiration time of the AT in seconds:

```json
200 OK
{
	"authToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJhYW4iLCJqdGkiOiIzMzk4NzFjNy1mNmFjLTQwNjctYmUwNC1lNDIwZTc0YTFlNmQiLCJuYmYiOjE1NzkyNjI5MzAsImV4cCI6MTU3OTI2MzUzMCwiaWF0IjoxNTc5MjYyOTMwfQ.rreDnZpEWXFV7is7pi0Xl3oJ29zxXLF2zbeeGcWaOfg",
  "expires_in": 600,
  "refreshToken": "9d524a40-4c49-4bda-b6a5-8776e442311f"
}
```

The endpoint returns ```400 BAD REQUEST``` if a malformed payload was posted or ```401 UNAUTHORIZED``` if the credentials were invalid.

## Accessing authorized endpoints

Various endpoints in the API (```/graphql``` for example) requires a valid AT to be provided in the ```Authorization``` header.

*See [Token based authentication](#Token based authentication) for more information.*

Any attempt to access an authorized endpoint without the header or with an invalid token returns ```401 UNAUTHORIZED```.

## Refreshing the token

The AT you get when logging in is valid for 10 minutes by default. After the AT expires any requests using that token will return a ```401 UNAUTHORIZED```. But by using the AT together with the RT you got when logging in you can exchange your stale AT for a new one and get another 10 minutes of access.

You have the choice of either keeping track of the AT expiration time and do a preemptive refresh or refreshing when receiving a ```401 UNAUTHORIZED``` with the ```token-expired``` header set to ```true```.

The RT has a default expiration time of 60 days. This means that a RT cannot be used for refreshing after that, and that a new login is needed. But if you continuously use the API and refresh the AT you will basically never be logged out.

To get a new AT you post the RT to the refresh endpoint:

```json
POST /login/refresh
{
	"refreshToken": "[your refresh token]"
}

Example:
{
	"refreshToken": "9d524a40-4c49-4bda-b6a5-8776e442311f"
}
```

*Please note that although this is not an authorized endpoint you still have to provide the AT (you got together with the RT) in the ```Authorization``` header.*

A successful refresh returns a new AT and RT:

```json
200 OK
{
  "authToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJhYW4iLCJqdGkiOiI1MjBlNzE3MS1hODZiLTQ3ZjEtYTlkMC0zZTBmM2JhNTA5MWIiLCJuYmYiOjE1NzkxODcyMzUsImV4cCI6MTU3OTE4NzgzNSwiaWF0IjoxNTc5MTg3MjM1fQ.p4lNaP1dYYiFKHwzOQ2lBeih_PJbZf1mGH3b3DCIocs",
  "expires_in": 600,
  "refreshToken": "daf5e75e-4490-42df-9107-5b16e378e052"
}
```

The endpoint returns ```400 BAD REQUEST``` if the payload was malformed or ```401 UNAUTHORIZED``` if the AT or RT was invalid.

## Logging out

*By "logging out" we mean revoking the RT so it can no longer be used for creating new AT's.*
*AT's are not blacklisted when logging out! This means that it might possible to access authorized endpoints even after logout since the AT hasn't expired, but you cannot use that AT for refreshing. The AT will eventually expire and then become invalid.*

There are two ways of logging out:

* Post an empty request to the ```/logout``` endpoint with the currently active AT in the auth header.

* Post the RT as payload to the `/logout` endpoint.

  ```json
  POST /logout
  {
      "refreshToken": "[the refresh token]"
  }
  
  Example:
  {
  	"refreshToken": "9d524a40-4c49-4bda-b6a5-8776e442311f"
  }
  ```

*If both tokens are present in the request the AT takes precedence.*

A successful logout returns ```204 NO CONTENT```, no AT and invalid RT returns `400 BAD REQUEST` and if the AT is invalid token you get a ```401 UNAUTHORIZED```.

## Verifying a token

The verification endpoint can be used to verify if a specific AT was issued by the server, and if the token still is valid.

```json
POST /login/verify
{
	"authToken": "[the auth token]"
}

Example:
{
	"authToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJhYW4iLCJqdGkiOiI1MjBlNzE3MS1hODZiLTQ3ZjEtYTlkMC0zZTBmM2JhNTA5MWIiLCJuYmYiOjE1NzkxODcyMzUsImV4cCI6MTU3OTE4NzgzNSwiaWF0IjoxNTc5MTg3MjM1fQ.p4lNaP1dYYiFKHwzOQ2lBeih_PJbZf1mGH3b3DCIocs"
}
```

The endpoint returns ```204 NO CONTENT``` if the AT was issued by the server and if the token is still valid. All other cases returns ```400 BAD REQUEST```.

# ArrigoFolder

An ArrigoFolder file lists the [Pvl files](#Pvl files) that are exposed in an area and it also contains a reference to the [ArrigoFolderViews](#ArrigoFolderViews) file of the area.

You can name the file as you like as long as it has a `.rwaf` extension. Only one ArrigoFolder file can be used in an area so if you create more than one file the API will pick the first it finds (in lexicographical order).

The file is a std. ExoConfig xml file which must conform to a specified format with the following outline:

```xml
<?xml version="1.0" encoding="utf-8"?>
<EXOconfigData format="ArrigoFolder" version="2017.5.000.236">
  <Object type="ArrigoFolder">
    <Object type="GlobalArguments" />
    <Object type="PublVarFiles">
	  <Object type="PublVarFile" />
      <Object type="PublVarFile" />
        ...
        ...
    </Object>
    <Object type="FolderViewsFiles">
      <Object type="FolderViewsFile" />
    </Object>
  </Object>
</EXOconfigData>
```

## Reference

***This section should be considered obsolete but remains in this document for reference.***

*The `GlobalArgument`object is not used in the API (yet) and will not be explained further in this document.*

Properties of `PublVarFiles`:

| Property | Description                                                  |
| -------- | ------------------------------------------------------------ |
| Name     | Just the name of the list, really. Globally unique name in the ArrigoFolder.ExoXml |

Properties of `PublVarFile`:

| Property      | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| Name          | The name of the Pvl file. Must be unique (in the entire file) |
| File          | The virtual path to the Pvl file.                            |
| FileArguments | Any arguments to be passed to the Pvl file when opening it.<br />**Note!** Not used at this moment! |
| Comment       | Comment from the integrator.                                 |

A "complete" file might look like this:

```xml
<?xml version="1.0" encoding="utf-8"?>
<EXOconfigData format="ArrigoFolder" version="2017.5.000.236">
  <Object type="ArrigoFolder">
    <Object type="GlobalArguments">
      <Attribute name="Name">GlobalArguments</Attribute>
      <Attribute name="Comment">This folder contains all arguments for the Published Variable List files. The arguments can be sent to the Pvl file when it is used in run-time.</Attribute>
    </Object>
    <Object type="PublVarFiles">
      <Attribute name="Name">Published Variable List files</Attribute>
      <Attribute name="Comment">This folder contains all Published Variable List files for the area. Each file exposes variables with names for external applications using the EOS API.</Attribute>
	    <Object type="PublVarFile">
        <Attribute name="Name">Controller_A1</Attribute>
        <Attribute name="File">Area:\Controller_A1.Pvl</Attribute>
        <Attribute name="FileArguments"></Attribute>
        <Attribute name="Comment">A comment</Attribute>
      </Object>
    </Object>
    <Object type="FolderViewsFiles">
      <Attribute name="Name">Folder Views Files</Attribute>
      <Attribute name="Comment">This folder contains the Folder Views File. The file exposes Widgets and Link Icons for the Arrigo BMS UI.</Attribute>
      <Object type="FolderViewsFile">
        <Attribute name="Name">Ventilation</Attribute>
        <Attribute name="File">Area:\Ventilation.rwafv</Attribute>
      </Object>
    </Object>
  </Object>
</EXOconfigData>
```

# ArrigoFolderViews

An ArrigoFolderViews file contains the widgets and link icons definitions for the area.

The type of widgets available are:

* AlarmWidget
* ChartWidget
* DynamicWidget

## Reference

***This section should be considered obsolete but remains in this document for reference.***

```xml
<?xml version="1.0" encoding="utf-8"?>
<EXOconfigData format="ArrigoFolderViews" version="99.99.99.99">
  <Object type="ArrigoFolderViews">
    <Attribute name="Name">AS1_Dashboard</Attribute>
    <Object type="WidgetsFolder">
      <Attribute name="Name">Widgets</Attribute>
      <Attribute name="Comment">This folder contains all widgets for this area.</Attribute>
	  <Object type="Widget">
        <Attribute name="Name">Chart</Attribute>
        <Attribute name="WidgetType">ChartWidget</Attribute>
        <Attribute name="WidgetFile">Area:\VentilationChartWidget.rwtv</Attribute>
      </Object>
	  <Object type="Widget">
        <Attribute name="Name">Alarms</Attribute>
        <Attribute name="WidgetType">AlarmWidget</Attribute>
        <Attribute name="Filters">FilterAlarmPriority,FilterAlarmStatus</Attribute>
        <Attribute name="Package">eos-alarms</Attribute>
        <Attribute name="Feature">alarms</Attribute>
      </Object>
      <Object type="Widget">
	   <Attribute name="Title">Ventilation</Attribute>
        <Attribute name="Name">Ventilation</Attribute>
        <Attribute name="WidgetType">DynamicWidget</Attribute>
        <Attribute name="WidgetFile">Area:\VentilationWidget.rwlv</Attribute>
      </Object>
      <Object type="Widget">
        <Attribute name="Name">HeatingPump</Attribute>
        <Attribute name="Title">Heating Pump - Settings</Attribute>
        <Attribute name="WidgetType">DynamicWidget</Attribute>
        <Attribute name="WidgetFile">Area:\VentilationHeatPumpWidget.rwlv</Attribute>
      </Object>
      <Object type="Widget">
        <Attribute name="Name">HeatingBattery</Attribute>
        <Attribute name="Title">Heating Battery - Settings</Attribute>
        <Attribute name="WidgetType">DynamicWidget</Attribute>
        <Attribute name="WidgetFile">Area:\VentilationHeatBatteryWidget.rwlv</Attribute>
      </Object>

    </Object>
    <Object type="LinkIconsFolder">
      <Attribute name="Name">Link Icons</Attribute>
      <Attribute name="Comment">This folder contains all link icons for this area.</Attribute>
	  <Object type="LinkIcon">
		<Attribute name="Title">Dashboard</Attribute>
		<Attribute name="Name">Dashboard</Attribute>
		<Attribute name="Icon">Area:\dashboard.svg</Attribute>
		<Attribute name="Feature">dashboard</Attribute>
	  </Object>
	   <Object type="LinkIcon">
		<Attribute name="Title">Charts</Attribute>
		<Attribute name="Name">Charts</Attribute>
		<Attribute name="Icon">Area:\flag.svg</Attribute>
		<Attribute name="Feature">charts</Attribute>
		<Attribute name="LazyPackage">eos-charts</Attribute>
	  </Object>
    </Object>
  </Object>
</EXOconfigData>
```

# Default views and widgets

If you [query an area](#List files) which doesn't contain the ArrigoFolder and ArrigoFolderViews files the API will generate a default file for you. The default file contains an AlarmWidget with default filters applied.

# Pvl files

A Pvl file is basically just a list of variables that Arrigo BMS API should expose to "the outside".

The file is a std. ExoConfig xml file which must conform to a specified format with the following outline:

```xml
<?xml version="1.0" encoding="utf-8"?>
<EXOconfigData format="PublishedVariableList" version="2017.5.000.184">
  <Object type="PublishedVariables">
	<Object type="PublishedVariable" />
    <Object type="PublishedVariable" />
      ...
      ...
  </Object>
</EXOconfigData>
```

Properties of `PublishedVariables`:

| Property | Description                                                  |
| -------- | ------------------------------------------------------------ |
| Name     | Just the name of the list, really. Unsure of if it has to be a unique name in context of the names of the individual variables... |

Properties of `PublishedVariable`:

| Property    | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| Name        | The technical name of the variable. Example: "OutdoorTemp". Must be unique (in the list) |
| Description | The human-friendly description of the variable. Example: "The outdoor temperature at Main Street, Smalltown." |
| Unit        | The human-friendly unit of the value of the variable. Example: "°C" |
| Variable    | Technical address of the variable<br />(see [Variables](#Variables) for more info) |
| Writable    | Indicates if the variable should be writable (Yes/No)        |
| ReadAccess  | The minimum access level a user needs in the area for reading the variable |
| WriteAccess | The minimum access level a user needs in the area for writing to the variable<br />(*only applicable if Writeable=Yes*) |

A "complete" file might look like this:

```xml
<?xml version="1.0" encoding="utf-8"?>
<EXOconfigData format="PublishedVariableList" version="2017.5.000.184">
  <Object type="PublishedVariables">
    <Attribute name="Name">Controller_A1</Attribute>
	<Object type="PublishedVariable">
      <Attribute name="Name">Var1</Attribute>
      <Attribute name="Description">A writable variable</Attribute>
      <Attribute name="Unit">s</Attribute>
      <Attribute name="Variable">*MyController.WritableInteger1</Attribute>
      <Attribute name="Writable">Yes</Attribute>
      <Attribute name="ReadAccess">None</Attribute>
      <Attribute name="WriteAccess">Guest</Attribute>
    </Object>
    <Object type="PublishedVariable">
      <Attribute name="Name">Var2</Attribute>
      <Attribute name="Description">Real time clock: Second (0-59)</Attribute>
      <Attribute name="Unit">s</Attribute>
      <Attribute name="Variable">*%Controller%.QSystem.Sec</Attribute>
      <Attribute name="Writable">No</Attribute>
      <Attribute name="ReadAccess">None</Attribute>
      <Attribute name="WriteAccess">Guest</Attribute>
    </Object>	
  </Object>
</EXOconfigData>
```

## Variables

`PublishedVariable/Variable` must be a valid technical address which can be resolved to to a variable in a controller or a EXO Computer Signal. The `%Controller%` macro is supported, and will resolve to the controller/area folder the Pvl file is located in.

The star/asterisk (`*`) prefix of the address denotes a binding. This means that that the variable will be included in the [Subscription](#Subscriptions) of the Pvl file, and that value updates (for that variable) will be published to the client.

### Access

If the user lacks the minimum access level needed for reading a variable then no subscription will be set up for that variable. This also implies that you shouldn't create a variable with a higher access level on reading than on writing since this variable then effectively will be "filtered out".

# In the API

## List files

After logging in you need to get hold of the `folderId` of the folder you're interested in. Once you have the id you can query for the Pvl files in it. Only `UserAreas` have Pvl lists in them so you need to use an *inline fragment* on the `folder` in order to access the fields. The list exposes two fields:

| Name | Type    | Description                                                  |
| ---- | ------- | ------------------------------------------------------------ |
| name | String  | The technical name of the file is specified (as read from ArrigoFolder.ExoXml). |
| path | String! | A base64 encoded node path, later used for getting the contents of the file or setting up subscriptions. |

Example:


```json
{
  folder(id: "TGFuZHNrcm9uYQ==") {
    name
    ...on UserArea {
      publicVariableFiles {
        name
        path
      }		
    }
  }
}
```
returns
```json
{
  "data": {
    "folder": {
      "name": "Landskrona",
      "publicVariableFiles": [
        {
        	"name": "SystemAir",
        	"path": "TGFuZHNrcm9uYS5zeXN0ZW1haXIuZmlsZQ=="
        },
        {
        	"name": "ReginPvl",
        	"path": "TGFuZHNrcm9uYS5yZWdpbnB2bC5maWxl"
        }
      ]
    }
  }
}
```

## Getting file data

With the **path** and the query `node` you can request the rest of the static data from the Pvl: 


```json
{
  node(path:"TGFuZHNrcm9uYS5zeXN0ZW1haXIuZmlsZQ==") {
    content
    hash
  }
}
```
returns
```json
{
  "data": {
    "node": {
      "content": {
        "Cwl": {
          "type": "PublishedVariables",
          "attributes": {
            "Name": "SystemAir",
            "Title": "SystemAir",
            "Description": "",
            "Comment": ""
          },
          "children": [
            {
              "type": "PublishedVariable",
              "attributes": {
                "Name": "Second",
                "Title": "Second",
                "Description": "Real time clock: Second (0-59)",
                "Unit": "s",
                "Variable": "((undefined))",
                "Writable": "Yes",
                "ReadAccess": "Guest",
                "WriteAccess": "Guest",
                "Comment": "",
                "VisualFilter": "1"
              }
            }
          ],
          "Advise": {
            "A": [
              "0:0"
            ]
          },
          "AdviseRefs": {
            "A": [
              [
                0
              ]
            ]
          },
          "ElementRefs": [
            [
              [
                0
              ],
              4
            ]
          ]
        }
      },
      "hash": "ED9C0F49"
    }
  }
}
```

## Subscriptions

The **path** also lets you set up subscriptions for updates/advises from a Pvl file. There is a limit in the API of one update per second per variable to prevent clients from choking on massive and rapid update bursts. If you have a lot of bound variables in a file you can still get bursts of multiple updates simultaneously, but we guarantee that they don't come more frequent than in 1 second intervals.

You are also guaranteed to get an initial value/state for each bound variable directly when you start a subscription. If there is (or just recently has been) another ongoing subscription (by you or another user) which include one of "your" bound variables you will get the last sent update for that variable, otherwise you'll probably get a "[Value pending](#Update types)" result.

**Note!**
To consume subscriptions you need to have a GraphQL subscription compliant client (there are WebSockets and protocols and stuff driving it all in the background). [Apollo Client](https://github.com/apollographql/apollo-client) is a nice one for javascript environments. You can also use the built-in Playground UI of the API to do some exploratory testing (go to `http(s)://[your-server]/arrigo/api` to try it out).

### Authentication

When you set up a subscription you need to authenticate using the Auth Token you got when [logging in](#Logging in). This is to make the subscription stream unique.

The following snippet shows how to pass the AT when subscribing using [Apollo Client](https://github.com/apollographql/apollo-client):

```javascript
import { WebSocketLink } from 'apollo-link-ws';

const wsLink = new WebSocketLink({
  uri: `ws(s)://[your-server]/arrigo/api/graphql/ws`,
  options: {
    connectionParams: {
        Authorization: "Bearer [your authToken]"
    },
});
```

#### Token expiration

When an AT expires, the subscription stream is closed by the API and an error code is returned ("**INVALID_AUTH_TOKEN**"). If this happens you have [refresh](#Refreshing the token) the AT and setup the subscription again.

If you do a preemptive refresh you have to manually close the subscription and set it up again with the new AT.

### Starting a subscription

You start a subscription by passing the [valid](#workflow) **path** to the `subscriptions/data` query:

```json
subscription {
  data(path: "TGFuZHNrcm9uYS5zeXN0ZW1haXIuZmlsZQ==") {
    value
    path
    technicalAddress
    type
    timestamp
  }
}
```
Each advise update is then delivered, one at a time, in the following format:

```json
{
  "data": {
    "data": {
      "value": 12,
      "path": "Cwl.Advise.A[0]",
      "technicalAddress": "MyController.QSystem.Sec",
      "type": "Update",
      "timeStamp": "2019-09-26T12:00:12"
    }
  }
}
```

*See [Value updates](#value updates) for more info.*

### Update types

Each update contains a `type` field. The possible values are:

| Name             | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| Response         | Normal response                                              |
| Update           | Published advise update                                      |
| ErrorNotExist    | The requested variable doesn't exist in the current domain   |
| ErrorUnreachable | The requested variable exists but isn't reachable at this point in time |
| Pending          | The requested variable exists and is reachable but the Scada Function is waiting for an initial value |
| UnknownError     | An unknown error occurred when processing the request        |

### Gray- and blacklisted variable

The Scada Function running in the background has lists containing variables that cannot be reached for the moment (gray-listed) and variables that cannot be resolved (black-listed).

When subscribing to path's** containing gray- or black-listed variables, the time stamp field indicates when the variable was put in the list. Please note that gray-listed variables _might_ start publishing updates if they become available at a later point in time.

### Errors

If the path you're using is invalid an "Invalid path" error message is returned.

If the AT is invalid or has expired the stream is closed and an "INVALID_AUTH_TOKEN" error message is returned.

## Polling

The `data` query has two other fields (besides `content`) that are used when for polling variable values:

| Field              | Description                                               |
| ------------------ | --------------------------------------------------------- |
| variables          | List of [Value updates](#value updates)                   |
| minPollingInterval | The minimum polling interval you need to use (in seconds) |
| hash               | Hash code for the file                                    |

With a [valid](#workflow) **path** you poll all the exposed variables by with the query:

```json
{
  data(path: "TGFuZHNrcm9uYS5zeXN0ZW1haXIuZmlsZQ==") {
    variables {
        value
        path
        technicalAddress
        type
        timestamp
    }
    hash
  }
}
```

and get a response:

```json
{
  "data": {
    "data": {
    	"variables": [{
          "value": 14,
          "path": "Cwl.Advise.A[0]",
          "technicalAddress": "MyController.QSystem.Hour",
          "type": "Update",
          "timeStamp": "2019-09-26T14:26:44"
        },
        {
          "value": 26,
          "path": "Cwl.Advise.A[1]",
          "technicalAddress": "MyController.QSystem.Minute",
          "type": "Update",
          "timeStamp": "2019-09-26T14:26:44"
        },
        {
          "value": 44,
          "path": "Cwl.Advise.A[2]",
          "technicalAddress": "MyController.QSystem.Sec",
          "type": "Update",
          "timeStamp": "2019-09-26T14:26:44"
        }],
        "hash": "ED9C0F49"
    }
  }
}
```

Please note that you'll probably get a "[Value pending](#Update types)" result as a response to the first poll. Subsequent polls should return the actual value of the variables.

### Hash check (check if the file has been changed )

The `hash` field for the `data` query should be compared to the `hash` field for `node` query to verify that the file not has been changed.
If the hash is not equal , the source file has been changed and the content (node query) needs to be reload for full synchronization between content and the data.


```json
{
  node(path:"TGFuZHNrcm9uYS5zeXN0ZW1haXIuZmlsZQ==") {
    content
    hash
  }
}
```

### Poll interval

It is recommended that you poll at least every `minPollingInterval ` seconds to avoid variables from being un-advised in the Scada Function (and thus needing extra resources at the next poll to set up advises again). There is no limit on how often you can poll but the Api is throttled to 1 update/second/variable.

## Value updates

Each update contains the following fields:

| Field            | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| path             | The path (in the tree) to the updated variable reference     |
| value            | The actual value                                             |
| type             | Type of update.<br />*See [Update types](#update types) for more info* |
| timeStamp        | Timestamp of the update                                      |
| technicalAddress | Technical address of the variable                            |

**Note!**
The `technicalAddress` field *might* be removed in future versions so do not rely on it! Instead you should focus on using the `path` field in combination with the actual Pvl content (from `node`) to update your tree.



## Writing values

With the  **nodePath** and a **path**  you can use the `setData` mutation to change the value of variables:

```json
mutation {
  setData(
    nodePath: "TGFuZHNrcm9uYS5zeXN0ZW1haXIuZmlsZQ==",  
    path: "Cwl.Advise.A[1]", 
    value: "5")
}
```

*It is not possible to mutate multiple paths/variables in one single query.*

The mutation returns `true` if it went well, otherwise `false`.

**Note!**
It is up to you as the implementer to make sure that the correct datatype is used when writing to variables. Writing the string "5" to an integer will work fine but "five" will definitely fail. 

## Workflow

Just because you have an `uid` doesn't mean that you just can set up a subscription or poll directly and expect everything to work.

The `uid` is created/registered in the Scada Function when you do a `folder { ..on UserArea{ publicVariableList}}` query. Once that is done you can go ahead and either get the contents of the file or setup a subscription. As long as the Scada Function isn't restarted you can "reuse" the uid and start a subscription directly (without the `folder` query), even between "sessions".

But if the Scada Function doesn't know about the `uid` (or if it is invalid) you get a GraphQL error when querying either `data` or `subscription/data`.

# Arrigo Dynamics Client

The repository for the client is located on https://github.com/rssoftwareab/arrigo-dynamics-client/tree/master. It is free to use, and contributions to the code base is welcome. 

To get up and running with a client, make sure you have git installed and clone the repository in your favorite folder

````
git clone https://github.com/rssoftwareab/arrigo-dynamics-client.git
````

Then, make sure all dependencies are installed

```
yarn install
```

And then, modify `/src/config/config.ts` with the correct account and password, and the correct path to the server. 

```typescript
export const config: any = {
  auth: {
    account: process.env.ACCOUNT || "",
    password: process.env.API_PASSWORD || "exo",
    username: process.env.API_USERNAME || "ReginSe",
  },
  url: process.env.URL || "https://services.regin.se/ci/eos_beta/api/",
  ws: process.env.WS || "ws://172.18.149.35/eos_beta/api/graphql/ws",
}
```

or simply set the environment variables in the shell. 

Run the example

```
yarn example
```

And view the output. 

The example is located in `src/examples/index.ts`

# Accessing the API from the command line

The following section contains a couple of examples/snippets on how to access the API from the command line.

## Using Power Shell

### Logging in

```powershell
$url = "https://services.regin.se/ci/arrigo/api/login"

$headers = @{
  "Content-Type" = "application/json"
}

$body = @'
{
  "username": "user",
  "password": "password"
}
'@

# Convert the response to Json and store it in a variable
$loginResponse = Invoke-WebRequest -Uri $url -Method POST -Body $body -Headers $headers | ConvertFrom-Json
```

#### Output

None, but the response is stored in a variable.

### Getting the root folder

```powershell
$url = "https://services.regin.se/ci/arrigo/api/graphql"

# Use the authToken from the loginResponse
$headers = @{
  "Content-Type" = "application/json"
  "Authorization" = "Bearer $($loginResponse.authToken)"
}

$body = @'
{
  "query": "{folder {name}}"
}
'@

$response = Invoke-WebRequest -Uri $url -Method POST -Body $body -Headers $headers | ConvertFrom-Json

# Write the root folder name
Write-Host $response.data.folder.name
```

#### Output

`account`

### Iterating sub-folders

```powershell
$url = "https://services.regin.se/ci/arrigo/api/graphql"

# Use the authToken from the loginResponse
$headers = @{
  "Content-Type" = "application/json"
  "Authorization" = "Bearer $($loginResponse.authToken)"
}

$body = @'
{
  "query": "{folder{name folders{edges{node{name}}}}}"
}
'@

$response = Invoke-WebRequest -Uri $url -Method POST -Body $body -Headers $headers | ConvertFrom-Json

# Iterate over the sub-folders and write their names
$response.data.folder.folders.edges | ForEach-Object {Write-Host $_.node.name}
```

#### Output

```
First folder
Second folder
Third folder
```

## Using curl

*These examples/snippets requires [jq](https://stedolan.github.io/jq/) to be installed.*

### Logging in

```bash
# Store the output of the entire operation using command substitution.
# The curl output is piped to jq to get the authToken from the Json content.
# The jq output is piped to sed to remove the double quotes around the authToken.
authToken=$(curl https://services.regin.se/ci/arrigo/api/login \
  -H "Cache-Control: no-cache" \
  -H "Content-Type: application/json" \
  -d '{
	"username":"user",
	"password":"password"
  }' | jq '.authToken' | sed -e 's/^"//' -e 's/"$//')
```

#### Output

None, but the `authToken` is stored in a variable.

### Getting the root folder

```bash
# Use the authToken from the login request.
# The curl output is piped to jq to get the root folder name.
curl https://services.regin.se/ci/arrigo/api/graphql \
  -H "Cache-Control: no-cache" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $authToken" \
  -d '{
	"query":"{folder {name}}"
  }' | jq '.data.folder.name'
```

#### Output

`"account"`

### Iterating sub-folders

```bash
# Use the authToken from the login request.
# The curl output is piped to jq to iterate over the sub-folders and getting their names.
curl https://services.regin.se/ci/arrigo/api/graphql \
  -H "Cache-Control: no-cache" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $authToken" \
  -d '{
	"query":"{folder{name folders{edges{node{name}}}}}"
  }' | jq '.data.folder.folders.edges[].node.name'
```

#### Output

```
"First folder"
"Second folder"
"Third folder"
```

