---
layout: main
title: Releases - Arrigo Local API
description: Change Log
---

# Change Log

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

