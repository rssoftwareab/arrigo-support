---
layout: main
title: Releases - Arrigo Local Scada Function
description: Change Log
---

# Change Log

## Upcoming releases

## 1.1.87

*2021-07-09*

* Fix: queueing callbacks from the kernel (#68)
* Sets the account title to account name if the title is empty from Project.Exo (#66)
* We handle any initial advise updates/callbacks better (than before) by adding variables to the internal list early. (#65)

## 1.1.84

*2021-06-10*

* Fixed argument updating issue when changing the binding arguments from the parent window (TP#9277)

## 1.1.83

*2021-06-07*

* Fixed yet another bug that prevented the Scada Function to start up if the pm2 services was not running (this caused `wamp.error`s in the frontend)

## 1.1.82

*2021-05-26*

* Fixed a bug that prevented the Scada Function to start up if the pm2 services was not running (this caused `wamp.error`s in the frontend)

## 1.1.81

*2021-04-28*

* Fix: Changed the way the internal Wamp host is terminated to prevent errors in connected services

## 1.1.77

*2021-04-20*

* Feature: Connecting to the local broker/host and registering ServerSideFunctions in views. Function registrations are automatically updated when files are saved.

## 1.1.76

*2021-04-16*

* Fix: Properly registering message client at startup

## 1.1.74

*2021-04-13*

* The "Account" macro is now supported

## 1.1.73

*2021-04-08*

* The File attribute can now contain static resources

## 1.1.72
*2021-03-29*

* Fixed issue with global arguments and parent folders 

## 1.1.70
*2021-02-02*

* Fix to resolve changes when files are renamed or moved

## 1.1.69
*2021-01-05*

* Improved the caching of files, which makes navigation much faster and lets you bookmark favourites etc. in the frontend
* Added the "Account" type in .folder.json to select which rwaf file to be displayed for the Account (home button)

**Note!** In this version `uid`´s has been replaced with `path`´s. This affects all 3rd party integrations. Please read [Arrigo Local API Usage Instructions](arrigo_local_api_usage_instructions.md) for more info.
