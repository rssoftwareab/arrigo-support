# Change Log

### `1.0.82` (*2021-01-13*)

#### New Features

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

#### Fixes/Improvements

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