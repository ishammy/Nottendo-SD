# Nottendo: Anemoia ESP32 based NES console project

This project is largely based and forked from **Shim06**'s [Anemoia-ESP32](https://github.com/Shim06/Anemoia-ESP32). Modified and catered for PCB design.

> Anemoia-ESP32 is a rewrite and port of the Anemoia Nintendo Entertainment System (NES) emulator running directly on the ESP32. It is written in C++ and is designed to bring classic NES games to the ESP32. This project focuses on performance, being able to run the emulator at native speeds and with full audio emulation implemented. However, games with complex mappers may induce a small speed loss.
> Anemoia-ESP32 is available on GitHub under the GNU General Public License v3.0 (GPLv3).

---

## Setup
#### Clone the repository
Copy and paste `git clone https://github.com/brylleee/nottendo` to your terminal to clone the repository

#### Open in Arduino IDE
1. Download and install the Arduino IDE. 
2. In <b> File → Preferences → Additional boards manager URLs </b> , add:
```cmd
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```
3. Download the ESP32 board support `v3.2.1` through <b> Tools → Board → Boards Manager </b>. 
> [!IMPORTANT]
> Make sure to download version 3.2.1, as different board versions may have worse performance.
4. Download the `TFT_eSPI` library from <b> Tools → Manage Libraries </b>.

#### Configure TFT_eSPI
The emulator uses a custom display configuration for the ST7789 display.
1. Navigate to your Arduino Libraries folder:
(Default location): `Documents/Arduino/libraries/TFT_eSPI`
2. Open `User_Setup_Select.h` in a text editor.
3. Comment out `#include <User_Setup.h>` and any other setup includes and add `<User_Setups/Anemoia-ST7789.h>`:
```C++
// #include <User_Setup.h>
#include <User_Setups/Anemoia-ST7789.h>
```
4. Copy the provided `Anemoia-ST7789.h` file from this repository into
`TFT_eSPI/User_Setups/`. Optionally, edit the `#define` pins as desired.
> ```C++
> #define ST7789_DRIVER
> // #define ILI9341_DRIVER
> ```

#### Apply custom build flags
1. Locate your ESP32 Arduino platform directory. This is typically at:
```cmd
\Users\{username}\AppData\Local\Arduino15\packages\esp32\hardware\esp32\{version}\
```
2. Copy the `platform.txt` file from this repository and paste into that folder.
This file defines additional compiler flags and optimizations used by Anemoia-ESP32.

#### Upload
1. Connect your ESP32 via USB.
2. In the Arduino IDE, go to <b> Tools → Board </b> and select ESP32 Dev Module.
3. Click Upload or press `Ctrl+U` to build and flash the emulator. Optionally, edit the `#define` pins as desired.

---

### Changes
- Removed SD card functionality
- Uses PAM8403 with no potentiometer
- Better UI 
