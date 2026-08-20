# Steam-FeatherWeight

![Version](https://img.shields.io/badge/version-v1.0.5-66c0f4)
![Python](https://img.shields.io/badge/python-3.8%2B-3776ab)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-8ed329)

**A very lightweight Steam game launcher.** No Electron, no bloat — a single Python file that lists the games on your account, shows which friends are online, and launches anything with one click via `steam://rungameid/`.

---

## ✨ Features

- 🎮 **Games only** — soundtracks, DLC, tools, SDKs, videos and other non-game apps are automatically filtered out of your library
- 👥 **Friends sidebar** — see who's online and what they're playing, with avatars (auto-refreshes every 60 s)
- 🚀 **One-click launch** — every game launches through the Steam client
- 🔍 **Instant search** with live filtering
- 🖼️ **Artwork & avatars** with a disk cache — second launch is near-instant
- ⚙️ **Settings page** — update checker, cache management, log out
- 🔄 **Auto update check** — compares against `version.json` and links you to the [releases page](https://github.com/imnotfisy/Steam-NaNo/releases) when a new version drops
- 🪶 **Featherweight** — small memory footprint, ~15 MB download as an exe



## 🚀 Getting started

### 1. Grab your login details

| What | Where to get it |
|---|---|
| **SteamID64** | [steamid.io](https://steamid.io/) or your profile URL — 17 digits starting with `76561…` |
| **Steam Web API key** | [steamcommunity.com/dev/apikey](https://steamcommunity.com/dev/apikey) (domain field can be anything) |

> ⚠️ Your Steam profile's **Game details** must be public for the library to load, and your **Friends list** must be public for the friends sidebar.

### 2. Download the exe

Head to the [releases page](https://github.com/imnotfisy/Steam-NaNo/releases/latest), download `Steam-FeatherWeight.exe`, and run it. Steam must be running and logged in for launches to work.

> **Note:** the exe is unsigned, so Windows SmartScreen may show a warning — click *More info → Run anyway*.

### 3. …or run from source

```bash
pip install customtkinter requests pillow
python steam_featherweight.py
```

Optionally place an `icon.ico` next to the script for the window icon.

## 🔨 Building the exe yourself

```bash
pip install pyinstaller
pyinstaller --onefile --windowed --name "Steam-FeatherWeight" --icon=icon.ico --add-data "icon.ico;." --collect-data customtkinter steam_featherweight.py
```

The exe appears in `dist\`. (On macOS/Linux, replace the `--add-data` separator `;` with `:`.)

## 🔄 How updates work

On launch (and via **Settings → Check for updates**) the app reads [version.json](https://raw.githubusercontent.com/imnotfisy/Steam-NaNo/refs/heads/main/version.json) and compares it against the running version. If you maintain releases, bump it with each release:

```json
{
  "version": "1.0.5"
}
```

## 🔒 Privacy & security

- Your API key and SteamID are stored **in plain text** at `~/.steam_featherweight/config.json` — only if you tick *Remember me*. **Log out** (Settings → Log out) or untick it to remove them.
- The app only *reads* Steam data via the official Web API. It can't buy, trade, or modify anything.
- Image caches live in `~/.steam_featherweight/cache/` and can be wiped from Settings.

## 🛠️ Troubleshooting

| Problem | Fix |
|---|---|
| `403 – invalid Web API key` | Re-check your key at steamcommunity.com/dev/apikey |
| Library empty / "no games" | Set profile **Game details** to public |
| Friends sidebar shows an error | Set your **Friends list** to public |
| Games don't launch | Make sure the Steam client is running and logged in |
| First launch is slow | Normal — it's classifying your apps; cached afterwards |
| No window icon | Put `icon.ico` next to the exe / script |

## 📄 License - MIT

All rights reserved.
