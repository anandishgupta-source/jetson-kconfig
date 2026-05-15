# jetson-kconfig

Interactive TUI for configuring and building Jetson kernel modules — no kernel knowledge required.

Auto-detects your board, lets you pick features from a checklist, then handles the build and install.

## Install

```bash
pip3 install jetson-kconfig
```

Or from source:

```bash
git clone https://github.com/anandishgupta-source/jetson-kconfig
cd jetson-kconfig
pip3 install .
```

## Run

```bash
sudo jetson-kconfig
```

(`sudo` is needed for the build/install steps. The TUI itself runs as root.)

## Features

| Feature | What it enables |
|---|---|
| CAN Bus | SocketCAN — `can_raw`, `can_bcm`, MCP251x |
| SPI Devices | `spidev` userspace SPI access |
| I2C Devices | `i2c-dev`, `i2c-tools` |
| USB Gadget | Serial, Ethernet, Mass Storage gadget modes |
| GPIO | `libgpiod`, character device GPIO |
| PWM | Tegra PWM sysfs |
| V4L2 / Camera | Video4Linux2 capture support |
| USB Webcam | UVC driver for USB cameras |
| 1-Wire Bus | DS18B20 and other 1-Wire sensors |
| FTDI / USB-Serial | FTDI, CP210x, CH341 USB-serial |
| WireGuard VPN | WireGuard kernel module |
| Netfilter | iptables / nftables firewall |

## How it works

1. **Detects your board** from `/proc/device-tree/model` — no manual selection needed
2. **You pick features** from a checklist
3. **Review screen** shows exactly what configs will change and what packages will install
4. **Builds and installs** the selected modules, installs userspace tools via `apt`, runs `depmod`

## Requirements

- NVIDIA Jetson running L4T (Ubuntu-based)
- Kernel headers: `sudo apt install linux-headers-$(uname -r)`
- Python 3.8+
- `pip3`
