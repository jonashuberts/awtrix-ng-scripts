# AWTRIX NG Apps

[![AWTRIX NG](https://img.shields.io/badge/AWTRIX-NG-FF6F00.svg)](https://github.com/Blueforcer/awtrix-ng)
[![Berry Language](https://img.shields.io/badge/language-Berry-blue.svg)](https://berry-lang.github.io/)
[![Hardware](https://img.shields.io/badge/hardware-Ulanzi%20TC001-green.svg)](https://blueforcer.github.io/awtrix-ng/)

A collection of lightweight, standalone [AWTRIX NG](https://github.com/Blueforcer/awtrix-ng) Berry (`.ax`) apps for the Ulanzi TC001 and other compatible LED matrix clocks.

All apps run completely autonomously on the device itself.

---

## 📱 Apps

### 1. Weather (`Weather.ax`)
A clean, memory-optimized weather app for AWTRIX NG.

- **Clean Display Layout**:
  - **Left (0, 0)**: High quality weather condition icon (8×8).
  - **Right (8 to 31)**: Centered temperature display (e.g. `24°` or `24°C`).
- **Keyless & Accurate**: Fetches live weather data from [Open-Meteo](https://open-meteo.com/) without requiring an account or API key.
- **Ultra Low Memory Usage**: Streams and extracts only ~160 bytes of JSON, making it reliable and lightweight on ESP32 microcontrollers.
- **Dynamic Temperature Colors**: Smooth gradient color coding from freezing purple/blue to mild green, warm yellow, and hot red.
- **Instant Display on Boot**: Caches the last known temperature and icon in persistent flash memory (`store`), displaying them immediately after clock startup.
- **Outdated Data Warning**: Displays a subtle red indicator pixel in the bottom-right corner if weather data is older than 20 minutes.
- **Manual Refresh**: Press the **middle button** on the clock to trigger an immediate update.

### 2. YouTube Subscriber Count (`YouTube.ax`)
A live subscriber tracker for any YouTube channel.

- **Native AWTRIX Icon**: Uses the native `youtube-2` (or `youtube`) icon with an automatic built-in graphic fallback.
- **Keyless**: Uses `api.socialcounts.org` to fetch live subscriber counts without needing a Google API key.
- **Smart Formatting**: Compact human-readable numbers (e.g. `1.2K`, `50.4K`, `1.5M`) with a clean red-to-pink gradient (`ramp_text`).
- **Concurrency Safe**: Includes TLS protection (`tls_busy()`) to avoid network stack collisions.
- **Instant Display on Boot**: Persistently stores the subscriber count to display immediately upon clock startup.
- **Manual Refresh**: Press the **middle button** on the clock to trigger an immediate update.

---

## 🚀 Installation

1. Open your browser and navigate to the AWTRIX NG Web interface:
   ```text
   http://<awtrix-ip>/
   ```
   *(e.g. `http://awtrix.local` or your device's local IP address)*
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
| `Format` | Select | `deg` | `deg` displays `24°`, `full` displays `24°C` |
| `Color by temperature` | Bool | `true` | Colorize text dynamically by temperature |
| `Refresh (minutes)` | Number | `15` | Update frequency in minutes (5–60) |

### YouTube Settings

| Setting | Type | Default | Description |
|---|---|---|---|
| `Channel ID` | Text | `UCGmQ7UYxfMAKYBbymrzf9-Q` | The `UC...` channel ID from your YouTube URL |
| `Icon ID/name` | Text | `youtube-2` | Icon name or ID in `/ICONS` (e.g. `youtube-2` or `youtube`) |
| `Refresh (hours)` | Number | `1` | Update frequency in hours (1–24) |

---

## 🎨 Icons

Both scripts use icons stored in the `/ICONS` directory on your AWTRIX.

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
