# Basic Bringup Documentation for Early Birds
> Devs who want to try PBRP over TWRP, follow this guide

First things first,
- [x] You need an actual TWRP Device Tree or make one.

Then you just have to modify the omni_$CODENAME.mk file

### omni_$CODENAME.mk sample

```makefile
# Inherit from those products. Most specific first.
$(call inherit-product, $(SRC_TARGET_DIR)/product/embedded.mk)

# Add this line if your device is 64-bit
$(call inherit-product, $(SRC_TARGET_DIR)/product/core_64_bit.mk)
# Otherwise, If you have 32-bit device, add the below line instead of above line
$(call inherit-product, $(SRC_TARGET_DIR)/product/core_minimal.mk)

# Inherit from main device makefile, if had any. Otherwise, ignore.
$(call inherit-product, device/$CODENAME/device.mk)

# If your device is treble compatible (64-bit), add below line
$(call inherit-product, $(SRC_TARGET_DIR)/product/treble_common_64.mk)

# For some dalvik improvement, better to keep it
$(call inherit-product, $(SRC_TARGET_DIR)/product/runtime_libart.mk)

# If you want full multilingual support
$(call inherit-product, $(SRC_TARGET_DIR)/product/languages_full.mk)

# Inherit from PitchBlack Recovery's custom product configuration instead of OmniROM's
# Delete any line that imports OmniROM's vendor config
$(call inherit-product, vendor/pb/config/common.mk)

# Now add device specific BRAND, MODEL, BOARD, Props, etc. if needed.
# Set those variables here to overwrite the inherited values.
BOARD_VENDOR :=
PRODUCT_BRAND :=
PRODUCT_DEVICE :=
PRODUCT_NAME := omni_$CODENAME
PRODUCT_MANUFACTURER :=
PRODUCT_MODEL :=
TARGET_VENDOR :=  
```

### omni.dependencies skeleton

You must add at least an empty omni.dependencies file in you device tree even if it has no dependency.
Otherwise, roomservice might throw a warning or two. Best to be on the Safe side.

```json
[
]
```

### Read More

- A few special [Build Flags](BUILD_FLAGS.md) that might need to tweak you device.
- Also See through [Building Instructions](BUILDING_Instructions.md) for building in CircleCI.
