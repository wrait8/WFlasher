# WFlahser - ESP32 Firmware Uploader

A Python-based firmware flashing tool designed specifically for ESP32 devices with both interactive and command-line modes. This tool provides a user-friendly interface for uploading firmware to ESP32 microcontrollers using esptool.

## 📋 Features

- **Interactive Mode**: User-friendly wizard-style interface for firmware uploads
- **Command-Line Mode**: Direct operation for automation and scripting
- **Auto-Detection**: Automatically detects connected ESP32 serial ports
- **Colorful Output**: Enhanced readability with color-coded status messages
- **Firmware Verification**: Option to verify uploaded firmware
- **Cross-Platform**: Works on Windows, macOS, and Linux
- **Automatic esptool Installation**: Installs esptool if not present

## 🚀 Quick Start

### Prerequisites

- Python 3.6 or higher
- pip (Python package manager)

### Installation

1. Clone this repository or download the script:

```bash
git clone https://github.com/wriat8/WFlasher.git
cd wflasher
```

2. Install required dependencies:

```bash
pip install pyserial colorama
```

### Usage

#### Interactive Mode
Simply run the script without any arguments:

```bash
python WFlasher.py
```

This will launch the interactive wizard that will guide you through:
- Automatic ESP32 port detection
- Firmware selection
- Flash address configuration
- Baud rate selection
- Upload confirmation
- Optional verification

#### Command-Line Mode
For direct operation or scripting:

```bash
python WFlasher.py -p COM4 -f firmware.bin
```

## 📖 Command-Line Options

| Option | Description | Default |
|--------|-------------|---------|
| `-p, --port` | Serial port (e.g., COM4, /dev/ttyUSB0) | - |
| `-f, --firmware` | Path to firmware .bin file | - |
| `-a, --address` | Flash address | 0x1000 |
| `-b, --baud` | Baud rate | 460800 |
| `--no-erase` | Skip flash erase | False |
| `--verify` | Verify after upload | False |

### Command-Line Examples

Basic upload:
```bash
python WFlasher.py -p COM4 -f firmware.bin
```

Custom address and baud rate:
```bash
python WFlasher.py -p /dev/ttyUSB0 -f firmware.bin -a 0x2000 -b 921600
```

Skip erase and verify:
```bash
python WFlasher.py -p COM4 -f firmware.bin --no-erase --verify
```

## 🔧 Supported Devices

WFlahser is specifically designed for ESP32 series microcontrollers:
- **ESP32**
- **ESP32-S2**
- **ESP32-S3**
- **ESP32-C3**
- **ESP32-C6**
- **ESP8266** (compatible)

## 🛠️ Technical Details

### Dependencies

- **pyserial**: Serial port communication
- **colorama**: Cross-platform colored terminal output
- **esptool**: ESP32 firmware tool (automatically installed if missing)

### How It Works

1. **Port Detection**: Scans available serial ports for potential ESP32 devices
2. **Firmware Preparation**: Validates firmware file and checks its size
3. **Flash Erase**: (Optional) Erases the ESP32 flash memory
4. **Firmware Upload**: Uploads firmware using esptool with ESP32-specific parameters
5. **Verification**: (Optional) Verifies the uploaded firmware on ESP32

### ESP32-Specific Features

- **Auto-Detection**: Identifies ESP32 bootloader ports (USB, ttyUSB, ttyACM)
- **Flash Addressing**: Supports standard ESP32 flash layouts (0x1000 for application)
- **Baud Rate Optimization**: Default 460800 baud for fast ESP32 uploads
- **Compatibility**: Works with ESP-IDF and Arduino-generated firmware

## 📁 Directory Structure

```
WFlasher/
├── WFlasher.py          # Main script
├── README.md           # This file
└── requirements.txt    # Python dependencies
```

## 🐛 Troubleshooting

### Common Issues

**esptool not found**
- The script attempts to install esptool automatically
- Manual installation: `pip install esptool`

**ESP32 not detected**
- Check USB connections
- Ensure ESP32 is in bootloader mode (some boards need to hold BOOT button)
- On Linux, ensure user has permissions: `sudo usermod -a -G dialout $USER`
- On Windows, check Device Manager for the correct COM port

**Permission denied (Linux)**
```bash
sudo chmod 666 /dev/ttyUSB0
```
Or add your user to the dialout group:
```bash
sudo usermod -a -G dialout $USER
```

**Upload timeout**
- Try reducing baud rate
- Check USB cable quality
- Ensure ESP32 is properly connected
- Try holding the BOOT button while uploading

**Failed to connect to ESP32**
1. Put ESP32 into download mode:
   - Hold the BOOT button
   - Press and release the RST/EN button
   - Release the BOOT button
2. Try again

## 💻 Development

### Building from Source

The script is self-contained and doesn't require compilation. Simply ensure all dependencies are installed.

### Adding New Features

The modular design makes it easy to add new features:
- Modify `upload_firmware()` for custom upload behavior
- Extend `get_ports()` for additional device detection
- Add new command-line arguments in `main()`

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.


## 📧 Support

For issues and feature requests, please open an issue on GitHub.

---

**WFlahser v1.0.0** - ESP32 Firmware Uploader
