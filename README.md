# ELMA IoT firmware releases

This public repository distributes assembled firmware for supported ELMA IoT devices. Windows and LCD/web OTA clients can discover board-specific release assets here without access to private application repositories.

## Available test target

- **VIEWE UEDX32480035E-WB-A, 3.5-inch 320 x 480**, ESP32-S3 N16R8, CHSC6540 touch and onboard SDMMC reader.
- ELMA compiled board profile: **25**.
- Asset naming: `elma-esp32s3-board25-<release-tag>.bin`.
- Initial releases are testing builds. Other boards will be added after their firmware is tested and corrected. A shared ESP32 chip alone does not make firmware interchangeable: use the exact board profile.

## Installation and OTA

Use the [Releases](https://github.com/elma-iot/ELMA-IoT-Firmware/releases) page. Each release identifies the supported board, firmware version, SHA-256 checksum, changes and remaining validation limits.

These `.bin` files are application images for OTA on devices already running a compatible ELMA partition layout. First installation or partition changes require the Windows application's USB compile/flash workflow; do not write an OTA image as a complete flash image at address zero.

In Firmware settings, use owner `elma-iot` and repository `ELMA-IoT-Firmware`. Board-specific builds match their compiled board ID; a missing compatible image must be reported as unavailable, not replaced by an image for another board.

Release builds contain clean project defaults, without personal Wi-Fi, MQTT, account credentials or user files. Saved settings are retained by normal OTA updates. Before switching from a custom build with personal compiled defaults, export the configuration: older builds stored only differences from their compiled defaults, so Wi-Fi or other default values may need to be reapplied with the Windows application after installing a clean image. Configure a newly installed device through its setup access point or the Windows application.

## Test scope

The first test build covers VIEWE LCD controls, synchronized web/LCD SD-format confirmation, dark-mode storage rendering and startup animation. Formatting erases the selected card and always requires explicit confirmation. The firmware offers FAT32; it does not claim exFAT/NTFS formatting support.

Release notes distinguish automated checks and device startup checks from features requiring further physical testing. More device-specific release images will be added as validation progresses.
