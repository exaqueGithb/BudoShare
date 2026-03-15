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
---

### Changing Boot and Miracast/DLNA Images

To customize the boot logo or Miracast/DLNA guide images:

1. Obtain the Firmware Image
   - Download the firmware `.img` file provided on the device’s manufacturer site or from the repository.

2. Extract the Firmware
   - Use a tool like `7-Zip`, `img unpacker`, or `simg2img` to extract the firmware.
   - Locate `system.img` inside the extracted firmware.

3. Mount or Extract `system.img`
   - On Linux/macOS, you can mount it using:

   ```bash
   sudo mount -o loop system.img /mnt/system
   ```

	•	Or use an ext4 extractor tool to unpack the contents.

	4.	Locate the Images
	•	Inside system.img, find the relevant images such as:

```bash
/res/drawable/miracast.jpg
/res/drawable/dlna.jpg
```

5.	Replace with Custom Images
	•	Prepare images in the same format (JPG/PNG) and resolution.
	•	Replace the existing images with your custom ones.

6.	Repack the Firmware
	•	Repack system.img using your extractor tool or mkfs.ext4.
	•	Reassemble the firmware image if needed.

7.	Flash Back to Device
	•	Use Rockchip Batch Tool or ADB/Fastboot to flash the modified firmware.
	•	Ensure to back up your original firmware before flashing.

---

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

