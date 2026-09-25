# Desk-Engine

**Desk Engine** — v5.1.0

Desk Engine is a professional, lightweight desktop overlay utility for Windows. It allows you to place GIFs, images, and videos directly onto your desktop, perfect for dashboard aesthetics, monitoring visual feeds, or just decorating your workspace.

<img src="https://github.com/user-attachments/assets/95f4f149-9f39-4981-9554-5b5eccc57bdc" width="450">

![Desk Engine Banner](https://img.shields.io/badge/Desk%20Engine-v5.1.0-818cf8) ![License](https://img.shields.io/badge/License-MIT-a78bfa) ![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-38bdf8)

## Features

- **Universal Media Support:** Play GIFs, static images (PNG, JPG, WebP, BMP, SVG, AVIF) and video files (MP4, WebM, MOV).
- **True Desktop Overlay:** Frameless, transparent windows that sit on your desktop.
- **Always on Top:** Overlays float above your windows and browser tabs — they never hide underneath. On-top mode can be toggled per overlay and defaults to ON.
- **Click-Through Mode (Pin):** Pin an overlay to lock it above everything — even fullscreen apps — while making it 100% click-through. Clicks, scrolls and even hovering pass straight through with zero visual reaction, so you can keep interacting with whatever is behind it.
- **Real GIF Speed Control:** GIFs are frame-decoded and played through a virtual clock, giving true 0.25×–2× speed control (browsers can't change GIF speed at all).
- **Multi-Monitor Done Right:** Each overlay remembers its monitor. Positions survive restarts, DPI changes, resolution changes and unplugged monitors — no more overlays restored off-screen.
- **Startup Persistence:** Pin your favorite overlays and Desk Engine reloads them automatically, exactly where you left them, when you restart your PC.
- **Real-Time Window Management:** Live control panel with per-overlay thumbnails, search, locate (flash) and bulk pin/unpin/close actions.
- **Global Hotkeys:** Close all overlays instantly with a custom global hotkey (Default: `Ctrl+/`, rebindable in Settings).
- **Drag & Drop:** Drop media files anywhere on the Control Panel to create overlays instantly.
- **Crash-Safe Settings:** Settings are written atomically (temp file + rename) — a crash can never corrupt `settings.json`.
- **Single Instance:** Launching the app twice just focuses the running instance instead of duplicating overlays.

## Download & Installation

1. Go to the **Releases** section on the right side of the page.
2. Download the latest **DeskEngine-Portable-5.1.0.exe**.
3. Double-click to run. No installation required.

> **Note:** Since this is an unsigned executable, Windows SmartScreen might show a warning. Click **"More info"** and then **"Run anyway"** to proceed.

## How to Use

### Basic Controls

- **Open Media:** Double-click the tray icon, click *Add media* in the Control Panel, or drop files onto the panel.
- **Move:** Click and drag the overlay with the Left Mouse Button (must be unpinned).
- **Menu:** Right-click the overlay for context options (Speed, Opacity, Size, Loop, Mute, Center, Always on top, Close).
- **Resize:** `Ctrl + scroll` over an overlay, or use the size presets in its context menu.
- **Pin (📌):** Double-click the overlay, the 📌 button in its hover bar, or the pin icon on its card.
  - **Unpinned:** The overlay acts like a normal draggable window and floats above other windows while you position it.
  - **Pinned:** The overlay locks itself **on top of all other windows** and becomes **fully click-through** — the mouse (hovering included) passes straight through it. Pinned overlays are restored at startup; unpin them from the Control Panel.

### Control Panel

The Control Panel allows you to:

- View and manage all active overlays (live thumbnails, monitor + size info, search, locate, bulk actions).
- Set default behaviors for new overlays (Opacity, Speed, **Always on top**, Loop, Mute).
- Manage Windows Startup settings (restores pinned overlays automatically).
- Rebind the global close-all hotkey, open the settings folder, or reset everything.

## ⚙️ Configuration

All settings are saved automatically in:

```
%APPDATA%\Desk Engine\settings.json
```

## 🛡 SmartScreen Warning

Because this application is not code-signed with an expensive Microsoft certificate, Windows Defender SmartScreen may warn you that it is an "unrecognized app". It is 100% safe.

1. Click **More info**.
2. Verify the App name (*Desk Engine*).
3. Click **Run anyway**.

##  For Developers (run from source)

```bash
git clone https://github.com/RAF-02/Desk-Engine
cd Desk-Engine
npm install

npm run dev            # development (Vite HMR + Electron)
npm start              # production run (builds the renderer first)
npm run dist           # build the portable Windows exe into release/
```

The portable exe is cross-buildable from Linux/macOS without wine — icons and version info are embedded by `build/after-pack.js` (resedit). A headless smoke suite is included (`npm run smoke`, plus the `DESK_ENGINE_SMOKE_PERSIST` phases — each prints `[SMOKE] ALL OK`).

**Stack:** Electron 33 · React 18 · Vite 5 · gifuct-js — media is streamed through a privileged local `dmedia://` protocol (no Node in renderers, strict CSP).

##  License

This project is licensed under the MIT License.
