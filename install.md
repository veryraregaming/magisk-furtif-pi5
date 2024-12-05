
# How to Use MagiskFurtif

## 1. Download the Latest Release
- Go to the [Releases Page](https://github.com/veryraregaming/magisk-furtif-pi5/releases).
- Download the latest `MagiskFurtif-<version>.zip`.

## 2. Flash the ZIP
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

## 3. Edit the Configuration
- Open the `furtifconfig.txt` file inside the ZIP and edit it with your settings (e.g., device name, Discord webhook).

## 4. Push the Configuration to Your Device
- Use the following command to push the configuration file:
  ```bash
  adb push furtifconfig.txt /data/local/tmp/
  ```

## 5. Reboot Your Device
- Reboot your device to apply the changes.
