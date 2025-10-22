# 🖥️ Waveshare ESP32-S3-Touch-LCD-4 (480×480, Rev 3.0) – Home Assistant Dashboard Display

[![ESPHome](https://img.shields.io/badge/ESPHome-2025-blue.svg)](https://esphome.io/)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Compatible-brightgreen.svg)](https://www.home-assistant.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP32--S3-orange.svg)](https://www.waveshare.com/esp32-s3-touch-lcd-4.htm)

> 🧠 Bring your **Waveshare ESP32-S3-Touch-LCD-4 (480×480 Pixels, Rev 3.0)** to life as a **live, touch-enabled Home Assistant dashboard** using ESPHome and Strange-V’s RemoteWebView system.

Even though the ESP32-S3 can’t run a full web browser, this project makes it possible to **view and interact** with your Home Assistant dashboard — rendered remotely and streamed to the display in real time.

---

## 📑 Table of Contents
- [Overview](#-overview)
- [Hardware](#-hardware)
- [Software Stack](#-software-stack)
- [Configuration](#-configuration)
- [Network Layout](#-network-layout)
- [Interactivity](#-interactivity)
- [Recommended Dashboard Setup](#-recommended-dashboard-setup)
- [Quick Start](#-quick-start)
- [Demo](#-demo)
- [Future Improvements](#-future-improvements)
- [Credits](#-credits)
- [License](#-license)

---

## 🚀 Overview

This setup turns the **ESP32-S3 Touch LCD** into a **remote web terminal** for Home Assistant.

A Linux server renders your dashboard in **headless Chromium**, sends it as compressed frames to the ESP32 over **WebSockets**, and receives touch input back for full interactivity.


---

## 🧩 Hardware

| Component | Description |
|------------|-------------|
| 🧠 **Main Board** | [Waveshare ESP32-S3-Touch-LCD-4 (Rev 3.0)](https://www.waveshare.com/esp32-s3-touch-lcd-4.htm) |
| 💡 **Display** | ST7796 480×480 LCD (SPI) |
| ✋ **Touch Controller** | GT911 (I²C) |
| 🔋 **Memory** | 16 MB Flash / 8 MB PSRAM |
| 🌐 **Connectivity** | Wi-Fi (with fallback AP) |
| 💡 **Backlight** | Controlled via PWM (`light.display_backlight` in Home Assistant) |

---

## 🧰 Software Stack

| Component | Role | Repository / Docs |
|------------|------|------------------|
| **ESPHome** | Firmware framework | [esphome.io](https://esphome.io/) |
| **RemoteWebViewClient** | WebView streaming client for ESPHome | [strange-v/RemoteWebViewClient](https://github.com/strange-v/RemoteWebViewClient) |
| **RemoteWebViewServer** | Headless Chromium renderer | [strange-v/RemoteWebViewServer](https://github.com/strange-v/RemoteWebViewServer) |
| **JPEG Decoder** | Efficient frame decoding | [strange-v/jpegdec-esphome](https://github.com/strange-v/jpegdec-esphome) |
| **Home Assistant** | Dashboard source | [home-assistant.io](https://www.home-assistant.io/) |
| **Server OS** | Ubuntu Server 24.x | — |

---

## ⚙️ Configuration

The ESPHome YAML is included under [`/esphome/esp32-lcd4-ha.yaml`](./esphome/esp32-lcd4-ha.yaml).

### Highlights
- Secure Home Assistant API with encryption  
- OTA updates  
- Display backlight exposed as a controllable light entity  
- Touch-enabled web dashboard via `remote_webview`  
- Configurable dashboard URL via Home Assistant text entity  

---

## 🌐 Network Layout

| Component | Example Address | Description |
|------------|-----------------|--------------|
| **Home Assistant** | `http://homeassistant.local:8123` | Serves the dashboard web UI |
| **RemoteWebViewServer** | `http://server.local:8181` | Streams rendered frames |
| **ESP32-S3 Device** | DHCP / Static | Connects to Wi-Fi and WebView server |

---

## 🖱️ Interactivity

- The GT911 touchscreen sends touch coordinates back to the server  
- The server injects these events into the headless Chromium browser  
- Fully interactive Lovelace dashboards — toggles, sliders, buttons, etc.  

---

## 🧠 Recommended Dashboard Setup

While this setup works with any existing Home Assistant dashboard, you’ll get **much better usability** if you create a **custom Lovelace view optimized for 480×480 resolution** — larger buttons, minimal text, and simple layouts.

You can then configure your **RemoteWebViewServer** to point to that dashboard by default for a seamless panel experience.

---

## ⚡ Quick Start

```bash
# 1. Clone This Repository
git clone https://github.com/<yourusername>/esp32-s3-touch-lcd4-ha.git
cd esp32-s3-touch-lcd4-ha

# 2. Adjust Secrets
# Create or update your secrets.yaml with your Wi-Fi and API credentials.

# 3. Flash the Device
# Use ESPHome (CLI or dashboard) to upload the firmware:
esphome run esphome/esp32-lcd4-ha.yaml

# 4. Run the RemoteWebViewServer
# Follow instructions from the RemoteWebViewServer repo to install and launch it on Ubuntu Server:
# https://github.com/strange-v/RemoteWebViewServer

# 5. Connect and Enjoy
# - Power up the ESP32-S3
# - It connects to your Wi-Fi and streams the dashboard from your Home Assistant instance
# - Interact directly via touch on the display!
