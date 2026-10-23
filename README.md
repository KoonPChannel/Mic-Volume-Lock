# 🎙️ QuicklyzXD Mic Volume Lock

A lightweight, portable microphone volume keeper for **Windows 10/11 (64-bit)**. Choose an input device and a volume percentage; when locking is enabled, the app checks the Windows microphone level and restores the selected value if another application changes it.

> **v1.0 Preview — not yet runtime-tested on a physical Windows PC.** The Windows x64 build compiles successfully, but function, safety and compatibility testing is still required before presenting it as a stable release.

## Features

- Select Windows default microphone, default communications microphone, or a specific recording device
- Set microphone input volume to **0–100%**
- Lock mode checks the current volume every **350 ms** and restores the target when the difference exceeds 1 percentage point
- Minimize to **System Tray** and keep running
- Optional **Start with Windows** using a current-user Registry Run entry
- Remember microphone, volume and user settings
- Standalone native Win32 GUI built with Go; **no .NET or PowerShell runtime required**

## Download

You can build an executable from this source. Once this repository has been uploaded to GitHub, a Windows build will also run via **GitHub Actions**. Open **Actions → Build Windows EXE → latest successful run → Artifacts** to download the generated executable.

**Note:** An Actions artifact is a preview build, not a tested stable release. Do not disable antivirus or SmartScreen blindly.

## Usage

1. Launch `QuicklyzXD_Mic_Volume_Lock.exe` on Windows 10/11 x64.
2. Select the microphone to control.
3. Choose a target input volume, for example 85%.
4. Check **ล็อกเสียงไมค์ (เปิด/ปิด)** to start locking.
5. Optionally check **เปิดใช้งานอัตโนมัติพร้อม Windows** to start automatically at sign-in.
6. Close or minimize the window to keep running in the tray. Right-click its tray icon to exit completely.

## Build from source

Requires **Go 1.23+**; no third-party Go modules.

**Windows Command Prompt** (from this directory):

```bat
set GOOS=windows
set GOARCH=amd64
set CGO_ENABLED=0
go build -trimpath -ldflags="-H windowsgui -s -w" -o QuicklyzXD_Mic_Volume_Lock.exe .
```

**Linux / macOS cross-compile:**

```sh
GOOS=windows GOARCH=amd64 CGO_ENABLED=0 go build -trimpath -ldflags='-H windowsgui -s -w' -o QuicklyzXD_Mic_Volume_Lock.exe .
```

For detailed Thai instructions, see [README_TH.md](README_TH.md).

## Important limitations

- Controls the **Windows microphone endpoint volume**, not an application's own Automatic Gain Control, noise suppression, or sensitivity (for example, Discord).
- The program must remain running for the lock to function.
- The selected microphone must match the device the target application is using.
- Settings: `%APPDATA%\QuicklyzXD\MicVolumeLock\settings.json`.
- Start-with-Windows writes under `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`; it does not request administrator rights.
- This preview is unsigned; Windows SmartScreen may show a warning.
- This app has **not** been runtime-tested on real Windows hardware yet.

## Project and license

Personal project by **QuicklyzXD**, unrelated to IT Vertex. Licensed under the [MIT License](LICENSE).