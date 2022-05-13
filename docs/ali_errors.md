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

## 1009

`Failed to modify the ExecutionPolicy settings.`

The installer tried to modify the PowerShell ExecutionPolicy settings but failed. Please verify that you have write permissions to the Registry section `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\PowerShell`.

You can also use the Windows Group Policy Editor (gpedit.msc) to change the policy. Navigate to `Local Computer Policy\Computer Configuration\Administrative Templates\Windows Components\Windows PowerShell\Turn on Script Execution`, select **Enable**, select the Execution Policy **Allow all scripts** and click **OK**.

*Please note that your system administrator or IT organization might have disabled your access to the Group Policy Editor.*

## 1010

`Failed to restore the ExecutionPolicy settings.`

The installer tried to modify the PowerShell ExecutionPolicy settings but failed. Please verify that you have write permissions to the Registry section `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\PowerShell`.

*Note: the following instruction will reset the MachinePolicy to Undefined.*  
You can also use the Windows Group Policy Editor (gpedit.msc) to change the policy. Navigate to `Local Computer Policy\Computer Configuration\Administrative Templates\Windows Components\Windows PowerShell\Turn on Script Execution`, select **Not Configured** and click **OK**.

*Please note that your system administrator or IT organization might have disabled your access to the Group Policy Editor.*

## 1011

`Installation aborted by user`

The current user is not a member of the Administrators group on the machine (BUILTIN\Administrators) and the user aborted.  
Re-run the installer as another user to prevent this warning.  
  
If you are running ALI on a domain connected machine, please contact system administrator or IT organization to verify that you are also a local administrator.

## 1012

`Failed to prepare offline installation`

The downloading and packaging of the offline installer failed.  
Please check the output or installation logs for the actual error. If, for example, the download failed please verify that you have internet access.

## 1013

`Failed to verify/copy files for offline installation`

ALI failed to find or copy one of the files needed for an offline installation.  
Please check the output logs for details about the missing file and then verify that the file is present in the extraction folder.  
If the file is missing there you can try to extract the files again, or run ALI on a coumputer with internet access to generate a new package.

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

## 4002

`pm2 was not found after offline installation`

The installer failed to verify the pm2 installation.  
Please check the output logs for any errors during the extraction.

## 4003

`Failed to detect required version after offline installation`

The installer found the pm2 binary but it was the wrong version.  
Please check the output logs for any errors during the extraction.

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
