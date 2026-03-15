# BudoShare

**Miracast Sharing Device Custom Theme**

---

## Overview

BudoShare is a toolkit designed for RK3036-based Miracast/DLNA devices. It allows users to explore the device, customize boot and guide screens, and manage firmware through ADB and network access.

This toolkit is intended for users who want to safely modify device visuals and settings without compromising core functionality.

---

## Requirements

* Mac, Linux, or Windows
* Android Debug Bridge (ADB) installed
* RK3036-based device with network or USB ADB enabled
* Optional: root access

---

## Installation

1. Clone or download the repository.
2. Ensure `platform-tools` (ADB and Fastboot) are available in your system PATH.
3. Connect the device to your network or via USB for ADB access.

---

## Usage Examples

### Connect to Device via ADB

```bash
# From the platform-tools directory
./adb connect <DEVICE_IP>:5555
./adb shell
```

### find Device Filesystem

```bash
# Search for images
find / -iname "*.jpg" 2>/dev/null
find / -iname "*.png" 2>/dev/null

# List contents of a directory with extensions
ls -l /system/bin/*.jpg
ls -l /data/media/*.png
```


### Firmware Upload (using Rockchip Batch Tool)

* Open Rockchip Batch Tool
* Select the firmware `.img` file
* Connect the device in bootloader or download mode
* Upload and restore firmware

---

## Notes

* The toolkit is designed for RK3036-based devices; compatibility with other chipsets is not guaranteed.
* Make sure to back up all data before modifying firmware or system images.
* Modifications should only be performed on devices you own or have permission to modify.

