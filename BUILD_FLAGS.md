# Additional Build Flags Examples

This section provides custom PBRP Build Flags that can be used while building for devices.
Add these flags at the bottom of `BoardConfig.mk` file.
> Please refer to https://pitchblackrecovery.com/docs-category/how-to/ for more info.

### Maintainer Info

Builders/Maintainers can add their Name and/or Contact info inside PBRP's About section itself. Fancy, right?
```makefile
MAINTAINER := "Short Name and/or Telegram Id"
# MAINTAINER := "Rokib Hasan @fr3akyphantom" # Example, keep it short
```

### Disable dm-verity by default

dm-verity is enabled by default in PBRP, this build flag disables that by default.
```makefile
PB_DISABLE_DEFAULT_DM_VERITY := true
```

### Disable treble compatibility check by default

```makefile
PB_DISABLE_DEFAULT_TREBLE_COMP
```

### Force Use of `dd` for Flashing Recovery

There are many old devices (like legacy MTK devices) which follow traditional approach to flash recovery which can cause issues while flashing.
This is a EXPERIMENTAL flag, enable only if u are facing the same kind of issue.
```makefile
PB_FORCE_DD_FLASH := TRUE
```

### Specific Torch Path

For Specific Device Source path in PBRP, use this flag.
```makefile
PB_TORCH_PATH := /sys/class/leds/flashlight
```
