---
layout: main
title: Releases - Arrigo Local
description: Change Log
---
# Change Log

### `1.0.xxx`
*2021-02-xx*

- Frontend: [1.0.94](./frontend.html#1.0.94)

- Arrigo Local API: [1.0.158](./arrigolocalapi.html#10158)

- Arrigo Local Scada Function: [1.0.70](./arrigolocalscadafunction.html#1070)

- Required EXO installation: EXO 2019 Edition 3  Build 793

#### Installer

* The ReginAppPool is stopped when installing EXO components to prevent issues where files are in use
* The install log is now copied by the bootstrapper instead of the scripts
* The theme and images folders are excluded from deletion when installing a new frontend

#### Views

- 

#### Tools

- Arrigo Folder tools can now be opened from the project/account node in Project Builder
- Added a template for the project/account folder

### `1.0.299`
*2021-01-22*

- Frontend: [1.0.91](./frontend.html#1.0.91)

- Arrigo Local API: [1.0.154](./arrigolocalapi.html#1.0.154)

- Arrigo Local Scada Function: [1.0.69](./arrigolocalscadafunction.html#1.0.69)

- Required EXO installation: EXO 2019 Edition 3  Build 793


#### Installer

No Changes.

#### Views

- Major improved speed and performance
- Persistent links to all routes. You are now free to bookmark anything
- Support for 2D rotation in views
- %Include("file", arg1,  arg2)% macro in views and config files
- Lots of bug fixes and improvements

#### Tools

- Bug fixes
- Chart tool opens correctly from link icons
- Improved link icon feature list

### `1.0.295`
*2021-01-13*

- Frontend: 1.0.68
- Arrigo Local API: 1.0.147
- Arrigo Local Scada Function: 1.1.60
- Required EXO installation: EXO 2019 Edition 3  Build 767



#### Installer

- Fixed a bug where the Arrigo BMS SCADA Function could be downgraded by the EXO installation.

- Removed the old Flash fix from the installer. Use FlashEnabler-1.0.7 instead!

### `1.0.277`
*2020-12-16*


#### Runtime

- Fixed a bug that could crash the Arrigo BMS Scada function when unadvising variables.

### `1.0.269`
*2020-12-07*

#### Installer

- Messages in the installer log are now timestamped
- Running the Flash fixer (KB4577586) as a part of the installation
- Saving the ArrigoLocalInstaller version in versions.json


#### Runtime

- Various fixes regarding images in views
- Fixed a bug where long startup times could deadlock the Arrigo BMS Scada function
- Fixed a bug that prevented the User Log/History from showing
- Fixed a bug that made logins fail under certain conditions

### `1.0.265`
*2020-11-24*

#### Installer

- Added the option to pin an installer, i.e. skip the online check for newer versions
- No output from bootstrapper when in quiet mode
- Added the "latest" mode which will let customers try production-ready code that hasn't been tested as much as "stable"

#### Tools

- New look for animated fan symbol
- Hotfix: Enable name change for Link Icons
- Various template fixes


#### Runtime

- Message timestamps are now delivered as UTC
- Handling non-existing connection strings
- Subscribed OneShots are only returned when they have a "valid" value, i.e. they're not "Pending"
- Reading variables is now approx. 40-200 times faster
- Added a new mutation for writing data based on keys in the view content
- Writing to variables from within an SVG now works as expected

### `1.0.247`
*2020-11-06*

#### Installer

- Preparing for Windows update KB4577586 (Flash removal). 
- Args passing when installation upgrade
- Folders were created in the disk root if the installer was run directly after a fresh EXO installation.
- Powershell version check
- Unsafe Mode flag added. Lets you try to install on unsupported OS'es. 
- Added a "press any key to continue" when running in unsafe mode

#### Tools

- Greater support for Shared: in tools. 
- Hotfix: Chart arguments did not show up in folder views tool
- Hotfix: Argument template missing in FolderViewsTool.

#### Templates

- ViewAppLib+ListViewTemplates+ViewDesignerTemplates:PTS19054:New fan,pump and compressor symbol
- Icon-path error in station's ArrigoBMS.Exocommands
- Preparing for area types
- New Corrigo 5.0 template and related files


#### Runtime

- Fix bug in arguments in many instances of same shared viewfile. 

### `1.0.239`
*2020-10-27*

This is the first release targeting EXO 2019 Edition 3. 

#### Installer 
- Check for new version automatically
- Targets EXO 2019 Edition 3

#### FolderTool
- Fix: icons
- Fix: icon suggests

#### FolderViewsTool
- Fix: icons

#### Templates
- Minor fixes.

### `1.0.233`
*2020-10-26*
The first one. The hot stuff. So hot that we haven't even tried every aspect of it ourselves. Try it out, you will not be disappointed.
- Widgets
- Link icons in groups
- Arguments in folder views files
- Lots of svg files included