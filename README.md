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

