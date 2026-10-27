<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:102B2B,50:146B5D,100:9ACB68&height=230&section=header&text=OmniBand&fontSize=72&fontColor=F5FFF5&fontAlignY=40&desc=One%20download%20manager.%20Multiple%20internet%20connections.&descSize=17&descAlignY=64" alt="OmniBand. One download manager, multiple internet connections." width="100%">

### One download manager. Multiple internet connections.

OmniBand routes supported downloads across available network adapters and keeps everything in one queue.

[**Download for Windows**](https://github.com/khairulmzncode/omniband-open/releases/latest) | [Features](#-features) | [System requirements](#system-requirements) | [Browser extension](#-browser-extension)

</div>

---

## ✨ Features

- **Use multiple connections:** Route supported downloads over Wi-Fi, Ethernet, and tethered adapters.
- **Manage one queue:** View download progress and network adapter activity in the desktop app.
- **Pause and resume:** Continue transfers when the file host supports the required range requests and metadata.
- **Capture browser downloads:** Send downloads from Chrome or Edge to OmniBand with the companion extension.

> **How multi-connection works:** OmniBand distributes downloads handled by the app. It does not combine all Windows network traffic, and actual speed depends on the file host and the capacity of each connection.

## 🚀 Get started

1. Download the latest Windows installer from [GitHub Releases](https://github.com/khairulmzncode/omniband-open/releases/latest).
2. Run the installer and open OmniBand.
3. In the app, open **Settings** → **Set up extension** to connect Chrome or Edge.

### System requirements

- Windows 10 or Windows 11, 64-bit
- 64-bit (x64) processor
- 4 GB RAM recommended for Windows and OmniBand running together
- About 250 MB of free disk space for installation
- Internet connection and at least one enabled network adapter
- Chrome or Microsoft Edge for browser download capture (optional)

OmniBand includes the .NET runtime, so you do not need to install .NET separately. Multi-connection downloads require two or more active network adapters. The memory and disk figures above are practical recommendations, not measured minimums.

## 🌐 Browser extension

The Chrome and Edge companion extension captures browser downloads and hands them to the OmniBand desktop app. Install or connect it by following **Settings** → **Set up extension** in OmniBand.

## ⚠️ Windows installer notice

The installer is not code-signed yet. Windows may show its standard unknown-publisher warning when you run it.

## 📦 Releases

Download the latest installer or view previous versions on the [Releases page](https://github.com/khairulmzncode/omniband-open/releases).

The repository is intentionally limited to this README. Installers are distributed as release assets.
