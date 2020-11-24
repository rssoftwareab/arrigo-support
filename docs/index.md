---
layout: main
title: Releases.
description: Releases and Change Log
---
# Download

Download EXO2019 Edition 3 from FTP.

[Arrigo Local Installation](https://arrigo.blob.core.windows.net/arrigo/ArrigoLocalInstaller.exe).

[Early Bird uninstaller](https://arrigo.blob.core.windows.net/arrigo/ArrigoEarlybirdUninstaller-1.0.19.exe).

[Installation instructions](./prereq.html)

# Arrigo Local Change Log

## Latest

### `1.0.265` (*2020-11-24*)

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


## Stable
### `1.0.247` (*2020-11-06*)

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

## Older releases

### `1.0.239` (*2020-10-27*)
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

### `1.0.233` (*2020-10-26*)
The first one. The hot stuff. So hot that we haven't even tried every aspect of it ourselves. Try it out, you will not be disappointed.
- Widgets
- Link icons in groups
- Arguments in folder views files
- Lots of svg files included
