# AWTRIX NG Scripts

Two clean, standalone Berry scripts for [AWTRIX NG](https://github.com/Blueforcer/awtrix-ng). They run directly on your clock with no extra server required.

---

## 📱 Apps

### 1. Weather (`Weather.ax`)
- Current temperature & condition icon from [Open-Meteo](https://open-meteo.com/) (keyless).
- Clean layout: 8×8 weather icon on the left, centered temperature on the right.
- No moon phase and no bottom forecast bar.
- Low memory usage and instant display after reboot.

### 2. YouTube (`YouTube.ax`)
- Live subscriber count via `api.socialcounts.org` (no API key needed).
- Displays official YouTube Icon (`3389`) with gradient subscriber text.
- Concurrency-safe and instant display after reboot.

---

## 🚀 Quick Setup

1. Open your AWTRIX Web UI in your browser (`http://<awtrix-ip>/`).
2. Go to **Scripts** → Click **+** (New Script).
3. Create `Weather`, paste the contents of [`Weather.ax`](Weather.ax), and click **Save**.
4. Create `YouTube`, paste the contents of [`YouTube.ax`](YouTube.ax), and click **Save**.

### Icons
- **YouTube**: Uses Icon ID `3389` (works out of the box with pixel-perfect fallback, or upload [`3389.gif`](3389.gif) under **Icons**).
- **Weather**: Uses standard Hub icons (`53386`, `2286`, `53384`, `17055`, `2720`, `2289`, `49300`, `29839`).

---

## ⚙️ Settings

In the Web UI, go to the **Apps** tab and click the **gear icon (⚙️)** next to each app:

- **Weather**: Set your `Latitude` and `Longitude`, unit (`C`/`F`), and update interval.
- **YouTube**: Set your `Channel ID` (default: `UCGmQ7UYxfMAKYBbymrzf9-Q`) and update interval.
