---
layout: main
title: Arrigo Local Installer - Errors
description: Description of errors that can occur when running Arrigo Local Installer
---

# Errors

## 1000

`This installer must be run as Administrator.`

The installer was not run as Administrator.

## 1001

`The EULA must be accepted before installing or updating the software`

The user didn't accept the End-User License Agreement.

## 1002

`Installation aborted by user`

The installer was running with -unsafeMode flag but the user aborted.

## 1003

`You need Windows 10 / Windows 2016 Server or greater to install`

The installer was run on an unsupported OS.

## 1004

`This computer is part of the Earlybird program. You must run ArrigoEarlybirdUninstaller before attempting to install again`

The installer was run on an Earlybird machine.

## 1005

`No EXOscada installation found`

The installer was run on a machine without EXOscada installed.

## 1006

`You need '[EXOscada edition]' to install`

The installer was run on a machine without the required EXOscada edition installed.

## 1007

`You need '[EXOscada edition]' Release [Release number] to install`

The installer was run on a machine with the correct EXOscada edition installed but with the wrong specific release.

The `Release number` may contain two digits (ex: `4.29`) and this simply means "Edition 4, Release 29".

## 1008

`Installation aborted by user`

The installer wanted to close all open EXO programs but the user aborted.

## 2000

`Installation aborted by user`

The installer wanted to restart the IIS after installing the Dotnet Hosting Bundle but the user aborted.

## 2001

`Failed to detect required version after installation`

The installer failed to verify the Dotnet Hosting Bundle installation.

## 3000

`Failed to download Node.js from [link]`

The installer failed to download the Node.js installer.

## 3001

`Node.js was not found after installation`

The installer failed to verify the Node.js installation.

## 3002

`Failed to detect required version after installation`

The installer found the Node.js binary but it was the wrong version.

## 4000

`pm2 was not found after installation`

The installer failed to verify the pm2 installation.

## 4001

`Failed to detect required version after installation`

The installer found the pm2 binary but it was the wrong version.

## 5000

`Failed to download ApplicationRequestRouting from [link]`

The installer failed to download the ApplicationRequestRouting installer.

## 5001

`Failed to detect ApplicationRequestRouting after installation`

The installer failed to verify the ApplicationRequestRouting installation.

## 6000

`Failed to download RewriteModule from [link]`

The installer failed to download the RewriteModule installer.

## 6001

`Failed to detect RewriteModule after installation`

The installer failed to verify the RewriteModule installation.