# Project 1: IoT Setup with Raspberry Pi 4 and ESP32

**Part 1 of my IoT Lab Series using ESP32 and Raspberry Pi 4**

## Overview

This project is the foundational step in building an IoT system using the Raspberry Pi 4 and ESP32 microcontroller.  
It covers setting up the Raspberry Pi with Ubuntu Server, connecting to WiFi, installing essential development tools, and flashing a "Hello World" program to the ESP32.

The goal is to prepare the hardware and environment for future embedded and IoT applications.

## Objectives

- ✅ Set up Raspberry Pi 4 with Ubuntu Server
- ✅ Connect Raspberry Pi 4 to WiFi (Eduroam / Home / Hotspot)
- ✅ Install XFCE Desktop Environment for user-friendly interface
- ✅ Install ESP32 software toolchain (ESP-IDF)
- ✅ Build and flash a simple "Hello World" program to the ESP32 board

## Project Structure

esp32-pi4-iot-setup/  
├── report.pdf # Lab report (required)  
├── raspberry-pi-setup/ # Raspberry Pi setup notes and configs  
├── esp32-hello-world/ # Lab 1.2: Hello World program  
│ ├── sdkconfig  
│ ├── CMakeLists.txt  
│ ├── README.md  
│ └── main/  
│ ├── CMakeLists.txt  
│ └── main.c  
├── esp32-blinky-led/ # Lab 1.3: Blinky LED program  
│ ├── sdkconfig  
│ ├── CMakeLists.txt  
│ ├── README.md  
│ └── main/  
│ ├── CMakeLists.txt  
│ └── main.c  


## Setup Instructions

### 🖥️ Raspberry Pi 4 Setup

1. **Install Ubuntu Server 64-bit**
   - Use Raspberry Pi Imager to flash the microSD card.
   - Choose Ubuntu 64-bit server image.

2. **Boot the Pi and login:**
username: ubuntu password: ubuntu

3. **Update and upgrade packages:**
sudo apt update sudo apt upgrade

4. **Install XFCE desktop (optional, but recommended):**
sudo apt install xfce4 xinit firefox

5. **Set up WiFi (Eduroam, Home WiFi, or hotspot).**
- Use `nmcli` for Eduroam.
- Install Network Manager:
  ```
  sudo apt install network-manager
  ```

6. **Install useful tools:**
sudo apt-get install fish neovim htop


### ⚙️ ESP32 Toolchain Setup

1. **Install required packages:**
sudo apt-get install g++ git wget flex bison gperf python3 python3-venv cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0

2. **Clone and install ESP-IDF:**
mkdir -p ~/esp cd ~/esp git clone --recursive https://github.com/espressif/esp-idf.git cd ~/esp/esp-idf ./install.sh esp32c3

3. **Source ESP-IDF environment:**
cd ~/esp/esp-idf . export.sh

### 🚀 Running "Hello World"

1. **Copy Hello World example:**
cp -a examples/get-started/hello_world ~/esp/ cd ~/esp/hello_world

2. **Set target and build:**
idf.py set-target esp32c3 idf.py build

3. **Flash to ESP32:**
- Connect ESP32 to Raspberry Pi (USB-C to USB-2 port).
idf.py flash

4. **Monitor output:**
idf.py monitor

5. **Modify main.c to print your name:**
```c
printf("Hello, Inhle Cele!\n");
```

## Notes
- Exclude build/ directories when zipping the project.

- Document issues or learnings in each subfolder’s README.md.

- All external code must follow APACHE or BSD-like licenses.

- Report any issues, even partial progress, in report.pdf.

### What I Learned
- Raspberry Pi 4 setup and configuration

- Ubuntu Server installation and WiFi setup

- ESP32 toolchain installation and environment setup

- Writing and flashing embedded programs

- Using FreeRTOS basics for multitasking

### Future Improvements
- Automate environment setup with scripts

- Expand ESP32 examples: sensors, Bluetooth, data logging

- Explore cloud integration for IoT data streams

## License
This project is for educational purposes.

Next Project: [ESP32 Sensor Data Logger](https://github.com/Inhle-C/Project-3-esp32-sensor-data-logger)  
(To be uploaded as Part 2 of the series)
