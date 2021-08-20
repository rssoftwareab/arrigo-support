#### arrigo-services-ssf

serverside functions service.

This service name is `ssf` and registers under `accounts.[accountName].services.ssf`.
The service is responsible for *exposing* user defined server side functions and *handle lifecycle events* for those functions.

Written in node 14. Source code on [Github](https://github.com/rssoftwareab/arrigo.services.ssf)

```dock
$>docker-compose up --build
```

or 

```
$>yarn install && yarn run dev && yarn run test
```

##### Commandline|Environment variables

| Name                                  | Description                           | Default                       |
| ------------------------------------- | ------------------------------------- | ----------------------------- |
| `env.KEY | argv.key | argv.k`         | The key(user) to run ssf instance     | *Mandatory*                   |
| `env.REALM | argv.realm | argv.r`     | The realm to connect to               | `realm1`                      |
| `env.URL | argv.url | argv.u`         | The url to wamp host                  | `wss://wamp.rssoftware.se/ws` |
| `env.ACCOUNT | argv.account | argv.a` | The account under which ssf registers | *Mandatory*                   |

##### [ssf].info

No arguments. Returns describing object of the below described methods

##### [ssf].register

| param  | type | Default            |
| ------ | ---- | ------------------ |
| `path` | args | Mandatory argument |
| `code` | args | Mandatory argument |
|        |      |                    |

THe Register method *registers* the exported methods from the code string sent in the `code` parameter. If invalid code is sent, the call throws exception. 

Any path is accepted. If same path is used, the before registered functions are overwritten without notice. 

##### [ssf].execute

| param         | type   | Default                                     |
| ------------- | ------ | ------------------------------------------- |
| `path`        | args   | Mandatory argument                          |
| `methodName`  | args   | Mandatory argument                          |
| `[kwargName]` | kwargs | Any kwarg to send to the method to execute. |

The execute method *executes* the provided methodName exported from the `path`. If no mehod exist, or no path exist, it throws exception. 

If method itself throws, the call thows as well. 

##### How stuff works

Each call to register results in a evaluation of the `code` parameter. The code sent in to the Register function is wrapped in a function body. the code block is executed and expects a result explained below.

Each time a `Serverside function` attribute is non empty in any EXOconfig file, that content is treated as a collection of *server side functions*. The attribute **must** export its functions through a `return` statement as the last statement in the attribute. 

###### Example of server side function block code

```javascript
function add(kwargs, callInfo){
  return kwargs.a + kwargs.b;
}

return { add }
```

The above example *defines* the function `add`, and at the bottom *exports* it. The `execute` call to the service takes a `path` and a `methodName` as parameters. The `methodName` is one of the exported names from the initial function export. 

##### callInfo parameter for a server side function

Each call to an exported server side function provides two arguments, always. 

The `kwargs` object.

This is the parameters sent in the `kwargs` key in the execute call. Examples below.

The `callInfo` object. 

| key       | type   | Description                                                  |
| --------- | ------ | ------------------------------------------------------------ |
| `context` | Object | Useful for talking with other services, internet, fetching data, get&set state, using the db and so on. |
| `details` | Object | The call details object, as described in the wamp protocol. Progressevents and callbacks for advanced server side functions is found here. See the docs for wamp protocol for more information. |
| `token`   | String | The callers token. This can be used to check access control, or sent along to another service as callmeta payload. |
| `path`    | String | The path for this function. This can be used to send to other services, to set the domain for the call. |



##### The `context`:

The context object is tied to the server side function code block through its path. the path is the id used when the code was registered in `[ssf].register` call. the `path` is used to define accesscontrol for calls and to bind the function to a scope. 

###### `async function context.state.get`

Gets a value from the state service for the path. It is a persistent value. The call returns the value or throws an exception.

Optional parameter `key`:

If provided, return the value for that key, instead of the whole object. The key parameter expects the file data to be JSON and to be of type Object with keys at root object level. 

Optional parameter `file`:

If provided, that file is read/written instead of the default state object path. 

```javascript
async function getStates(kwargs, callInfo){
    let result
    const state = callInfo.context.state
    
    //read setting from the functions state
	result = await state.get()
	
    //read setting from a specified file
    result = await state.get({ file: "Shared:/globalsettings.json" })
    
    //read setting from a key
    result = await state.get({ key: "mySetting" })
    
    //read setting from  a key in a specified file
    result = await state.get({ key: "mySetting", file: "Shared:/globalsettings.json" })
    
    return result
}

return { getStates }
```



###### `async function context.state.set`

Sets data in the state service for the path. When set, the data is stored persistent. However, if set is called without file argument, the value is bound  to the path. if the path is changed (any rename of file or parent files), the state will get lost. 

`key` and `file` params exactly as for `get`.

Mandatory parameter `data`:

When provided, this data is written to target. If used in combination with `key` , the data is written as value for that key. 

```javascript
async function setStates(kwargs, callInfo){
    const state = callInfo.context.state;
    
    //set simple data to the state for this path
    await state.set(23)
    
    //set complex data to the state for this path
    await state.set({ key1:"value1", key2:[1,2,3,4,5] })
    
    //set complex data to the state for this path
    await state.set({data:['a','b','c']})
    
    //set complex data for a key
    await state.set({data: [1,2,3], key:"key2" })
    
    //set complex data for a key in a file
    await state.set({data:[1,2,3], key:"key2", file:"Shared:/globalsettings.json" })
    
    //erase data for a key
    await state.set({data: null, key:"key1" })
    
    //erase state for the entire state
    await state.set(null)
    
    //erase state for a file (removes the file as well)
    await state.set({ data:null, file:"Shared:/globalsettings.json" })
    
    return 0
}
```



###### `async function context.db.[analogs|digitals|alarms|userlog].query`

Uses the attached projects database as default database. The database names is used. 

Mandatory parameter `sql`:

The SQL query. Do NOT concatenate SQL in where clauses. Use Parameters. Always. 

If `null`, `undefined` or *empty*, exception is thrown. 

Optional parameter `params`:

If SQL query contains parameters, they are provided here. 

Example

```javascript
async function getAlarms(kwargs, callInfo){
    const db = callInfo.db.analogs;
    const top10rows = await db.query("select top 10 * from [Analog Register]")
    
    //use named params
    let sql = 'SELECT * FROM AnalogRegister WHERE Name LIKE @name1 OR LIKE @name2'
    let params = [{name1: 'GT31'}, {name2: 'SV21'}])
    const match1 = await db.query(sql, params)

    //or use multiple with same name     
    sql = 'SELECT * FROM AnalogRegister WHERE Name EQUALS @name'
    params = [{key:'name' value: 'GT31'}, {key:'name', value: 'SV21'}])
    const match2 = await db.query(sql, params)
    
    return match2
}
return { getAlarms }
```



###### `async function context.fetch`

Fetches a resource. The port to  HTTP requests. Use this when you want to read or write any data from any web service. Any url is valid, as long as it can be fetched from the Arrigo Local server. 

As the server side functions runs under node, the npm package https://github.com/node-fetch/node-fetch is used to provide very sophisticated data.

A nice feature here is that the Arrigo Local API can be fetched from the server side function and any data from the API can be returned as a value from the server side function. 

```javascript
async function getFromHttp(kwargs, callInfo){
    const fetch = callInfo.fetch;
    
    //fetch the resource
    const response = await fetch('http://localhost/api/login')
    const json = await response.json();
    
    return json
}

return { getFromHttp }
```



