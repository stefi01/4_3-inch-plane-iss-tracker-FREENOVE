# Home Field Scope

Official firmware updates for the **Home Field Scope** 4.3 inch desk display sold on Etsy.

Board: FREENOVE ESP32 Display ESP32-S3 CYD 4.3" 480x272 TN Resistive Touch Screen.

This repo is the update feed that screen reads. Buyers do not need Arduino, Visual Studio, or a computer flash tool.

It is a desk gadget. It is not FAA equipment and not for navigation.

This is the Freenove 4.3 inch board. It is not the 7 inch Waveshare screen and not the 7 inch 8048 screen. Do not install a 7 inch bin on this glass.

## If you bought one

The scope must already be on Wi-Fi (2.4 GHz).

1. On the screen: **SETUP → ABOUT**
2. Tap **CHECK**
3. If a newer version is listed, tap **INSTALL**
4. Leave the USB power connected until it reboots

The screen downloads `ota/hfs_43.bin` from this repository and writes it by itself.

**No GitHub / no Wi-Fi update:** copy the 4.3 inch firmware onto a FAT32 microSD card, name it `HFS.BIN`, put the card in the scope, then **SETUP → ABOUT → FROM SD**. Do not unplug while it writes.

The published version is 3.63.

## Files

| File | What it is |
| --- | --- |
| `ota/version_43.txt` | One line, the latest version number (`3.63`) |
| `ota/hfs_43.bin` | The 4.3 inch firmware image the chip flashes |
| `Home Field Scope 4.3 inch User Manual.pdf` | The buyer manual |
| `sketch/Final_3.5/Final_3.5.ino` | The sketch |
| `sketch/Final_3.5/iss_world.h` | ISS earth picture used by the sketch |
| `sketch/Final_3.5/XPT2046_Touchscreen.h` | Touch header. The `.cpp` sits beside it |
| `libraries/ArduinoJson` | ArduinoJson 7.4.2 used to build this bin |
| `libraries/GFX_Library_for_Arduino` | GFX library used to build this bin. Cache flag stays false |
| `libraries/TJpg_Decoder` | JPEG decoder used for the map |
| `libraries/XPT2046_Touchscreen` | Touch library |

`ota/version_43.txt` and `ota/hfs_43.bin` must stay on branch `main` under `ota/`.

Wi-Fi, HTTP, SD, and SPI come with the esp32 board package. They are not in `libraries/`.

## Publish a new version (shop)

1. Bump the version in the 4.3 inch sketch (`HFS_VER`) and in `ota/version_43.txt` so they match.
2. Arduino IDE: **Sketch → Export compiled Binary**.
3. Rename that `.bin` to `ota/hfs_43.bin` and replace the copy here.
4. Push `ota/version_43.txt` and `ota/hfs_43.bin` to `main`.

The screen looks up:

- `https://raw.githubusercontent.com/stefi01/4_3-inch-plane-iss-tracker-FREENOVE/main/ota/version_43.txt`
- `https://raw.githubusercontent.com/stefi01/4_3-inch-plane-iss-tracker-FREENOVE/main/ota/hfs_43.bin`

This repository must stay **public** or CHECK / INSTALL will fail on buyer units.

The file the chip wants is a `.bin` built for the Freenove 4.3 inch board. An Intel `.hex` will not install. A 7 inch `.bin` will not fit this screen.

## Support

Etsy message the shop if CHECK fails, INSTALL stops, or the glass stays black after an update. Have the version from **SETUP → ABOUT** ready.
