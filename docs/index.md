---
layout: main
title: Releases.
description: Releases and Change Log
---
# Download

Manually check for the latest service release of EXO2019 Edition 3 on the FTP server.

[Arrigo Local Installation](https://arrigo.blob.core.windows.net/arrigo/ArrigoLocalInstaller.exe). ArrigoLocalInstaller will automatically download and run the latest stable version.

[Early Bird uninstaller](https://arrigo.blob.core.windows.net/arrigo/ArrigoEarlybirdUninstaller-1.0.19.exe).

[Installation instructions](./prereq.html)

# www.arrigo.se
### Latest changes

**2021-01-20**

**EMS Fixes/Improvements**

- Meter Value Reading validation now allowing inputed value to be the same as the previous one

- Added translations to Meter Value validation

- Generic formatting of Numeric input values

- Improved Offline Sync view, and redirects when going online again

- Scrolling inputs into view when using number inputs

  

**2021-01-15**

**Features:**
Account Selector
Now displaying an Account Selector when switching between different accounts in multiple tabs.

**Fixes:**

- QR scanning
  QR scanning should now redirect to the correct meter when scanning a QR code containing a meter number
- Maps
  Moving the building/meter location-pin on the map will now trigger a confirmation box, this is to prevent unintentional clicks in the map, resulting in changing location.
- Feedback when verifying formula for Calculated meters
  Now giving some additional feedback when verifying a formula for calculated meters.
- Offline mode
  Now supports offline mode for meter-list.
- Other
  Several bugfixes for added stability, security and performance.

### Current build: 
- Frontend: [1.0.89](./frontend.html#1.0.89)
- Arrigo API: [1.0.26](./arrigoapi.html#1.0.26)

# Arrigo Local
### Latest changes

### Builds
- Latest: [1.0.295](./arrigolocalinstaller.html#1.0.295)
- Stable: [1.0.295](./arrigolocalinstaller.html#1.0.295)