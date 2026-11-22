<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:102B2B,50:146B5D,100:9ACB68&height=230&section=header&text=OmniBand&fontSize=72&fontColor=F5FFF5&fontAlignY=40&desc=One%20download%20manager.%20Multiple%20internet%20connections.&descSize=17&descAlignY=64" alt="OmniBand. One download manager, multiple internet connections." width="100%">

### One download manager. Multiple internet connections.

OmniBand is a Windows download manager that routes supported transfers across selected network adapters and keeps them in one queue.

OmniBand is proprietary software. The Windows installer is free to download from the product website. Release assets include the installer and portable app; desktop source code and the private extension signing key are not published here. The installer and portable package include the signed CRX and unpacked browser-extension folder.

[**Download for Windows**](https://ominbandweb.vercel.app/api/v1/download) | [Product website](https://ominbandweb.vercel.app/) | [How it works](#how-it-works) | [Tech stack](#tech-stack) | [Support on Ko-fi](#support)

</div>

---

## ✨ Features

- **Multi-adapter transfers:** Route supported downloads over Wi-Fi, Ethernet, and tethered adapters.
- **One download queue:** View progress and adapter activity in the desktop app.
- **Resume supported downloads:** Continue transfers when the file host provides compatible byte-range and file metadata support.
- **Browser handoff:** Send downloads from Chrome or Edge to OmniBand through the companion extension.
- **Adapter change detection:** Refresh the available adapter list as network connections change while the app is running.

Multi-adapter transfers only apply to downloads handled by OmniBand. They do not combine all Windows network traffic, and the result depends on the file host and the capacity of each connection.

## How it works

1. OmniBand detects active network adapters and lets you choose the connections to use.
2. For a compatible download, the app checks whether the server supports HTTP byte ranges, then requests file ranges in parallel. Connections are bound to the selected adapters.
3. The downloaded ranges are assembled into one file. Resume information lets compatible transfers continue after an interruption.
4. The Chrome and Edge extension captures a browser download and hands it to the desktop app using the browser's Native Messaging connection.

If the download server does not support byte ranges, OmniBand cannot split that file across adapters. More connections do not guarantee a faster download.

## Tech stack

| Component | Technologies |
| --- | --- |
| Windows desktop app | C#, .NET 10, WPF, and XAML |
| Download and network engine | .NET `HttpClient`, HTTP byte ranges, sockets bound to adapter IP addresses, and Windows network-interface notifications |
| Chrome and Edge extension | JavaScript, Chrome Extension Manifest V3, and Native Messaging |
| Product website | TypeScript, React 19, and Next.js 16 |

The product website is a separate project. It is not needed to install or run the Windows app.

## 🚀 Get started

1. Download the latest Windows installer free from the [OmniBand website](https://ominbandweb.vercel.app/api/v1/download).
2. Run the installer and open OmniBand.
3. In the app, open **Settings** → **Set up extension** to connect Chrome or Edge.

### System requirements

- Windows 11, 64-bit, or a Windows 10 Enterprise/LTSC version supported by [.NET 10](https://learn.microsoft.com/dotnet/core/install/windows#supported-versions)
- 64-bit (x64) processor
- 4 GB RAM recommended for Windows and OmniBand running together
- About 500 MB of free disk space to allow for the installer, temporary extraction, and installed app
- Internet connection and at least one enabled network adapter
- Chrome or Microsoft Edge for browser download capture (optional)

OmniBand includes the .NET runtime, so you do not need to install .NET separately. Multi-connection downloads require two or more active network adapters. The memory and disk figures above are practical recommendations, not measured minimums.

## 🌐 Browser extension

The Chrome and Edge companion extension captures browser downloads and hands them to the OmniBand desktop app. Open **Settings** → **Set up extension** in OmniBand. In Chrome or Edge on Windows, enable Developer mode, choose **Load unpacked**, and select the `chrome-extension` folder shown by the app. Standard Chrome on Windows blocks direct installation from a local CRX; the signed CRX is bundled for Web Store or managed distribution.

## ⚠️ Windows installer notice

The installer is not code-signed yet. Windows may show its standard unknown-publisher warning when you run it.

## 📦 Releases

Download the latest installer from the [OmniBand website](https://ominbandweb.vercel.app/api/v1/download) or [GitHub Releases](https://github.com/khairulmzncode/omniband/releases).

GitHub Releases contain the installer, portable app, checksums, and setup instructions; the extension ships inside the app packages rather than as a separate release asset. Desktop source code and the private signing key remain proprietary and are not published here.

### What's new in 1.0.3

- The self-contained installer and portable ZIP include the signed Chrome CRX and unpacked extension folder beside the desktop app.
- Browser setup points to the included extension folder. On Windows, install it with Developer mode → Load unpacked; Chrome Stable does not install an off-store local CRX directly.
- Uninstalling clears OmniBand settings, tasks, queues, secrets, logs, native-host registration, startup entries, and extracted extension files. Downloaded files in the chosen destination are kept; browser-installed extensions must be removed in Chrome or Edge.
- Added checksums and setup instructions for the release packages.
- The installer remains unsigned, so Windows may show its unknown-publisher warning. The download engine did not change in this packaging release.
## 🌐 Product website

Visit [ominbandweb.vercel.app](https://ominbandweb.vercel.app/) for product information and the download page.

## ☕ Support

If OmniBand is useful to you, you can support its development on Ko-fi:

<div align="center">

[![Support me on Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/miezan)

</div>
