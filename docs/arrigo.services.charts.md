# arrigo.services.charts

To save a custom configuration for a chart widget we need a backend service that saves data locally on the EXOscada server. 

This service is installed on our beta server (https://services.regin.se/ci/arrigo_beta) for a first test.



The service has three wamp procedures to manage the chart configurations.

accounts.[account].services.charts.list

accounts.[account].services.charts.get

accounts.[account].services.charts.set

## Procedure results

All procedures returns a generic Result object:

| Name  | Type                               | Description       |
| ----- | ---------------------------------- | ----------------- |
| type  | string                             | "fail"/"success"  |
| value | *depends on the invoked procedure* | The actual result |

## list

Returns a list of chart configurations metadata for an area. The list includes all private and public configurations.

| Param    | Type   | Description                          |
| -------- | ------ | ------------------------------------ |
| folderId | string | A base64 encoded id for the UserArea |

Returns a list of Elements:

| Name           | Type     | Description                                                  |
| -------------- | -------- | ------------------------------------------------------------ |
| name           | String   | The name/title of the configuration                          |
| id             | String   | The configuration id                                         |
| public         | bool     | Indicates if the configuration is a public or private configuration |
| lastAccessTime | DateTime |                                                              |
| lastWriteTime  | DateTime |                                                              |

### Example

```javascript
const list = session.call('accounts.[account].services.charts.list', ['QVMc=']);

// list =>
// [
//   {
//     type: "success",
//     result:[
//     {
//       name: "my_private_config",
//       id: "QVMx.VaqKB6YwcY",
//       public: false,
//       lastAccessTime: "2021-02-15T20:45:30Z",
//       lastWriteTime: "2021-02-11T12:15:22Z" 
//     	},
//		{
//       name: "public_config_no_1",
//       id: "QVMx.TXlOaWNlQ2hhcnQ=",
//       public: true,
//       lastAccessTime: "2021-02-15T20:45:30Z",
//       lastWriteTime: "2021-02-11T12:15:22Z" 
//     	 }
//		 ]
// ]
```

## get

Returns the content for a chart configuration.

| Param | Type   | Description                                                  |
| ----- | ------ | ------------------------------------------------------------ |
| id    | String | A base64 encoded id for the configuration. Use the id from [`list`](#list) |

### Example

```javascript
const content = session.call('accounts.[account].services.charts.get', ['QVMx.VaqKB6YwcY']);

// content =>
// {
//   {
//     type: "success",
//     result:
//     {
//       ...the std chart config content...  
//     }
//   }
// }
```

## set

Saves a chart configuration for an area.

| Param    | Type   | Description                                                  |
| -------- | ------ | ------------------------------------------------------------ |
| folderId | String | A base64 encoded id for the UserArea                         |
| name     | String | Name/title for the configuration                             |
| content  | String | The chart configuration content                              |
| public   | bool   | Indicates if the configuration should be saved as public or private configuration |
| id       | String | The configuration id. Leave this argument to create a new configuration.<br />Use the id from [`list`](#list) to save an existing configuration |

### Example

```javascript
const result = session.call('accounts.[account].services.charts.set', ['QVMx', 'My nice chart config', '..the chart content...', false, 'QVMx.VaqKB6YwcY']);

// result =>
// {
//   {
//     type: "success",
//     result: {id}
//   }
// }
```

## Connection

To access the chart procedures a valid jwt must be set to `session._options.authid`

```javascript
const url = "wss://services.regin.se/ci/arrigo_beta/api/wamp/";
const realm = "realm1";

var session = new autobahn.Connection({
    url: url,
    realm: realm,
    authmethods: ['anonymous']
});

 session._options.authid = jwt;
```