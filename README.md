
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

1. Create or download `furtifconfig.txt` with your desired settings.
2. Push the config file to your device:
   ```bash
   adb push furtifconfig.txt /data/local/tmp/
   ```
3. Reboot your device to apply the configuration.

---

### 3. Installation

#### Option A: Pre-built Module
1. Download the latest release from the [releases page](https://github.com/veryraregaming/magisk-furtif-pi5/releases/).
2. Flash the downloaded ZIP using Magisk Manager.
3. Push the config file:
   ```bash
   adb push furtifconfig.txt /data/local/tmp/
   ```
4. Reboot your device.

#### Option B: Build from Source
1. Clone the repository:
   ```bash
   git clone https://github.com/veryraregaming/magisk-furtif-pi5.git
   ```
2. Edit the `furtifconfig.txt` file in the cloned directory.
3. Build the module:
   ```bash
   python3 build.py
   ```
4. Flash the built ZIP from the `builds` directory using Magisk Manager.

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

### Binary Directory Setup
Depending on your device, you may need to modify the Termux binary path:

- Default Pi 5 path: `/data/data/com.termux/files/usr/bin`
- Alternative paths:
  - `/system/xbin`
  - `/vendor/bin`
  - `/system/bin`


Thank you to [Furtif](https://github.com/Furtif) for their incredible tools and inspiration for this project!
