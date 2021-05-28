# Arrigo Reports Service

Source code in EXO repository. Folder/solution `EXO/EXO/arrigo-services-reports`. 

Copy the latest bin files from the artifact from build server into your bin folder of EXO.
Build solution. 
In project properties, under command line arguments, you can provide the following options:

## Commandline / Environment options

| Environment | Command line       | Description                                    | Default                   |
| ----------- | ------------------ | ---------------------------------------------- | ------------------------- |
| URL         | -u or -url         | The `WAMP` router to connect to                | `ws://127.0.0.1:8080/ws`  |
| REALM       | -r or -realm       | The `WAMP` *realm* to use                      | `realm1`                  |
| ACCOUNT     | -a or -account     | The *name* of the account                      | **none**                  |
| SERVICENAME | -s or -servicename | *Name* of service to register in `WAMP` router | `reports`                 |
| EXODSURL    | -exodsurl          | EXOds router to connect to                     | `ws://127.0.0.1:26488/ws` |
| EXODSREALM  | -exodsrealm        | Realm in EXOds router                          | `data`                    |
| SECURITYKEY | -k                 | The service token used for connection to URL   | **none**                  |



## Initalization

On startup, the environment is loaded and connections are made to two routers. The Arrigo router, and the EXOds router. 

Connections are persistent and reconnects on dropout or restarts of routers. 

The reports service are driven entirely from invocation of the registered methods. no automatic or scheduled reports. 



## Methods

The reports service register itself at `accounts.[accountName].services.[SERVICENAME]` (`accounts.smalltown.services.reports`). All methods registers under this namespace. 

### [reports].createreport

The report is created immediately. However, due to the maybe complex execution of the report, the status should be checked to find out report result. Status flags are described. 

| param         | type   | Default  | Description                                                  |
| ------------- | ------ | -------- | ------------------------------------------------------------ |
| folderId      | args   | **none** | the Id of the folder the report should be run in             |
| erwvFile      | args   | **none** | path with virtual drive. points to report file.              |
| fileArguments | args   | **none** | list of argument values to erwv file                         |
| callMeta      | kwargs | null     | object with mandatory key `token` with users token. used for access control |

Returns the id of the newly created report.

### [reports].get

This method is used for querying the report for data of different kinds.

| param    | type   | Default  | Description                                                  |
| -------- | ------ | -------- | ------------------------------------------------------------ |
| reportId | args   | **none** | the report Id                                                |
| props    | args   | **none** | Object with key-value pairs.  See description of `attribute` key below. |
| callMeta | kwargs | null     | Object with mandatory key `token` with users token. used for access control |

#### props parameter `attribute` key

| attribute value | return type | description                                                  |
| --------------- | ----------- | ------------------------------------------------------------ |
| `status`        | int         | Returns the status for the report. `2` - all macros resolved. `3` - all arguments are resolved. `4` -  all variables are read (peeked). `5` - excelfile is read and loaded. `6` - all data from database are inserted into excel file. `10` - report done without errors. `101` - unable to find/open excel file. `110/100` - unknown error (see server messages in exoscada runtime on server for error description) |
| `cells`         | string      | Read any cell from excel file. `sheet`, `row`, `col` is mandatory param keys. `sheet` - name of the sheet to read from. `row` - the row number in excel. `col`- the column number in excel. |
| `pngData`       | Buffer      | Get the buffer for png output from the report.               |
| `xlsxData`      | Buffer      | Get the buffer for xlsx output from the report.              |
| `csvData`       | Buffer      | -""-                                                         |
| `pdfData`       | Buffer      | -""-                                                         |
| `svgData`       | Buffer      | -""-                                                         |

## Examples

create a report in a serverside function: 

```

const createReportMethod = 'accounts.rsdemo2.services.reports.createreport';

async function createReport(args, context, path, token){
    const { filter: [f_resolution, f_startDate, f_timeSpan, f_compare, f_showPrice, f_price, f_currency] } = args;
    let reportArguments;
    const timeSpan = f_timeSpan.value[0];
    const excelFile = excelFiles[timeSpan];
    const signalRange = signalRanges[timeSpan];
    const reportFile = "%ReportFile%";
    const reportTitle =  "ReportTitle";
    const resolution = f_resolution.value;
    const startDate = f_startDate.value;
    const compareYears = Number(f_compare.value[0].split(' ')[0]);
    console.log("f_compare", compareYears);
    const compare = [0,1,2,3,4].map(value => value <= compareYears ? "%Signal%":"")
    
    const price = f_price.value;
    const currency = f_currency.value;
    const showprice = f_showPrice.value ? 1 : 0;
    
    const rpcArguments =[
        path,
        reportFile, 
        [
            reportTitle,
            excelFile,
            startDate, 
            timeSpan,
            resolution,
            ...compare,
            signalRange, 
            price,
            currency, 
            showprice
        ] 
    ]
         
    let reportId 
    try{
        console.log('report arguments', rpcArguments);    
        reportId = await context.call(createReportMethod, rpcArguments, { callmeta: {token} });
    }
    catch(err){
        console.error("Error when calling ", createReportMethod, rpcArguments);
        console.error("CreateReport", err);
        throw err;
    }
}
```

Get a report status from a server side function:
```try {
        result = await context.call(getReportMethod, [reportId, {attribute:'status'}], { callmeta: {token} });
    }
    catch(err){
        console.error("getReportStatus", err);
        throw err;
    }
```

Get the svgData for a report:

```

    

    let payload = null;    
    try{
        payload = await context.call(getReportMethod, [reportId, {attribute: 'svgData'}], { callmeta: {token} } );
    }
    catch(err){
        console.error("getReportData", err);
        throw err;
    }

```

Get a cell value from a report:

```

    let celldata = null;    
    try{
        celldata = await context.call(getReportMethod, [reportId, {attribute: 'cells', row:2, col:3 sheet:"sheet1"}], { callmeta: {token} } );
    }
    catch(err){
        console.error("getReportData", err);
        throw err;
    }

```

