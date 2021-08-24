---
layout: main
title: Releases - Arrigo Local API
description: Change Log
---

# Change Log

## Upcoming releases

## 1.0.18?

*2021-08-23*

* Optimized subscriptions (reading variables in views)


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

