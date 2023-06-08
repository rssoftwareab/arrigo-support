---
layout: main
title: Releases - Arrigo Licens Manager
description: Change Log
---

# Change Log

## 1.0.121

*2023-06-08*

### Fixes/Improvements
- Fix: The license manager no longer uses the machine name over the WAMP, resolves issues with too long machine names.
- Fix: The shortcut for the license manager now gets the correct path to the icon, delete the icon before updating the license manager to get the correct path if it's already installed.

## 1.0.99

*2023-03-13*

### Fixes/Improvements
- Fix: Upgrade to .Net 7 for the arrigo-wamp-host.

## 1.0.96

*2023-03-01*

### Fixes/Improvements
- Fix: AZ#1746 Now checks version correctly so latest version don't trigger download latest version of license manager installer prompt
- Fix: AZ#1747 Crashes when writing install log, directory is now created to the installer doesn't crash when installing for the first time
- Fix: When choosing to download the latest the program now terminates correctly so the installation of the old version does't proceed

## 1.0.91

*2023-02-22*

### Fixes/Improvements
- Fix: LMI crashes if computer lacks internet connection
- Fix: Checks for newer versions of License Manager Installer correctly
- Fix: Logs installed version

## 1.0.69

*2023-01-30*

### Fixes/Improvements

- Initial release.
