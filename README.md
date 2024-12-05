# MagiskFurtif [![Magisk Module](https://github.com/Furtif/magisk-furtif/actions/workflows/magisk_module.yml/badge.svg)](https://github.com/Furtif/magisk-furtif/actions/workflows/magisk_module.yml)

## Description

A Magisk module designed to run FurtiF Tools on boot, specifically optimized for Pi 5 devices. The module includes automatic health checks, Discord notifications, and a double-login mechanism to ensure stable operation.

## Features

- Automated startup of FurtiF Tools and Pokémon GO
- Double-login mechanism to address first boot issues
- Health monitoring with automatic restart
- Discord notifications for status updates (with message ID persistence)
- Configurable delays and coordinates through external config file
- Support for Rotom API integration

## Setup Instructions

### 1. Prerequisites (Might be unnecessary)
Install the required dependencies in Termux:
```bash
pkg install curl jq
```

### 2. Configuration Setup

1. Download or create `furtifconfig.txt` with your settings
2. Push the config file to your device:
```bash
adb push furtifconfig.txt /data/local/tmp/
```
3. Reboot your device

### 3. Installation

#### Option A: Using Pre-built Module
1. Download the latest release from the [releases page](https://github.com/veryraregaming/magisk-furtif-pi5/releases/)
2. Flash the zip using Magisk Manager
3.Push the config file to your device:
```bash
adb push furtifconfig.txt /data/local/tmp/
```
4. Reboot your device

#### Option B: Building from Source
```bash
git clone https://github.com/veryraregaming/magisk-furtif-pi5.git
cd magisk-furtif-pi5
edit furtifconfig.txt
python3 build.py
```
The built module will be available in the `builds` directory.

## Configuration

The `furtifconfig.txt` file controls various aspects of the module:

- Device name and Discord webhook settings
- Rotom API configuration
- APK package names and activities
- UI interaction coordinates
- Timing delays for various operations

Example configuration can be found in the repository's `base/furtifconfig.txt`.

## Troubleshooting

### Common Issues
1. If the service fails to start, verify your config file is properly placed at `/data/local/tmp/furtifconfig.txt` prior to installation and reboot.
2. Check Discord notifications (if enabled) for status updates
3. Verify the coordinates in config match your device's screen resolution

### Binary Directory Setup
Depending on your device, you may need to modify the Termux binary path:

- Default Pi 5 path: `/data/data/com.termux/files/usr/bin`
- Alternative paths:
  - `/system/xbin`
  - `/vendor/bin`
  - `/system/bin`


## Version History

### v1.8 (Picasso)
- Implemented double login mechanism
- Added external configuration file support
- Enhanced stability with health monitoring
- Added Discord notification system
- Improved error handling and recovery

## Releases

New releases are automatically built when a version tag is pushed. To get the latest release:

1. Go to the [Releases page](https://github.com/veryraregaming/magisk-furtif-pi5/releases/)
2. Download the latest `MagiskFurtif-pi5-{version}.zip`
3. Flash through Magisk Manager

Latest version: v1.8 (Picasso)

Thank You Furtif!