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

If CHECK says the version file is not on GitHub, no 4.3 inch update has been published yet.

## Files the screen uses

| File | What it is |
| --- | --- |
| `ota/version_43.txt` | One line, the latest version number (example `3.63`) |
| `ota/hfs_43.bin` | The 4.3 inch firmware image the chip flashes |

Those two files must stay on branch `main` under `ota/`.

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
