---
layout: main
title: Releases - Arrigo Local Scada Function
description: Change Log
---

# Change Log

## 1.4.21
*2024-02-19*

* Removing unused code

## 1.4.16
*2023-12-05*

* Feature: The Arrigo Scada Function does not peek variables anymore, as this could hide underlying communication problems

## 1.4.12

*2023-09-18*

* Fix: Improved startup procedure to prevent loss of kernel events

## 1.4.11

*2023-09-18*

* Feature: ArrigoHome functionality

## 1.3.11

*2023-05-04*

* Feature: AZ#1573: Common log config folder (#97)

## 1.3.5

*2023-03-22*

* Fix: Solves the problem when we stop the function (invalid license) while the function is starting

## 1.3.4

*2023-03-21*

* Fix: Update EXOGeneralLibrary library to be compatible with EXO2023. This fixes the multiple instance issue
 
## 1.3.3

*2023-02-08*

* Fix: AZ#1674: Arrigo Local API has problems starting up (ArrigoAppPool needs to be restarted for the API to start up correctly)

## 1.3.1

*2023-01-30*

* Feature: AZ#1023 License system

## 1.1.146

*2023-02-08*

* Fix: AZ#1674: Arrigo Local API has problems starting up (ArrigoAppPool needs to be restarted for the API to start up correctly)

## 1.1.142

*2023-01-18*

Saving format files as json on startup. All this so that ViewDesigner doesn't have to do the dll mangling on every startup.

## 1.1.141

*2023-01-11*

* Fix: AZ#1508 Ensure that the application has startup before exo send running command (#94)
* Feature: Better peeking and poking (#92)
* Fix: Better cache for non existing files (#91)
* Fix: AZ#1276 Fix cache level (#90)

## 1.1.136

*2022-12-02*

* Fix: AZ#1224 Resolving date macros (TP#20813)

## 1.1.135

*2022-10-21*

* Fix: Better support for Central Time Channels and Central calendars

## 1.1.134

*2022-09-29*

* Fix: Handling unsubscription of variables better

## 1.1.133

*2022-09-08*

* Fix: TP#16776: Handling doubles using invariant culture (#85)

## 1.1.132

*2022-08-25*

* Fix: TP#17496: Now translating SLib and ALib.

## 1.1.131

*2022-06-08*

* Fix: Translating 'web:' (TP#15416)

## 1.1.126

*2022-05-23*

* Fix: Error handling improvement (TP#15193)
* Hotfix: Always activate bindings on root object
* Added checks for explicitly defined connectionstrings 

## 1.1.115

*2021-03-16*

* Hotfix: Attribute in wrong order in listviews (TP#14742)

## 1.1.114

*2021-03-09*

* Hotfix: ecQuery-format list is now thread safe (TP#15112)

## 1.1.112

*2021-02-25*

* Hotfix: Global arguments at account level (TP#14860)

## 1.1.111

*2021-01-28*

* Hotfix: auto SSF reconnect when attach/detach project(#78)

## 1.1.107

*2021-12-09*

* Updated internal nuget packages

## 1.1.106

*2021-12-08*

* Feature: Support for execute exobasic over WAMP

## 1.1.103

* Feature: New fast transpiler. Handle startup/teardown of transpiler instances. 

## 1.1.96

2021-11-26

*Only changes in internal build script*

## 1.1.92

2021-10-13

* Hotfix: Cwav and Cwlv format files are embedded as resources (TP#11464) (#72)

## 1.1.91

2021-08-24

* Optimized subscription

## 1.1.90

2021-08-24

* Optimized read (#70)

## 1.1.89

2021-08-19

* Fix/updating variable stopworking (TP#10202)

## 1.1.88

2021-07-16

* Minor internal fixes

## 1.1.87

2021-07-09

* Fix: queueing callbacks from the kernel (#68)
* Sets the account title to account name if the title is empty from Project.Exo (#66)
* We handle any initial advise updates/callbacks better (than before) by adding variables to the internal list early. (#65)

## 1.1.84

2021-06-10

* Fixed argument updating issue when changing the binding arguments from the parent window (TP#9277)

## 1.1.83

2021-06-07

* Fixed yet another bug that prevented the Scada Function to start up if the pm2 services was not running (this caused `wamp.error`s in the frontend)

## 1.1.82

2021-05-26

* Fixed a bug that prevented the Scada Function to start up if the pm2 services was not running (this caused `wamp.error`s in the frontend)

## 1.1.81

2021-04-28

* Fix: Changed the way the internal Wamp host is terminated to prevent errors in connected services

## 1.1.77

2021-04-20

* Feature: Connecting to the local broker/host and registering ServerSideFunctions in views. Function registrations are automatically updated when files are saved.

## 1.1.76

2021-04-16

* Fix: Properly registering message client at startup

## 1.1.74

2021-04-13

* The "Account" macro is now supported

## 1.1.73

2021-04-08

* The File attribute can now contain static resources

## 1.1.72
2021-03-29

* Fixed issue with global arguments and parent folders 

## 1.1.70
2021-02-02

* Fix to resolve changes when files are renamed or moved

## 1.1.69
2021-01-05

* Improved the caching of files, which makes navigation much faster and lets you bookmark favourites etc. in the frontend
* Added the "Account" type in .folder.json to select which rwaf file to be displayed for the Account (home button)

**Note!** In this version `uid`´s has been replaced with `path`´s. This affects all 3rd party integrations. Please read [Arrigo Local API Usage Instructions](arrigo_local_api_usage_instructions.md) for more info.
