# Changelog

## Version 0.0.8
* `camera`:
  * Attributes update more frequently, to show recording mode and online status. Let me know if this causes any issues, as I achieve this by asking the Cameras to poll status every 30 seconds, and that is usually the case for a camera entity. In my own tests I have not seen any problems.
  * Fixed missing import of *core* component
  * Added Attribute *online* - Is true when the camera is Online else shows false. This attribute can be used to check if the camera is available before performing automations.
  * Added Attribute *up_since* - showing time when camera went Online, or Offline if Camera is not connected
  * Added Attribute *last_motion* - showing time within the last 24 hours, when motion was detected, if any.
  * If the camera is not online, the recording state will now correctly be *idle*
* `core`:
  * Fixed missing string conversion of error code
  * Fixed bug in error reporting, when Authentication Failed

## Version 0.0.7
* Fixed NoneType error when one or more cameras are offline at the time of Home Assistant start
* Minor code clean-up

## Version 0.0.6
* `binary_sensor`:
  * Changed default SCAN_INTERVAL to 3 seconds to optimize Motion Detection
* `camera`:
  * Added new service `camera.unifiprotect_save_thumbnail`. When calling this services the Thumbnail of the last recorded motion will be saved to disk, and could then be used in an automation, to send to a phone via the `notify` platform. Requires `entity_id` and `filename` as attributes.
* `sensor`:
  * Added new attribute `camera_type` to the sensor. Showing what type of Unfi Camera is attached to this sensor
* `Core Module`
  * changed size of the thumbnail image when being created.
  * fixed error when no *Last Motion* record exist
  * cleaned up the code, removing obsolete parts.