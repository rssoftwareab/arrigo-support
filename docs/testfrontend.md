---
layout: main
title: Releases - Frontend
description: Change Log
---
# Change Log

## Next Releases

## 1.0.240

*2021-10-13*

### Fixes/Improvements

- Hotfix: YMS - Added loading icons in widgets and text when empty (#752)

## 1.0.239

*2021-10-13*

### Fixes/Improvements

- Hotfix: YMS - Added z-index to icon (#750)

## 1.0.238

*2021-10-13*

### Fixes/Improvements

- Hotfix: YMS - Fixed size for filters (#749)

- Hotfix: YMS - Open gate loading indicator (#751)

- Hotfix: YMS - Align buttons (#748)

## 1.0.237

*2021-10-13*

### Fixes/Improvements

- Hotfix: TP#11348 SVGs smaller than 15px misaligned in view (#756)

## 1.0.196

*2021-10-13*

### Fixes/Improvements

- Disable date range filter in the sql query for all status lists (TP#11459) (#112)

## 1.0.236

*2021-10-13*

### Fixes/Improvements

- Hotfix: TP#8366 Change to Transparent color for empty values #745

## 1.0.195

*2021-10-04*

### Fixes/Improvements

- Fix: We accidentally treated all static resources as folder icons. This is now fixed. We also return 404 if a folder icon isn't found.

## 1.1.144

*2021-10-01*

### Fixes/Improvements

- Fix: Machine global installation of npm/pm2 to handle multiple users (TP#11425) (#21)

* WIP

* Need to uninstall pm2 service before we reinstall the service

* Creating npm folder if it doesn't exist

* SetFolderPermissions is now generic-ish

* Minor text output fixes

* Killing pm2 after stopping it to ensure it starts up as SYSTEM

* Null-checking to prevent errors

* Minor text output fixes

* Minor textual changes and refactoring

* Refactored EnsureFolders

* Moved folder creation from InstallPm2 to EnsureFolders

* Minor text output fixes

* Minor text output fixes

* Added correct npm location as global variable

* Comparing current and correct npm prefix

* Minor text output fixes

* Fixed folder issue

* Minor text output fixes

* Moved all npm-fix stuff to one file

* Minor text output fixes

* Minor text output fixes

Co-authored-by: Danne <daniel.lindstrom@rssoftware.se>

## 1.0.194

*2021-10-01*

### New Features

- Feature: Added icon support for folder icons (#113)

## 1.0.193

*2021-09-29*

### Fixes/Improvements

- Fix: Now we log all unhandled exceptions for better debugging (#111) (TP#11134)

## 1.0.235

*2021-09-28*

### Fixes/Improvements

- Hotfix: TP#10255 Chart with "small" numbers shows flat lines (#732)

* fix: Chart API requests use signal tolerances

Co-authored-by: Jonas Johansson <jonas@RSS.local>

- Hotfix: TP#9567 Changed behavior on mobile login input labels (#733)

* changed behaviour on mobile login input labels

* Update src/external/packages/eos/components/login/styles/StyledLoginContainer.js

* Update src/external/packages/eos/components/login/styles/StyledLoginContainer.js

Co-authored-by: TeodorAndersson <teodor.andersson@rssoftware.se>
Co-authored-by: Mikael Ohlsson <69139850+mikael-rssoftware@users.noreply.github.com>

- Hotfix: TP#11037 Update meter value inputs to take another decimal (#731)

## 1.0.234

*2021-09-27*

### Fixes/Improvements

- Hotfix: Bump CW2 to 1.0.45 (#742)

## 1.0.231

*2021-09-27*

### Fixes/Improvements

- Hotfix: User Admin Create/Update fix (#740)

## 1.0.192

*2021-09-21*

### Fixes/Improvements

- Test purposes

## 1.0.229

*2021-09-21*

### Fixes/Improvements

- Publishing new ALI build info

## 1.0.228

*2021-09-14*

### Fixes/Improvments

- Fix: Added permissions for MeterValues (#721)
- Hotfix: MeterValue Permission fix (#728)
- Hotfix: Minor fixes for MetersList (#729)
- Hotfix: YMS send order to port without specific port (#730)

## 1.0.224

*2021-09-13*

### New Features

- Feature: Logo size now set by theme (#718) 
- Feature: TP-10942 Added Splash login (#717) 
- Feature: TP-10589 View popup bring to front not working (#719)

### Fixes/Improvments

- Hotfix: Enhance offline mode support (#725) 
- Hotfix: Adds chart zoom limit (#720) 
- Hotfix: TP#9278 and TP#9994: Broken images in views (#726) 
- Hotfix: Dynamic page title (#722) 
- Hotfix: TP-10734 Prevent create event from creating multiple meters (#715)
- Hotfix: Add validation messages if custom theme file contains unparsable json (#712)
- Hotfix: Change Default client to Arrigo (#714)
- Hotfix: YMS add account to crossbar name space (#713) 
- Hotfix: YMS shorter minimum length on phone number (#710)
- Fix: TP-10942 Sizes logo based on height instead of width (#716) 
- Fix: Use local time in create order + cleanup (#711)
- Fix: Logofix in header (#723)

## 1.0.213

*2021-08-30*

### Fixes/Improvments

- Hotfix: Fix a crash when a helper got overridden (#709)

## 1.0.212

*2021-08-30*

### New Features
- Feature: Add login logic to be able to auto-login from Cypress test suite (#707)
- Feature: UsePreviousRoute for LinkIcons (#684)
- Feature: Add a full screen mode to views (#694)

### Fixes/Improvments
- Hotfix: Secure localStorage set (#708)
- Hotfix: YMS Add validation on registration number (#706)
- Hotfix: YMS Alphanumeric sorting of ports (#705)
- Hotfix: YMS sms number validation (#704)
- Hotfix: Yms create and send order (#703)

## 1.0.206

*2021-08-24*

### Fixes/Improvments

- Hotfix: TP-9142 Right axis misalign when unpinning navigation (#696)


## 1.0.205

*2021-08-20*

### Fixes/Improvments
- Hotfix: Remove fullscreen loader when fetching folder config (#700)


## 1.0.204

*2021-08-19*

### Fixes/Improvments
- Hotfix: YMS Ramberg fixes (#699)

## 1.0.203

*2021-08-11*

### Fixes/Improvments
- Hotfix: YMS Increase default end year with +1 (#697)

## 1.0.202

*2021-08-09*

### Fixes/Improvments
- Hotfix: Update the Dutch, German and French translation files (#695)

## 1.0.201

*2021-07-15*

### Fixes/Improvments
- Hotfix: Access control on widget visibility (#693)
- Hotfix: Fixed infinite scroll (#692)
- Hotfix: Don't show send to port when already at port (#688)

## 1.0.199

*2021-07-09*

### Fixes/Improvments
- Hotfix: Fix Swedish characters in username (#691)
- HotFix: Folder config loading (#690)
- HotFix: Fire Icon (#689)
- Hotfix: TP#9605 Arrigo BMS and Controller Web - Password style in List View not working (#687)

## 1.0.191

*2021-06-17*

### New Features
- Feature: Drag 'n Drop - CRUD behaviour in Nagivation tree
- Feature: TP#9503 Keep last tab in navigation for Meter and Buildings
- Feature: Add audit info to Set- and WriteData mutations for views

### Fixes/Improvments
- HotFix: TP#9574 Chart export date range
- HotFix: TP#9567 Login label

## 1.0.187

*2021-06-10*

### Fixes/Improvments
- HotFix: Updated visuals on login screen (#665)

## 1.0.186

*2021-06-09*

### Fixes/Improvments
- Fix: Scroll container restyling (#653)
- Hotfix: TP#9427 Admin views navigation issue (#668)
- Hotfix: TP#9141 Chart axis error when no axis present (#670)
- Hotfix: TP#9087 Serverside functions in popup views, viewcontainers and popup windows (#672)

## 1.0.180

*2021-05-28*

### Fixes/Improvments
- Hotfix: Scrolling behavior in Charts (#662)
- Hotfix: Honor auto scale from config (#664)
- Hotfix: Admin radio select will now only trigger once on click (#663)

## 1.0.178

*2021-05-20*

### Fixes/Improvments
- Hotfix: TP#8721 Chart RulerLegend timezone (#659)
- Hotfix: TP#8530 User feedback for login status 403 and 409 (#658)
- Hotfix: Fix hang up issue when logging in (#657)
- Hotfix: TP#8994 Restrict climate city and degree days (#655)
- Hotfix: TP#8999 Class C alarms should be active in filter as default (#654)

## 1.0.175

*2021-05-17*

### Fixes/Improvments
- Hotfix: Minor changes to calculated meters (#652)
- Hotfix: TP#7590 Max and min values on symbols where not bound (#651)
- Hotfix: Generic svg update (#650)
- Hotfix: Saved work overflow (#649)
- Hotfix: Reconnecting issue (#648)
- Hotfix: Energy widget not displaying values (#647)

## 1.0.173

*2021-05-07*


### New Features
- Feature: Show empty result info in list views (#642)
- Feature: New Login and Logo (#634)

### Fixes/Improvments
- Hotfix: Issue when history is missing in DigitalDetails and AlarmDetails (#646)
- Hotfix: Chart axis multiple units (#641)
- Hotfix: Hide legend footer if user access level is below operator (#640)
- Hotfix: TP#7887 Issue clicking on filter button touch device (#638)
- Hotfix: Revert to set user filter when navigating away from the reports view (#636)

## 1.0.172

*2021-05-07*

### Fixes/Improvments
- Hotfix: Replaced Finnish square flag with a round one. (#645)

## 1.0.168

*2021-05-05*

### Fixes/Improvments
- Hotfix: TP#7644 Open popup view from list in viewcontainer not working (#639)
- Hotfix: Add finnish translations (#635)
- Hotfix: Set densityfactor for Arrigo BMS (#633)
- Hotfix: Fixes issue where create order would not work for Swedish users
- Hotfix: Map location coordinates (#631)
- Hotfix: Translation Change (#629)
- Hotfix: Meter and Building Default Route (#628)
- Hotfix: Allow zero as consumption / reading value (#627)

## 1.0.164

*2021-05-03*

### Fixes/Improvments
- Hotfix: #TP7799 Text of signals overlapping in chart (#630)

## 1.0.163

*2021-04-27*

### Fixes/Improvments
- Hotfix: Close navigation on navigate (#626)
- Hotfix: Call autobahn list topic only when chart is in viewMode (#625)
- Hotfix: More Generic SVG view fixes and enable Load/Save Work feature (#623)
- Hotfix: Loader in generic SVGs (#622)
- Hotfix: Add minutes to the bmsGetDate function (#621)
- Hotfix: Do not pin navigation on mobile devices (#620)
- Hotfix: Chart resize down (#619)
- Hotfix: Alarms view and widget crash when alarms status update (#611)

## 1.0.149

*2021-04-20*

### New Features
- Feature: Add support for static resource in link icons (#593)
- Feature: Generic SVG views and ServerSideFunctions (#601)
- Feature: Real time value collections (#602)

### Fixes/Improvments
- Hotfix: RPC names should always be lowercased (#603)
- Fix: Minor changes to popup button (#605)
## 1.0.140

*2021-04-08*

### New Features
- Feature: Queries/Mutations errors handling (#581) 
- Feature: ETreport addons (#570) 

### Fixes/Improvments
- Hotfix: Add building name to CMA-input plus some restyling (#588)
- Hotfix: Add more descriptive placeholders to meter inputs (#589)
- Fix: QR scanner (#586) 
- Hotfix: Fix issue with folder configs that was not cleared when logging out of Arrigo (#587)
- Fix: Feature toggle Load/Save signals feature (#583) 

## 1.0.136
*2021-04-01*

### Fixes/Improvments
- Minor improvements
- Hotfix: Added path to static resources (#584)
- Hotfix: Portgroup with sortorder, edit order only selected terminal portgroups (#575)

## 1.0.130

*2021-03-29*

### Fixes/Improvments
- Hotfix: YMS History should not display closed or welcome events (#573)
- Hotfix: Undefined variables in animation views (#572)
- Hotfix: Closing time for YMS screen (#571)

## 1.0.127

*2021-03-24*

### Fixes/Improvments
- Hotfix: No longer cutting edges on add menu (#569)
- Hotfix: Plus button no longer overlaps delete button (#568)
- Hotfix: Symbol cache in listview (#566)
- Hotfix: Filling in User correctly when entering admin view (#564)
- Hotfix: Numeric Maneuver Backspace Fail (#563)
- Hotfix: More contrast on radio buttons and checkboxes (#562)

## 1.0.123

*2021-03-17*

### Fixes/Improvments
- Hotfix: Bump CW2 to fix button icon centering in Views (#565)

## 1.0.121

*2021-03-12*

### Fixes/Improvments
- Hotfix: Search in selectlist on meter (#558)

## 1.0.120

*2021-03-09*

### Fixes/Improvments
- Hotfix: Web socket connectivity in views (#554)
- Hotfix: Menuitems will now grow in height if they are really long. (#552)
- Hotfix: Confirmation when creating new building or meter (#550)
- Hotfix: Added translation for meter icon hovering (#551)

## 1.0.118

*2021-02-26*

### Fixes/Improvments
- Hotfix: Font too big in area Views (Issue: 19275) (#546) 
- Hotfix: Factor as default on meter (#544) 
- Hotfix: Default to correct date in meterDetails panel (#545)
- Hotfix: Add indicator to MeterValueRow instead of italic numbers (#543)

## 1.0.114

*2021-02-24*

### New Features
- Feature: Alarm signals collection (#515)
- Feature: CSV export in charts (#517)
- Feature: Make linkicon accept full url-paths as feature. (#526)
- Feature: Global CSV Export (#531)
- Feature: Custom default route (#529)
- Feature: Chart axis/grid improvements (#532)
- Feature: Historical charts help side panel (#536)
- Feature: Multi language support (#540)

### Fixes/Improvments
- Fix: Calculated meters drag and drop (#535)
- Fix: Add condition for language change in translationManager (#542)

## 1.0.113

*2021-02-22*

- Hotfix: YMS new messages (#538)
- Hotfix: Fix overflow issue with AlarmRow title text (#537)
- Hotfix: View feature now expands more dynamic to viewport (#534)
- Hotfix: Allow ETreport to show temperature with decimals (#533)
- Hotfix: YMS Issues from Feedback (#530)

## 1.0.109

*2021-02-12*

- Hotfix: Rotate2D stopped working after changes in cw2 package 1.0.30 (#528)
- Hotfix: Indication in meters list (#524)
- Hotfix: Refetch navigation list data on updates. (#525)
- Hotfix: Add missing translations to UserCredentials in admin view (#520)
- Hotfix: Fix reload loop when changing API's (#522)
- Hotfix: Bump CW2 to fix issue when loading non-svg symbols (#523)
- HotFix: Hiding User Admin and Collection cart from EMS. (#521)
- Hotfix: Corrected LinkIcon order (#519)
- Hotfix: Resolve async issues with large SVGs (#518)
- Hotfix: Solved dead image due to pop (#516)

## 1.0.98

*2021-02-04*
### New Features
- Feature: Added toolbox feature to Calculated meters (#472)
  When custom formula is used, a small set of logic in a toolbox is presented
- Feature: Account changer (#464)
	If you are logged in on multiple accounts, you have an option to select account during startup.
- Feature: Extension of clear functionality for FilterFeature (#492)
	Improved Reset options in filters
- Feature: User admin view EXOScada (#491)
	Finally you can get User Administration View from Arrigo Local! Feature is located at top right in popupmenu on user avatar.
- Feature: Fix a typo in the cookie string (#502)
	Improved browserupdate when new version exist on server
- Feature: Chart Ruler and Controls (#501)
	Improved data detail in charts, hover to se details of data points
- Feature: Convert command bar (#507)
	Conversion of command bar element in views is now supported
- Feature: Collect signals for chart (#506)
	Add signals to chart view. For now Digital and Analog history values is supported.
	Alarm history and Real time values is near future.

### Fixes/Improvements
- Fix: Sidepanel overlapping content (#446)
  Sidepanel pushes content so overlapping of information is avoided. All buttons is visible always.

- Fix: Scanning QR with meternumber should now redirect correctly (#460)
- Fix: Added verification feedback to Calculated meters (#459)
    You will be notified in UI.
- Fix: Moving the pin on map will now trigger a confirmation box (#462)
    Cards with map and location will now confirm your reposition of the map pin.

- Fix: Widgets patch (#461)
    Minor fixes.
- Fix: Navigation node loading (#469)
    Sometimes the tree got stuck in loading state. 
- Fix: Meterslist offline support (#471)
    Improved offline experience
- Fix: Offline mode notification (#477)
    Automatically close offline notifications
- Fix: Auto scroll input into view (#481)
    Scroll meter value input into view, if not visible.
- Fix: Reset inputs to default after offline change of value. (#483)
    Reset to defaults after offline mutation.
- Fix: Network errors update (#476)
- Hotfix: View observer & Network errors (#490)
    Avoids broken pictures in animation views due to long session time
- Hotfix: Fixed a stylingissue in the Meter Details calendar (#509)
- Hotfix: Added null check in admin view (#510)
- Hotfix: Increased width of meter value inputs on phone (#511)
- Hotfix: Added a min-height to the folder header on mobile. (#512)
- Hotfix: Pass real null value instead of string (#513)

## 1.0.94

*2021-01-27*

### New Features

- Feature: Added toolbox feature to Calculated meters (#472)

**Fixes/Improvements**

- Fix: Meterslist offline support (#471)
- Fix: Offline mode notification (#477)
- Fix: Auto scroll input into view (#481)
- Reset inputs to default after offline mutation. (#483)
- Fix: Network errors update (#476)
- Hotfix: Allow longer meter texts in MeterRow (#495)
- Fix: Reading validation now compares the correct values (#494)
- Hotfix: Remove validation while offline (#498)
- Clear all notifications after discard or sync offline mutations
- No validation of readings while offline
- Hotfix: Auto-reload application if new version has been published to the server (#497)
- Add initial version check middleware to GraphQLManager
- Remove unused ApolloWrapper component
- Add new translations for Version detection
- Display notification and reload browser if new X-Frontend-Version header mismatches with value in localStorage
- Add new LongPressContainer component to show a notification of current version number
- Add link to release notes from version notification
- Pass a hard reload argument to location.reload to assure source reload from server
- Update version message
- Tweek timing of logo long press
- Update public/translations.json
- Hotfix: Clear all notifications after discard or sync offline mutations (#496)
- Hotfix: Null check X-Frontend-Version header on login (#499)
- 

## 1.0.90

*2021-01-22*

### New Features
Account Selector
Now displaying an Account Selector when switching between different accounts in multiple tabs

### Fixes/Improvements

- Meter Value Reading validation now allowing inputed value to be the same as the previous one
- Added translations to Meter Value validation
- Generic formatting of Numeric input values
- Improved Offline Sync view, and redirects when going online again
- Scrolling inputs into view when using number inputs
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

## 1.0.82

*2021-01-13*

### New Features

**Mobile Overlay Panel**
– Allows for listed content to be displayed in a more mobile-friendly panel on mobile devices.
The panel pops from the bottom in overlay mode to get all the focus until action is taken.

**Offline support in MetersList**
– When using the `MetersList` offline, all the mutations are now stored until the device is online again. When online again, action is required to determine which mutations to sync.

**Manual Meters Filter**
– A checkbox that when ticked, filters out only the manual meters in `MetersList`

**Permissions on Entities**
– Permission checks on entities. Determines if the user is permitted to perform CRUD operations.

**Manual Meter Presets**
– Possibility to add a presets to manual meters. Presets determines if the default input type should be “Consumption” or “Reading”, and if the default resolution should be “Year”,“Month”,“Day” or “Hour”.

**Connecting Buildings To Users**
– Interface to set which buildings a user is permitted to see and handle.

**Calculated Meters**
– Updated interface for the old Calculated meter feature. Now with drag and drop support. (Only available after account has been migrated)

**Account changer**
– Solves problem with being signed in to different accounts on different tabs. The `AccountChanger` allows to be able to pick which account to proceed with.

**DynamicListElement new types (Text & TextSelect)**
– `DynamicWidgets` accepts new text element types, with prefilled options to be selected on edit mode

**DynamicWidget refresh on hash update**
– `DynamicWidget` loads content from API, so that if there's a change on widget file configuration the widget updates by itself without the need of refreshing the page

**DynamicWidget access level**
– Users are only able to update `DynamicWidget` element values if they have required access level

**Applied filters indicator**
– Visual indicator that is displayed near the filter toggle so the user knows there are filters applied

### Fixes/Improvements

- Format of numbers depending on localization.
- Meter Reading validation on `MeterChanges`.
- `ClimateDataNormalYears` dataset merge. (fixes error with duplicate months being displayed)
- Remove possibility to perform meter change on calculated meters.
- `MetersList` performance enhancements. Enable caching of queries, giving instant feedback.
- `SidePanel` rendering on iPhone (Safari specifically)
- Correct indication of locked meter values.
- Display building connection in `MeterDetails` panel
- Change of `ET-data` x-values for reference lines.
- Remove swipe-button on mobile devices.
- General mobile device adaption.
- Default to current time when creating meter readings.
- Deletion of metervalues in `MetersList`
- Performance optimization `EnergyWidget` query
- Add missing metervalue indicators, depending on meter value type. (prognosis, calculated etc.)
- Clear navigation redux store on logout. This prevents error when switching accounts.
- Verification feedback to Calculated meters
- Scanning QR with meternumber now redirects correctly
- Confirmation when moving Building pin
- Redirecting to `reading` or `consumption` depending on default preset upon scanning QR code
- Loading of required features' packages based on routes and folders' configurations (`PackageLoader` patch) improvement
- Node libraries versions upgrade
- CW2 package update
- Several fixes/improvements on Arrigo Views features
- Re-rendering issues caused by folder switch swipe function (mobile feature) fix
- Service worker resets on version bumps to prevent cache from now showing new content
- Notifications layout revamp
- `DynamicWidget` errors presentation improvement
- Folder title on `Dashboard` inherited widgets
