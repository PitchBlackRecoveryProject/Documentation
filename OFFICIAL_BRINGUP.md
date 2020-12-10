# Official Device Release for Maintainers and Developers

Maintainers and Developers can release new PBRP versions for Official Stable and Beta Releases. Please follow the [conventions](https://github.com/PitchBlackRecoveryProject/Documentation/blob/master/GREEN_Repositories.md) for the device tree.

## Device Maintainership 
Device maintainerships are managed through [vendor_utils/pb_devices.json](https://github.com/PitchBlackRecoveryProject/vendor_utils/blob/pb/pb_devices.json). You need to give Pull Request to the same repository with the changes/additions for device.

Here is the format for devices in `pb_devices.json` :
```JSON
{
  "vendor": {
    "codename": {
      "name": "Full Device Name",
      "maintainer": "Full Maintainer Name"
    }
  }
}
```

> NOTE: The `vendor` and `codename` are case sensitive and should EXACTLY match the `vendor` and `codename` as in the repository name and makefiles.

## Build and Release

Build and Release is managed through Circle CI, please refer to [Building Instructions](https://github.com/PitchBlackRecoveryProject/Documentation/blob/master/BUILDING_Instructions.md) for it.
