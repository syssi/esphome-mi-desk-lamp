# esphome-mi-desk-lamp

![GitHub actions](https://github.com/syssi/esphome-mi-desk-lamp/actions/workflows/ci.yaml/badge.svg)
![GitHub stars](https://img.shields.io/github/stars/syssi/esphome-mi-desk-lamp)
![GitHub forks](https://img.shields.io/github/forks/syssi/esphome-mi-desk-lamp)
![GitHub watchers](https://img.shields.io/github/watchers/syssi/esphome-mi-desk-lamp)
[!["Buy Me A Coffee"](https://img.shields.io/badge/buy%20me%20a%20coffee-donate-yellow.svg)](https://www.buymeacoffee.com/syssi)

ESPHome custom firmware for the Xiaomi Mi Desk Lamp (MJTD01YL)

## Getting Started

### Prerequisites

- [ESPHome](https://esphome.io/guides/installing_esphome) installed
- USB-to-serial adapter (3.3 V logic level, e.g. CP2102 or CH340)
- Soldering iron to access the UART pads inside the lamp

### Configuration

Copy `secrets.yaml` and fill in your Wi-Fi credentials:

```yaml
wifi_ssid: "your-ssid"
wifi_password: "your-password"
```

### First flash (serial)

The lamp must be opened to expose the ESP8285 UART pads. Connect the adapter:

| Adapter | Lamp pad |
|---------|----------|
| GND     | GND      |
| 3.3 V   | 3.3 V    |
| TX      | RX       |
| RX      | TX       |
| GND     | GPIO0    |

GPIO0 is not exposed as a button — solder a wire to the GPIO0 pad and pull it to GND while powering on to enter flash mode. Once flashing starts, the wire can be removed.

For a detailed walkthrough with photos of the disassembly and wiring, refer to the [Tasmota device page for the Xiaomi Mi Desk Lamp](https://tasmota.github.io/docs/devices/Xiaomi-Mi-Desk-Lamp/).

Then run:

```bash
esphome run mi_desk_lamp.yaml
```

### OTA updates

Once the firmware is running, all subsequent updates can be flashed wirelessly:

```bash
esphome run mi_desk_lamp.yaml
```

ESPHome will detect the device on the network and flash over-the-air automatically.

## Inspiration

* https://github.com/fvollmer/open-desk-lamp-firmware
* https://tasmota.github.io/docs/devices/Xiaomi-Mi-Desk-Lamp/
* https://github.com/Torxgewinde/Desk-Lamp-Alternative-Firmware
* https://www.reddit.com/r/Esphome/comments/j11ayw/working_configuration_for_xiaomi_mi_desk_lamp_1s/
