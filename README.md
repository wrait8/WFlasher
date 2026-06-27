# WFlasher - ESP32 Firmware Uploader

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/wrait8/WFlasher)
[![Python](https://img.shields.io/badge/python-3.6+-green.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-orange.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey.svg)]()

A professional, cross-platform firmware flashing tool for ESP32 microcontrollers with both interactive CLI and web-based interfaces.

---

## ✨ Features

- **Dual Interface**: Interactive CLI wizard and modern web GUI
- **Auto-Detection**: Automatically identifies connected ESP32 devices
- **Multi-Platform**: Works on Windows, macOS, and Linux
- **Real-time Progress**: Live flash progress and device feedback
- **Firmware Verification**: Optional MD5 verification after upload
- **Multi-File Support**: Flash bootloader, partition table, and application simultaneously
- **Remote Flashing**: Direct firmware download from GitHub releases
- **Serial Console**: Built-in serial monitor for debugging
- **Auto-Installation**: Automatic esptool dependency management

---

## 🚀 Quick Start

### Web Interface (Recommended)

Access the professional web flasher at: [https://wrait8.github.io/WFlasher/](https://wrait8.github.io/WFlasher/)

### CLI Installation

```bash
# Clone the repository
git clone https://github.com/wrait8/WFlasher.git
cd WFlasher

# Install dependencies
pip install pyserial colorama esptool
```

### CLI Usage

#### Interactive Mode
```bash
python WFlasher.py
```

#### Command-Line Mode
```bash
python WFlasher.py -p COM4 -f firmware.bin
```

---

## 📖 Command-Line Reference

| Option | Description | Default |
|--------|-------------|---------|
| `-p, --port` | Serial port (e.g., COM4, /dev/ttyUSB0) | Auto-detect |
| `-f, --firmware` | Path to firmware .bin file | Required |
| `-a, --address` | Flash address | 0x1000 |
| `-b, --baud` | Baud rate | 460800 |
| `--no-erase` | Skip flash erase | False |
| `--verify` | Verify after upload | False |

### CLI Examples

```bash
# Basic upload
python WFlasher.py -p COM4 -f firmware.bin

# Custom configuration
python WFlasher.py -p /dev/ttyUSB0 -f firmware.bin -a 0x2000 -b 921600

# Skip erase and verify
python WFlasher.py -p COM4 -f firmware.bin --no-erase --verify

# Multi-file flash
python WFlasher.py -p COM4 -f bootloader.bin -a 0x1000 -f partitions.bin -a 0x8000 -f app.bin -a 0x10000
```

---

## 🔧 Supported Devices

| Device Family | Support Level |
|---------------|---------------|
| ESP32 | Full |
| ESP32-S2 | Full |
| ESP32-S3 | Full |
| ESP32-C3 | Full |
| ESP32-C6 | Full |
| ESP8266 | Compatible |

---

## 📁 Project Structure

```
WFlasher/
├── index.html           # Web flasher interface
├── WFlasher.py          # CLI tool
├── README.md            # Documentation
└── requirements.txt     # Python dependencies
```

---

## 🛠️ Technical Architecture

### Web Interface
- **Framework**: Vanilla HTML5 + CSS3 + ES Modules
- **Protocol**: Web Serial API with esptool-js
- **Features**: Real-time logging, progress tracking, multi-file support
- **Deployment**: GitHub Pages

### CLI Tool
- **Language**: Python 3.6+
- **Core Library**: esptool
- **Dependencies**: pyserial, colorama
- **Mode**: Interactive wizard & batch scripting

---

## 🐛 Troubleshooting

### Web Interface Issues

**"Web Serial API not supported"**
- Use Chrome 89+, Edge 89+, or Opera 75+
- Ensure HTTPS or localhost connection

**"Failed to connect to ESP32"**
1. Hold BOOT button on ESP32
2. Click Connect
3. Release BOOT button after connection

**"Sync failed: Invalid response"**
- Check USB cable quality
- Try different baud rate
- Ensure ESP32 is in bootloader mode

### CLI Issues

**esptool not found**
```bash
pip install esptool
```

**Permission denied (Linux)**
```bash
sudo usermod -a -G dialout $USER
# Log out and back in
```

**ESP32 not detected**
- Hold BOOT button while connecting
- Check USB connections
- Try different USB port

---


## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request


---

**Made with ❤️ for the ESP32 community**
