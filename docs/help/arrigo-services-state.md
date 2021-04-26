#### arrigo-services-state

This is a micro service for getting and setting metadata or any object or buffer.

It is used from the server side functions or any other service which needs to keep a state of anything. 

THe implementation of state service stores the state as JSON files on disk if keys are used for the file. If no keys are used, they are treated as text files. If binary data needs to be stored as state, we suggest base64 encoding the data before setting the state. 

The state service base its storage location around an Arrigo path. This path is used for determine the callers access based on the token sent along the requests. if only path is provided, this means that it is up to the state service to store the information in any format anyware, as long as it keeps track of it persistent between run times. If the `file` attribute is provided, that file is used for storage. 

##### [stateservice].get

| params | type   | Default |
| ------ | ------ | ------- |
| `path` | args   | none    |
| `key`  | kwargs | null    |
| `file` | kwargs | null    |

##### [stateservice].set

| params | type   | Default |
| ------ | ------ | ------- |
| `path` | args   | none    |
| `data` | args   | none    |
| `key`  | kwargs | null    |
| `file` | kwargs | null    |

##### mandatory argument `path` in args in get and set method

Used for accesscontrol, resolve of relative file paths, and so on. if not provided, the state service throws exception. 

This is also the default file name in the global state folder. simply use the path b64decoded as filename. 

Default settings location is in Proj volume with path  `/Arrigo/state/`.

##### optional argument `key` in kwargs in get and set method

If provided, this means that both get and set will preprocess and cut out the value part of the object if any. When setting with a key, this probably means that the file will need to be read parsed updated with key content and written to volume. If keys are used, the underlying storage format is JSON files. 

If no key provided, technically the state get/set method can handle any text data.

##### optional argument `file` in kwargs in get and set method

if provided, this overrides the default file store location. The `path` is used and though that the domain is resolved. The file can be a virtual path which is resolved to an absolute volume path if possible.  

##### optional argument `data` in args in set method

If null, the entry is removed. If used in combination with a `key`, the key is removed from the file. if provided, this data is used as content for the state. If key provided, the data is stored under this key. 

##### translations of relative file paths in state service volume

`Proj:` translates to `/`

`EXOscada:` translates to `/EXOscada/`

`Area:` translates to `/[name of area fetched through path and domaincontroller]/`

`Web:` does not yet translate to anything. maybe throw here if virtual drive is defined.

`Shared:` translates to `/Shared`

##### Examples:

```
get path:1sdlksdlskdjflsd==, key:"my setting", file:"Area:viewsettings.json"

example result path to volume: /Varmecentral/viewsettings.json
```

This example uses the path, to resolve the file location. Use the volume to read the file. Get the key `my setting` from the json object. Return only that object.

```
get path:1sdlksdlskdjflsd==, key:"my setting", file:"globalsettings.json"
```

This example shows that we are using the `/arrigo/state` folder for storing data, because it has not a relative path in file argument. The file read/written here is `/arrigo/state/globalsettings.json` this will be used for shared/blobal settings in the project. 

```
get path:1sdlksdlskdjflsd==, key:"my setting"
```

This example uses the default store location for the state/setting. 

Use the volume to read the `/arrigo/state/[pathDecoded].json`, return only the value for key `my setting`

```
get path:1sdlksdlskdjflsd==
```

This example is the most common and simple. Just read the file `/arrigo/state/[pathDecoded].json` and return the contents.

```
set path:1sdlksdlskdjflsd== data:[1,2,3]
```

Data is just object. serialized and written to disk. data is written to file `/arrigo/state/[pathDecoded].json`.

```
set path:1sdlksdlskdjflsd== data:[1,2,3], file:globalsettings.json key:"mySetting"
result:
{
    key1:1,
    key2:2,
    mySetting:[1,2,3]
}

get path:1sdlksdlskdjflsd== file:globalsettings.json key:"mySetting"
result:


```

Data is just object. serialized and written to disk. data is written to file `/arrigo/state/[pathDecoded].json`.

- SET: If data is null, whipe the entry from file, or erase the file if no key provided. Null means remove/erase.

  

- GET: If key is not present throws exception

- GET: if file/path not present throws exception