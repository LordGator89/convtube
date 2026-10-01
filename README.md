<div align="center">

<img src="https://convtube.com/favicon.svg" width="96" height="96" alt="ConvTube logo" />

# ConvTube App

**YouTube in any format – as a tiny native Windows app.**

Download videos and audio from 8K down to 144p, in 10 video and 8 audio formats.
Free, ad-free, no account, no tracking. A single ~490 KB EXE.

[![Download](https://img.shields.io/badge/Download-ConvTube.exe-7c5cff?style=for-the-badge&logo=windows&logoColor=white)](../../releases/latest)
&nbsp;
[![Website](https://img.shields.io/badge/convtube.com-ff4d6d?style=for-the-badge)](https://convtube.com/download.html)

![Windows 10/11](https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4?logo=windows&logoColor=white)
![x64](https://img.shields.io/badge/arch-x64-555)
![C++17](https://img.shields.io/badge/C%2B%2B-17-00599C?logo=cplusplus&logoColor=white)
![License: MIT](https://img.shields.io/badge/license-MIT-2bd99a)

</div>

<!-- Screenshot: put one at docs/screenshot.png and uncomment the line below.
<p align="center"><img src="docs/screenshot.png" width="720" alt="ConvTube App" /></p>
-->

## Features

- **Paste a link or search YouTube** right in the app, with thumbnails, channel, duration and view count
- **10 video formats:** MP4, MKV, WebM, MOV, AVI, FLV, 3GP, MPEG, OGV, WMV
- **Any quality:** Best, 8K, 4K, 2K, 1080p, 720p, 480p, 360p, 240p, 144p
- **8 audio formats:** MP3, M4A, AAC, FLAC, OGG, Opus, WAV, WMA, with 64–320 kbps
- **Whole playlists** with one click
- **Live progress** with time remaining, cancel at any time
- **17 languages:** English, Deutsch, Français, Español, Italiano, Português, Nederlands, Polski, Türkçe, Русский, Українська, العربية, हिन्दी, Bahasa Indonesia, 日本語, 한국어, 中文
- **Portable:** no installer, no admin rights, runs from any folder
- **Native and lightweight:** pure Win32 with Direct2D/DirectWrite, no Electron, no .NET, no runtime to install
- **High-DPI ready** (per-monitor DPI aware), with keyboard navigation

## Download

1. Grab **`ConvTube.exe`** from the [latest release](../../releases/latest) or from [convtube.com/download.html](https://convtube.com/download.html).
2. Run it. On first launch the app sets up its components automatically (see [How it works](#how-it-works)).

Each release lists the SHA-256 checksum and a link to a public malware scan. To check your download in PowerShell:

```powershell
Get-FileHash .\ConvTube.exe
```

> [!NOTE]
> **"Windows protected your PC"?** The app is new and not yet known to Microsoft SmartScreen.
> Click **More info** → **Run anyway**.

### Requirements

- Windows 10 (version 1703 or newer) or Windows 11, 64-bit
- An internet connection

## How it works

ConvTube App is a graphical front end. The heavy lifting is done by proven open-source tools:

| Component | Purpose |
| --- | --- |
| [yt-dlp](https://github.com/yt-dlp/yt-dlp) | Fetches videos, audio and metadata from YouTube |
| [FFmpeg](https://ffmpeg.org) ([yt-dlp build](https://github.com/yt-dlp/FFmpeg-Builds)) | Merges video and audio, converts to formats like AVI, WMV or 3GP |
| [Deno](https://github.com/denoland/deno) | JavaScript runtime that yt-dlp needs for YouTube |

On first launch the app downloads these directly from their official GitHub releases into
`%LOCALAPPDATA%\ConvTube\tools`. On later launches yt-dlp keeps itself up to date, so downloads keep working when YouTube changes.

If one of the tools is already next to the EXE or on your `PATH`, the app uses that one.

## Privacy

- No telemetry, no analytics, no account, no ads.
- The app only connects to **GitHub** (to download and update its components) and **YouTube** (search, previews and the downloads themselves).
- Settings (language, save folder, last selected formats) are stored in the registry under `HKEY_CURRENT_USER\Software\ConvTube`.

## Uninstall

1. Delete `ConvTube.exe`.
2. Delete the folder `%LOCALAPPDATA%\ConvTube`.
3. Optional: delete the registry key `HKEY_CURRENT_USER\Software\ConvTube`.

## Contributing

Bug reports, translations and pull requests are welcome.

- **Translations:** every language is a block in [`src/i18n.h`](src/i18n.h). Missing strings fall back to English.
- **Download problems:** please include the text from the app's **Log** panel in your issue. Most "it stopped working" errors come from YouTube changes and are fixed by a yt-dlp update, which the app installs on the next launch.

## Disclaimer

ConvTube App is meant for downloading content you own or are allowed to download, such as your own uploads,
Creative Commons or public-domain videos. Please respect copyright and YouTube's Terms of Service.
This project is not affiliated with YouTube or Google.

## License

The external tools it downloads at runtime come under their own licenses: yt-dlp ([Unlicense](https://github.com/yt-dlp/yt-dlp/blob/master/LICENSE)),
FFmpeg (GPL-3.0 for the build used), Deno ([MIT](https://github.com/denoland/deno/blob/main/LICENSE.md)).
They are not part of this repository or of `ConvTube.exe`.
