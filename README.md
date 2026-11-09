# TikTok Saver — No Watermark

[![Download](https://img.shields.io/badge/⬇_Download-Latest_Release-1DB954?style=for-the-badge&logo=github&logoColor=white)](https://github.com/YOUR_USERNAME/TikTok-Saver-NoWatermark/releases/latest)
[![Build](https://img.shields.io/github/actions/workflow/status/YOUR_USERNAME/TikTok-Saver-NoWatermark/ci.yml?label=Build&style=flat-square)](https://github.com/YOUR_USERNAME/TikTok-Saver-NoWatermark/actions)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows_10%2F11-lightgrey?style=flat-square&logo=windows)](#installation)

![TikTok Saver](assets/banner.svg)

A lightweight desktop utility for saving TikTok videos in original quality — **without the watermark overlay**. Paste a link, pick a folder, done. No account, no login, no telemetry.

## Features

- 🚀 **Original quality** — downloads the clean source stream (Full HD when available)
- 💧 **No watermark** — fetches the raw video file directly from the CDN
- 📋 **Clipboard monitoring** — copy a TikTok link and the app picks it up automatically
- 🖼 **Cover & audio export** — optionally save the thumbnail and MP3 audio track
- 📂 **Batch queue** — drop in dozens of links at once
- 🌓 **Dark / light theme** — follows the system theme
- 🔒 **Fully offline-friendly** — only talks to TikTok CDN endpoints, nothing else

## Installation

### Ready build (recommended)

1. Click the green **Download** badge above (or grab the archive from the [Releases](https://github.com/YOUR_USERNAME/TikTok-Saver-NoWatermark/releases) page).
2. Unpack `TikTok-Saver-NoWatermark-v2.4.1-win-x64.zip`.
3. Run `TikTokSaver.exe` — no installation required, portable build.

### From source

```bash
git clone https://github.com/YOUR_USERNAME/TikTok-Saver-NoWatermark.git
cd TikTok-Saver-NoWatermark
pip install -r requirements.txt
python -m tiktok_saver "https://www.tiktok.com/@user/video/1234567890"
```

## Usage

```
usage: tiktok-saver [-h] [-o OUTPUT] [--audio] [--cover] [--quiet] urls [urls ...]

Save TikTok videos without the watermark.

positional arguments:
  urls                  one or more video / profile links

options:
  -h, --help            show this help message and exit
  -o, --output          target folder (default: ./downloads)
  --audio               also export the audio track as MP3
  --cover               also save the video cover image
  --quiet               suppress progress output
```

Example:

```bash
python -m tiktok_saver -o "D:/Clips" --audio "https://vt.tiktok.com/XXXXXX/"
```

## How it works

The utility resolves short links, extracts the video ID, requests the item metadata from TikTok's public endpoint and downloads the `play_addr` stream — the same clean file TikTok serves internally, before the watermark is composited on top. No API keys required.

## Project layout

```
├── src/tiktok_saver/     # core package
│   ├── downloader.py     # link resolution + stream download
│   ├── cli.py            # command-line interface
│   └── utils.py          # helpers (filenames, progress, retries)
├── tests/                # unit tests
├── assets/               # banner & icons
├── docs/                 # extra documentation
└── release/              # packaged builds (attached to Releases)
```

## Building

```bash
pip install -r requirements.txt
pip install pyinstaller
pyinstaller --onefile --name TikTokSaver src/tiktok_saver/__main__.py
```

## FAQ

**Is an account required?**
No. The tool works with public videos only and never asks for credentials.

**Why are some videos saved with a watermark?**
Slideshows / photo-mode posts and some older regional posts only expose the watermarked stream. The tool falls back automatically and marks those files.

**Does it work with private videos?**
No — only publicly accessible content.

## Disclaimer

This project is not affiliated with, endorsed by, or sponsored by TikTok or ByteDance Ltd. It is intended for saving content the user has the right to access. Please respect creators' copyright and TikTok's Terms of Service.

## License

Distributed under the [MIT License](LICENSE).
