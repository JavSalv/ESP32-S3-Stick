# ESP32-S3 Stick

> Breadboard-friendly ESP32-S3 module with onboard RTC, LiPo battery charger, and USB-C — designed for low-power and deep-sleep applications.

![Board render](images/ESP32-S3%20Stick-Cropped.png)

---

## Overview

The ESP32-S3 Stick is a compact development module built around the **ESP32-S3-WROOM-1** that fits standard 830-point breadboards leaving room on both sides of the module.
It combines a complete power path (USB-C input, LiPo charging, and a synchronous buck converter) with an ultra-low-power RTC clock, making it well suited for prototyping battery-operated IoT nodes, data loggers, and any application that relies on deep sleep.

---

## Features

### Microcontroller
- **ESP32-S3-WROOM-1-N16R2**: Dual-core Xtensa LX7 @ up to 240 MHz, 16 MB Flash, 2 MB PSRAM
- All GPIOs broken out to the standard 22-pin headers.

### Power
- **USB-C input** (USB 2.0, 16-pin receptacle) with correct CC pull-downs for UFP/sink detection
- **MCP73831** single-cell LiPo/Li-Ion charger with 100 mA charge current (configurable via R_PROG)
- **TPS629210** synchronous buck converter for 3.3V output up to 1A.
- **P-channel MOSFET load-sharing** (DMP2045U-7) seamless switchover between USB and battery with low dropout penalty.
- **USBLC6-2SC6** TVS diode array for USB ESD protection.

### RTC
- **RV-3028-C7** — ultra-low-power RTC (40 nA), ±1 ppm accuracy, I²C interface on IO13 (SCL) / IO14 (SDA)

### Connectivity & I/O
- **USB-C** - USB 2.0 FS data lines connected directly to ESP32-S3 USB transceiver (USB_D+ / USB_D−)
- **UART0** (TXD0 / RXD0) broken out for programming and debug
- **2 × 22-pin headers** 2.54 mm pitch, breadboard-compatible


### User Interface
- **RST button**: Reset the controller
- **BOOT button**: Enters download mode when held during reset
- **3 × status LEDs**: Charge status, power status and one user LED connected to GPIO48

---


## Pin Map

The Pin Map is similar to other ESP32-S3 modules like the ESP32-S3-DevKitC-1 or cheaper AliExpress clones.

![ESP32-S3-DevKitC-1 Pinout](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32s3/_images/ESP32-S3_DevKitC-1_pinlayout.jpg)

> **Note:** IO0 is the BOOT strapping pin — avoid driving it LOW at power-on unless entering download mode. IO45 and IO46 are also strapping pins; check the ESP32-S3 datasheet before using them as outputs.

### LiPo Battery

Connect a single-cell LiPo or Li-Ion battery (3.7 V nominal) to the battery connector (JST PH 2-pin 2mm pitch connector). The MCP73831 charges the battery at 100mA.

## License

Hardware design files are open source. See [LICENSE](LICENSE) for details.
