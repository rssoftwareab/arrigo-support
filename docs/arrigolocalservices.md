---
layout: main
title: Releases - Arrigo Local Services
description: Change Log
---

# Change Log

## Upcoming releases
## 1.1.202
*2021-12-10*
- Hotfix: Corrected return value when calling register in ssf service

## 1.1.201
*2021-12-10*
- Fix: Volumes fileInfo contains correct data.

## 1.1.194
*2021-12-08*
* Feature: legacy read/write/execute support in server side functions.
###### `async function context.legacy.read|write|execute`

A portal to the legacy (existing EXOscada) domain. Use these functions while you are waiting for the proper datasource interface for advanced read/write to variables. 
**Be careful! This is raw read/write. No access control at all.** Make sure that your client code (`OnManeuver`, `OnChanged`, `OnOpen`) does **NOT** send in the variables as strings. Define the variables in the serverside function. Make sure the variable values are within boundaries before write.

request/response Message type definition for  variable quality. 
```javascript
const  Request = 0,
        Response = 1,
        Update = 2,
        ErrorNotExist = 3,
        ErrorUnreachable = 4,
        Pending = 5,
        Expired = 6,
        AboutToExpire = 7,
        UnknownError = 8;
```

###### `read`
call read. The function returns immediately with an response array containing variable responses. Check the type for each response. If this is the first time the variable is read, the value is still pending, and type for object is 5, according to the definition above. You have  to manually enumerate and check if you need to read again, to make sure that every variable has its value before proceeding.
> If you set upp an interval in the view, which periodically calls the function, the type will update and client side can be updated when variables is read.
We strongly recommend that you use these functions with caution, as a last resort. Use expressions and OneShot bindings in OnOpen as long as you can. This is only for variables which you not know during compile time.

```javascript
async function readFromController(args, callInfo){
    const read = callInfo.context.legacy.read;
    const variables = ["Controller_A1.QSystem.Sec"];
    const readResult = await read(variables);
    console.log(readResult);
    return readResult;
}
```

variables contains an array of read results. Each entry is the response for corresponding read variable in the array sent in. 

```javascript 
[{
    "value": 40,
    "variable": "Controller_A1.QSystem.Sec",
    "type": 1,
    "timestamp": "2021-12-08T14:59:29.777131Z"
}]

```

###### `write`
Same as read. Only difference is that only one variable is possible to write at a time. The write method has same response object as above, but is not an array. 

```javascript
async function writeToController(args, callInfo){
    const write = callInfo.context.legacy.write;
    const variable = {variable: "Controller.DigOut(7)", value: 1};
    const writeResult = await write(variable);
    console.log(writeResult);
    return writeResult;
}
```

###### `execute`
This method can execute EXObasic snippets, or oneliners. This can be used for synchronizing controllers, block/unblock alarms e.t.c.
```javascript
async function blockAlarm(args, callInfo){
    const execute = callInfo.context.legacy.execute;
    const executeResult = await execute("UnreachableAlarms.Controller_A1.Block");
    console.log(executeResult);
    return executeResult;
}
```

## 1.0.186

*2021-11-26*

* Feature: Logs from Volume service is now timestamped

## 1.0.185

*2021-10-14*

* Feature: 'require' is now exposed in SSF function definitions (#3)

## 1.0.184

*2021-08-23*

* Fix: Access in area for users without ExplicitAccess

## 1.0.183

*2021-07-09*

* Fix: Reports for account
* Fix: Verbosity logging level

## 1.0.176

*2021-05-03*

* Fixed a bug in all services that could prevent them from starting up correctly

## 1.0.136

*2021-04-28*

* First release
