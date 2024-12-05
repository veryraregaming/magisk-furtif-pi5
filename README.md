
# MagiskFurtif [![Magisk Module](https://github.com/Furtif/magisk-furtif/actions/workflows/magisk_module.yml/badge.svg)](https://github.com/Furtif/magisk-furtif/actions/workflows/magisk_module.yml)

## Description

A Magisk module designed to run FurtiF Tools on boot, specifically optimized for Pi 5 devices. The module includes automatic health checks, Discord notifications, and a double-login mechanism to ensure stable operation.

---

## Features

- Automated startup of FurtiF Tools and Pokémon GO
- Double-login mechanism to address first boot issues
- Health monitoring with automatic restarts for unresponsive apps
- Discord notifications for status updates (with optional message ID persistence)
- Configurable delays, coordinates, and settings through an external config file
- Optional integration with Rotom API for detailed health checks

---

## Setup Instructions

### 1. Prerequisites
Ensure required binaries (`curl` and `jq`) are installed. On devices with Termux, run:
```bash
pkg install curl jq
```

### 2. Configuration Setup

1. **Create or download** `furtifconfig.txt` with your desired settings.
2. **Push the config file** to your device:
   ```bash
   adb push furtifconfig.txt /data/local/tmp/
   ```
3. **Reboot your device** to apply the configuration.

---

### 3. Installation

#### Option A: Pre-Built
1. **Download the Latest Release**
   - Go to the [Releases Page](https://github.com/veryraregaming/magisk-furtif-pi5/releases).
   - Download the latest `MagiskFurtif-<version>.zip`.

2. **Flash the ZIP**
   - Flash the downloaded ZIP file using **Magisk Manager** or **TWRP**:
     - **Magisk Manager**:
       1. Open Magisk Manager.
       2. Go to **Modules** > **Install from Storage**.
       3. Select the downloaded ZIP file.
       4. Reboot your device.
     - **TWRP**:
       1. Boot into TWRP Recovery.
       2. Tap **Install**.
       3. Select the downloaded ZIP file.
       4. Swipe to flash.
       5. Reboot your device.

3. **Edit the Configuration**
   - Extract the ZIP file and locate `furtifconfig.txt` inside the module's folder.
   - Edit it with your settings (e.g., device name, Discord webhook).

4. **Push the Configuration to Your Device**
   - Use the following command to push the configuration file:
     ```bash
     adb push furtifconfig.txt /data/local/tmp/
     ```

5. **Reboot Your Device**
   - Reboot your device to apply the changes.

#### Option B: Build from Source
1. **Clone the repository**:
   ```bash
   git clone https://github.com/veryraregaming/magisk-furtif-pi5.git
   ```
2. **Edit the `furtifconfig.txt` file** in the cloned directory.
3. **Build the module**:
   ```bash
   python3 build.py
   ```
4. **Flash the built ZIP** from the `builds` directory using Magisk Manager.

---

## Configuration

The `furtifconfig.txt` file controls various aspects of the module, including:

- Device name and Discord webhook settings
- Rotom API configuration (optional)
- APK package names and activities
- UI interaction coordinates for taps and swipes
- Timing delays for app operations and retries

Refer to `base/furtifconfig.txt` in the repository for an example configuration.

---

## Troubleshooting

### Common Issues
1. **Services Fail to Start**:
   - Ensure the configuration file is placed at `/data/local/tmp/furtifconfig.txt`.
   - Verify your device-specific coordinates and delays match its screen resolution.
2. **Discord Notifications Not Sent**:
   - Check webhook URL in `furtifconfig.txt`.
   - Ensure `curl` is installed and working.
3. **Logs**:
   - Use `logcat` to debug errors related to startup or app interactions.

### Checking and Setting Device Resolution and DPI
The script is based on the default resolution and DPI for Raspberry Pi 5 devices, which are expected to be:

- **Resolution**: `1920x1080`
- **DPI**: `240`

If these values do not match, you may encounter issues with UI interactions. Follow these steps to verify and set them:

1. **Check Resolution**:
   - Run the following ADB command:
     ```bash
     adb shell wm size
     ```
     Example output:
     ```
     Physical size: 1920x1080
     ```

2. **Check DPI**:
   - Run the following ADB command:
     ```bash
     adb shell wm density
     ```
     Example output:
     ```
     Physical density: 240
     ```

3. **Set Resolution and DPI**:
   - If the values are not correct, set them to the default values using these commands:
     ```bash
     adb shell wm size 1920x1080
     adb shell wm density 240
     ```

4. **Reset to Defaults**:
   - If you've made changes and want to reset to the original settings:
     ```bash
     adb shell wm size reset
     adb shell wm density reset
     ```

5. **Verify Changes**:
   - Recheck the resolution and DPI using:
     ```bash
     adb shell wm size && adb shell wm density
     ```

6. **Detailed Display Information**:
   - For full display details, run:
     ```bash
     adb shell dumpsys display | findstr "mBaseDisplayInfo"
     ```

---

### Binary Directory Setup
Depending on your device, you may need to modify the Termux binary path:

- Default Pi 5 path: `/data/data/com.termux/files/usr/bin`
- Alternative paths:
  - `/system/xbin`
  - `/vendor/bin`
  - `/system/bin`

---

Thank you to [Furtif](https://github.com/Furtif) for their incredible tools and inspiration for this project!
