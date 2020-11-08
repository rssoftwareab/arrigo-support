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

## `1.0.247` 
### Installer
- Preparing for Windows update KB4577586 (Flash removal). 
- Args passing when installation upgrade
- Folders were created in the disk root if the installer was run directly after a fresh EXO installation.
- Powershell version check
- Unsafe Mode flag added. Lets you try to install on unsupported OS'es. 
- Added a "press any key to continue" when running in unsafe mode

### Tools
- Greater support for Shared: in tools. 
- Hotfix: Chart arguments did not show up in folder views tool
- Hotfix: Argument template missing in FolderViewsTool.

### Templates
- ViewAppLib+ListViewTemplates+ViewDesignerTemplates:PTS19054:New fan,pump and compressor symbol
- Icon-path error in station's ArrigoBMS.Exocommands
- Preparing for area types
- New Corrigo 5.0 template and related files


### Runtime
- Fix bug in arguments in many instances of same shared viewfile. 


## `1.0.239` 
This is the first release targeting EXO 2019 Edition 3. 

### Installer 
- Check for new version automatically
- Targets EXO 2019 Edition 3

### FolderTool
- Fix: icons
- Fix: icon suggests

### FolderViewsTool
- Fix: icons

### Templates
- Minor fixes.

## `1.0.233`
The first one. The hot stuff. So hot that we haven't even tried every aspect of it ourselves. Try it out, you will not be disappointed.
- Widgets
- Link icons in groups
- Arguments in folder views files
- Lots of svg files included
