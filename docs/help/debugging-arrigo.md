## Debugging Arrigo Local services

Each service is run under a service runner (PM2). This services ensures that the services are active and online. All services connects to the broker `arrigo-wamp-host` on startup and registers its methods. PM2 logs all output and all errors from the services with their names in the `%PROGRAMDATA%/Arrigo/Arrigo Local/pm2/logs` folder. 

#### PM2 command line interface 

Start a `cmd` window as administrator and run following commands to investigate status of the running Arrigo Local services:

`cd %PROGRAMDATA%/Arrigo/Arrigo Local/pm2` to navigate into the pm2 folder.

| cmd                         | Description                                                  |      |
| --------------------------- | ------------------------------------------------------------ | ---- |
| `pm2 status`                | Lists a table with all running services and their status. All should be online. |      |
| `pm2 stop [serviceName]`    | Stops a service                                              |      |
| `pm2 start [serviceName]`   | Starts a service                                             |      |
| `pm2 restart [serviceName]` | Restart  a service                                           |      |
| `pm2 logs [serviceName]`    | View the service logs in realtime, useful for debugging serverside functions |      |
| `pm2 flush`                 | Erases all logs                                              |      |

#### Debugging ServerSideFunctions

All execution of serverside function takes place in the `arrigo-services-ssf` service. information about which paths loads functions, and execution of them are logged to the `arrigo-services-ssf` error and out log files. All console.log printouts are found in the out file. all console.error output is found in the error file. This is very useful when debugging the serverside functions attributes. 

run `pm2 logs --lines 100 arrigo-services-ssf`  in a `cmd` window.  the window will print everything in realtime. Be careful! If the window accidently contains selected text, the automatic scrolling of the window stops, and the printouts does not show on screen. If so, just press enter to autoscroll to the last line in the log. The realtime output is also put to disk. 

### The ecosystem.config.js file

Each time an Arrigo project is attached to Arrigo Local, the template file is put into the project Arrigo folder. when Attaching the project, the file is also put in the `%PROGRAMDATA%/Arrigo/Arrigo Local/pm2` folder. This file contains all service specifications.

If the Project needs to be re-attached to Arrigo Local, just remove the `Proj:/Arrigo/pm2/ecosystem.config.js` file and run the `Attach project to Arrigo Local` menu option in Project Builder. 

```javascript
const environment = {
	ACCOUNT: '[accountName]',
	PROJECTPATH: '[PathTOEXOProject]',
};

module.exports = {
	apps: [
		{
			name: "[serviceName]",
			script: "[pathToservice]",
			args: '-k [key] -v [volumeName] -f [directory]',
			env: {
				...environment,
			},
		}
	]
}
```

