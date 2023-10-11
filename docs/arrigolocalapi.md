---
layout: main
title: Releases - Arrigo Local API
description: Change Log
---

# Change Log

## 1.4.43

*2023-09-29*

* Feature: Change password and password expire (#173)

## 1.4.23

*2023-09-18*

* Feature: ArrigoHome functionality

## 1.3.24

*2023-05-23*

* Dotnet 7 compatible

## 1.3.15

*2023-05-03*

* Feature: AZ#1573: Common log config folder (#156)

## 1.3.12

*2023-04-06*

* Feature: AZ#1878 Implement EXO user groups for ArrigoID (#164)

## 1.3.10

*2023-03-22*

* Fix: AZ#1715: Chart export (#163)
* Fix: Defaulting to signal name if signal text is null (#162)
* Fix: AZ#1650: Chart: Digital signals are shown incorrectly if on/off isn't inside current interval (#159)
* Fix: AZ#1617: Year zero date on alarms (0000-01-01T00:00:00Z) (#158)
* Feature: AZ#1751 Global search (#160)

## 1.3.1

*2023-01-30*

* Feature: AZ#1023 License system

## 1.0.240

*2023-01-18*

* Fix: Retrying 'Read' in 'setData' and 'writeData' 10 times instead of once.

## 1.0.239
*2023-01-09*

* Feature: Configurable log configurations

## 1.0.238
*2023-01-03*

* Error message fixes

## 1.0.237

*2022-11-16*

* TP#21331 AZ#1318: No numerical limitation on returned folders. (#148)
* Hotfix: Checking if token is parsable before trying to parse. Prevents explosions. (#149)
* We're throwing, but not catching. So whenever this happens it ends up in the Event Log. (#150)
* Hotfix: Memory greedy and CPU intense w3wp.exe AZ#1350,AZ#1355 (#151)

## 1.0.231

*2022-11-16*

* Added filter for unhandled WebSocketExceptions to prevent logging in Windows Event Log

## 1.0.230

*2022-10-21*

* Removed EXO build version from sysinfo endpoint 

## 1.0.229

*2022-10-20*

* Various fixes regarding Refresh Tokens

## 1.0.226

*2022-10-20*

* Fix: AZ#1175 check email as username (#145)

## 1.0.225

*2022-10-19*

* Feature: Add support for Arrigo ID login

## 1.0.224

*2022-10-05*

* Fix: AZ#950 (TP#18262)

## 1.0.223

*2022-09-08*

* Feature/AZ#781 (#143)
    - Optimize sql queries for Alarms and Digitals
    - Added new fields for Alarms EventTime and AlarmTime
    - Added new fields for Digitals EventTime and SwitchedOnTime
    - Added new order fields for Alarms and Digital


## 1.0.222

*2022-08-31*

* Fix: TP#17538: Analog events are now matched on TimeLength (#142)

## 1.0.221

*2022-07-06*

* Fix: AZ#718: Handling cultural differences in decimals better

## 1.0.220

*2022-07-01*

* Feature: TP#17330: Added the option to provide a custom url for the legacy UA. This is needed if the server has a valid cert installed

## 1.0.219

*2022-06-30*

* Fix: TP#17353: More validation on data/value messages internally

## 1.0.218

*2022-06-27*

* Fix: Prevents crash if columns in database are missing

## 1.0.217

*2022-06-17*

* Fix: Authentication problems for static resources
 
## 1.0.215

*2022-06-08*

* Auto-filtering on TimeLength for Analogs History (Azure#665)

## 1.0.213

*2022-05-24*

* Error handling improvement (TP#15913)
* Fix: Ignore case sensitivity for static resources
* Deprecate field 'publicVariableFiles' on 'Account' and 'Userarea'. Use new field 'publishedVariableLists' instead

## 1.0.208

*2022-03-25*

* TP#13489 Added "SignalType" to analog filter (#131)

## 1.0.206

*2022-02-17*

* Fix: Writable access in Account views (TP#14557)

## 1.0.205

*2022-01-14*

* Fix: Audit Log entries are now written correctly (with titles) (TP#8504)

## 1.0.204

*2021-12-09*

* Fix: The locale from the old token is now carried over to the new (#122)

## 1.0.203

*2021-12-03*

* Feature: Fix: Now the account access level is the same as the user's RootArea access level (#121)	
* Feature: Reading the command timout from settings, or defaulting to 60 seconds (Dapper default is 30 seconds). (#119)

## 1.0.199

*2021-11-08*

* Feature: No authentication required on known image formats (#117)

## 1.0.198

*2021-10-21*

* Fix: It is now possible to toggle between Arrigo- and EXOscada style signals lists (#115)

## 1.0.197

*2021-10-19*

* Fix: Removes tolerance limitations (#114)

## 1.0.196

*2021-10-13*

* Fix: Date range filters are disabled (in the underlying sql query) for all status lists (TP#11459) (#112)

## 1.0.195

*2021-10-04*

* Feature: Added support for folder icons (only svg's) (#113)

## 1.0.193

*2021-09-29*

* Fix: All unhandled exceptions are logged to ease debugging (#111) (TP#11134)

## 1.0.191

*2021-09-15*

* Fix: User log crashes when entries does not belong to a folder/area (TP#11085)

## 1.0.190

*2021-09-07*

* Fix: Case-insensitive variable handling (TP#9937)

## 1.0.186

*2021-08-27*

* Fix: Sql query V2 date ranges


## 1.0.185

*2021-08-27*

* Fix: Updating values in views (TP#10593)

## 1.0.184

*2021-08-23*

* Optimized read


## 1.0.183

*2021-08-10*

* Folder->AccessLevel is now a string and not an enum

## 1.0.182

*2021-07-11*

* Action templates for audit log (#106)
* Optimized SQL queries for alarms,digitals,analogs (TP#9505) (To test experimental optimization, enable the flag by setting  `sqlquery_version2` to `true` in `%ProgramData%/Arrigo/Arrigo Local/settings/arrigo-api.json`.)
* Moved the api setting files to  %programdata%\Arrigo\Arrigo local\settings (#105)

## 1.0.176

*2021-06-10*

* Hotfix : `readData` now handles duplicates of same element in variable list (TP#9509)

## 1.0.175

*2021-05-20*

* Fix: Audit info is now stored correctly (TP#8668)

## 1.0.174

*2021-05-20*

* Hotfix: ReadData now returns the correct order of the variables list (compared to the input arguments) (TP#9033)

## 1.0.173

*2021-05-19*

* Users who are blocked or need to change their password are now prevented from logging in. (TP#8503)
  **Note!** Passwords are changed using the EXOscada login page (which doesn't require Flash) 

## 1.0.171

*2021-05-11*

* Fixed a bug that could prevent the selected folder from being included in filter queries

## 1.0.170

*2021-05-11*

* Hotfix: Reverted fix regarding alarms and ShowInScada from 1.0.165

## 1.0.169

*2021-05-07*

* Fixed a bug that causes Block of Write function when using Script with ¤ and same value not listed in the view (#101)

## 1.0.168

*2021-05-05*

* Implemented untriggered signals in alarm/digital list (#100)
* Fix: App error "t.map is not a function'  (#99)

## 1.0.166

*2021-04-29*

* The 'Account' and 'Root' areas now share the same access level (#95)

## 1.0.165

*2021-04-29*

* Fix: Only alarms from areas with ShowInScada set to true are shown (#98)


## 1.0.164

*2021-04-01*

* Hotfix: Resolve folderId for static resources in views (Fix Popup window issue)
* Fixed a bug that could result in failed login attempts (concurrency issues) (#97)


## 1.0.162

*2021-03-24*

* Optimized SQL queries for analogs

## 1.0.161

*2021-02-11*

* Fixed a bug regarding subscriptions (#92)

## 1.0.158
*2021-02-02*

* Added support for opening the EXOscada UserAdmin page 
* We now return version info in response headers
* More resolvers and endpoints are now async for faster responses
* SystemInfo now contains versions for all Arrigo Local components

## 1.0.154
*2021-01-18*

* Minor fixes

## 1.0.153
*2021-01-06*

* Optimized the common SQL queries for analogs and digitals to improve speed
* ChartWidget now work with big databases and databases without the "Count" column in the "Analog Values" table
* Added the "Account" type in .folder.json to select which rwaf file to be displayed for the Account (home button)

**Note!** In this version `uid`´s has been replaced with `path`´s. This affects all 3rd party integrations. Please read [Arrigo Local API Usage Instructions](arrigo_local_api_usage_instructions.md) for more info.

