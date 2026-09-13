# AWTRIX NG Scripts

[![AWTRIX NG](https://img.shields.io/badge/AWTRIX-NG-FF6F00.svg)](https://github.com/Blueforcer/awtrix-ng)
[![Berry Language](https://img.shields.io/badge/language-Berry-blue.svg)](https://berry-lang.github.io/)
[![Hardware](https://img.shields.io/badge/hardware-Ulanzi%20TC001-green.svg)](https://blueforcer.github.io/awtrix-ng/)

Native, standalone [AWTRIX NG](https://github.com/Blueforcer/awtrix-ng) Berry (`.ax`) scripts for **Weather** and **YouTube Subscriber Count**.

Everything runs directly on the clock (ESP32) — **no local MacBook server, Python daemon, or external bridge required.**

---

## 📱 Included Apps

### 1. Weather (`Weather.ax`)
A clean, memory-optimized weather app for AWTRIX NG.

- **Clean Display Layout**:
  - **Left (0, 0)**: High-resolution animated or static weather condition icon (8×8).
  - **Right (8 to 31)**: Clean, centered temperature display (e.g. `24°` or `24°C`).
  - *No moon phase clutter and no distracting bottom forecast bar.*
- **Keyless & Accurate**: Fetches live weather data from [Open-Meteo](https://open-meteo.com/) — no API keys or accounts required.
- **Ultra Low RAM Footprint**: Streams and filters only ~160 bytes of JSON on ESP32 microcontrollers without PSRAM.
- **Dynamic Temperature Color**: Smooth gradient color coding from freezing purple/blue to mild green, warm yellow, and hot red.
- **Instant Boot Display**: Caches the last known temperature and icon in flash memory (`store`), rendering immediately after a clock reboot.
- **Outdated Data Warning**: Shows a subtle red indicator pixel in the bottom-right corner if weather data is older than 20 minutes.
- **Manual Refresh**: Press the **middle button** on the clock to trigger an immediate update.

### 2. YouTube Subscriber Count (`YouTube.ax`)
A live subscriber tracker for any YouTube channel.

- **Proper AWTRIX Icon**: Uses the native `youtube-2` (or `youtube`) icon from `/ICONS` instead of crude hand-drawn pixel shapes, with an automatic drawn fallback if no icon file is found.
- **Keyless**: Uses `api.socialcounts.org` to fetch live subscriber numbers without needing a Google Cloud API key.
- **Smart Formatting**: Compact human-readable formatting (e.g. `1.2K`, `50.4K`, `1.5M`) with a smooth red-to-pink gradient (`ramp_text`).
- **RAM & TLS Safe**: Includes TLS concurrency protection (`tls_busy()`) to prevent Wi-Fi stack memory collisions on ESP32.
- **Instant Boot Display**: Stores subscriber counts in persistent memory to display immediately upon startup.
- **Manual Refresh**: Press the **middle button** on the clock for an immediate refresh.

---

## 🚀 Installation Guide

### Option 1: Web UI Copy & Paste (Recommended)

1. Open your browser and navigate to your AWTRIX NG Web interface:
   ```text
   http://<awtrix-ip>/
   ```
   *(e.g. `http://awtrix.local` or `http://192.168.1.5`)*
2. In the top navigation bar, click on **Scripts**.
3. Click **New Script** (or `+`):
   - **Name**: `Weather`
   - Copy the entire contents of [`Weather.ax`](Weather.ax) and paste it into the editor.
   - Click **Save** (or press `Ctrl+S`).
4. Repeat for YouTube:
   - Click **New Script**:
   - **Name**: `YouTube`
   - Copy the entire contents of [`YouTube.ax`](YouTube.ax) and paste it into the editor.
   - Click **Save**.

---

## ⚙️ Configuration

AWTRIX NG allows you to change app settings without editing code:

1. Open the Web UI and go to the **Apps** tab.
2. Click the **gear icon (⚙️)** next to your script row.

### Weather Settings

| Setting | Type | Default | Description |
|---|---|---|---|
| `Latitude` | Number | `48.05` | Geographic latitude of your location |
| `Longitude` | Number | `10.88` | Geographic longitude of your location |
| `Temperature unit` | Select | `C` | Choose between Celsius (`C`) and Fahrenheit (`F`) |
| `Format` | Select | `deg` | `deg` shows `24°`, `full` shows `24°C` |
| `Color by temperature` | Bool | `true` | Colorize text according to temperature |
| `Refresh (minutes)` | Number | `15` | Update frequency in minutes (5–60) |

### YouTube Settings

| Setting | Type | Default | Description |
|---|---|---|---|
| `Channel ID` | Text | `UCGmQ7UYxfMAKYBbymrzf9-Q` | The `UC...` channel ID from your YouTube URL |
| `Icon ID/name` | Text | `youtube-2` | Icon name or ID in `/ICONS` (e.g. `youtube-2` or `youtube`) |
| `Refresh (hours)` | Number | `1` | Update frequency in hours (1–24) |

---

## 🎨 Icons

Both scripts use high-quality icons stored in the `/ICONS` directory on your AWTRIX.

### Weather Icons
The weather script maps WMO weather codes to the following icon IDs:
- `53386` — Clear sky
- `2286` — Partly cloudy
- `53384` — Overcast
- `17055` — Fog
- `2720` — Rain / Drizzle
- `2289` — Snow
- `49300` — Rain showers
- `29839` — Thunderstorm
- `36637` — Unknown / Fallback

### YouTube Icon
- `youtube-2` (or `youtube`)

> **Tip:** You can download and install icons directly from the [AWTRIX Hub Icon Directory](https://awtrix.de/icons) or upload GIF/JPG files in the **Icons** section of your AWTRIX Web UI.

---

## 🗄️ Legacy Code

The legacy Python server daemon and macOS menu bar application previously used to push updates from a Mac to AWTRIX have been moved to the [`legacy/`](legacy/) folder. They are preserved for historical reference and are no longer required.
