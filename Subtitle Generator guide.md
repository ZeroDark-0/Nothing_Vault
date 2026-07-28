---
date: 2026-07-15T21:51
tags: []
---
part 1:
part 2: [[Subtitle Generator guide part 2]]
part 3: 

# <code style="color:cyan">use Purfview Faster Whisper XXL better then whisper CPP</code>

#  -> Subtitle Edit + Whisper Installation & Setup Guide
> Generate English subtitles for Japanese, Korean, and Chinese videos using AI (Whisper).

---

# Requirements

- Windows 10/11
- NVIDIA GPU (Recommended: RTX 3060/4060 or better)
- Internet connection (for downloading models)
- Around 4 GB free disk space (depending on the model)

---

# Step 1 - Download Subtitle Edit

Download the latest portable or installer version.

## Official Website
https://github.com/SubtitleEdit/subtitleedit/releases

Download:

```
SubtitleEdit-Windows-x64.zip
```

Extract it anywhere.

Example:

```
E:\Subtitles Generator\
```

Open:

```
SubtitleEdit.exe
```

---

# Step 2 - Install FFmpeg

Subtitle Edit requires FFmpeg for reading video/audio.

## Method 1 (Recommended)

Open Subtitle Edit

```
Options
    → Settings
        → Waveform/Spectrogram
```

Click

```
Download
```

Subtitle Edit automatically downloads and configures FFmpeg.

---

## Method 2 (Manual)

Download the Windows executable build.

Official builds:

https://www.gyan.dev/ffmpeg/builds/

Download:

```
ffmpeg-release-essentials.zip
```

Extract it.

The folder should contain

```
bin
│
├── ffmpeg.exe
├── ffprobe.exe
└── ffplay.exe
```

> **Important:** Do **not** download the FFmpeg **source code** (`Source Code.zip` or `.tar.gz`). It does not contain the required executable files.

---

# Step 3 - Launch Subtitle Edit

Run

```
SubtitleEdit.exe
```

---

# Step 4 - Open Your Video

Go to

```
Video
    → Open video...
```

Choose your video.

Subtitle Edit will automatically generate the waveform.

---

# Step 5 - Open Speech Recognition

Go to

```
Video
    → Speech to text...
```

---

# Step 6 - Configure Whisper

Use these settings.

## Engine

```
Whisper CPP
```

---

## Backend

If you have an NVIDIA GPU:

```
cuBLAS
```

If cuBLAS is unavailable:

```
Vulkan
```

Otherwise:

```
CPU
```

### Performance Ranking

```
cuBLAS ⭐⭐⭐⭐⭐
Vulkan ⭐⭐⭐⭐☆
CPU ⭐⭐☆☆☆
```

---

## Input Language

Choose the video's language.

Examples

```
Japanese
```

```
Korean
```

```
Chinese
```

---

## Translate

Enable

```
☑ Translate to English
```

Without this option, Whisper generates subtitles in the original language.

---

# Step 7 - Download a Whisper Model

Click the model selector.

Recommended models:

| Model | Size | Recommendation |
|---------|------|---------------|
| tiny | 77 MB | ❌ Too inaccurate |
| base | 148 MB | ❌ Not recommended |
| medium | 1.5 GB | ✅ Good |
| **large-v3-turbo** | **1.62 GB** | ⭐ **Best balance** |
| large | 3.1 GB | ⭐ Highest quality but slower |

Recommended:

```
large-v3-turbo
```

---

# Step 8 - Start Transcription

Click

```
Transcribe
```

Whisper will

- Extract audio
- Detect speech
- Translate to English
- Create subtitles automatically

---

# Step 9 - Save the Subtitles

Go to

```
File
    → Save As...
```

Save as

```
lesson01.srt
```

---

# Step 10 - Watch the Video

Use any video player.

Recommended:

- VLC Media Player
- MPC-HC
- PotPlayer

Place the subtitle file in the same folder as the video.

Example

```
Lesson01.mp4
Lesson01.srt
```

Most players will automatically load the subtitles.

---

# Recommended Settings (RTX 4060)

| Setting | Value |
|----------|-------|
| Engine | Whisper CPP |
| Backend | cuBLAS |
| Input Language | Korean / Japanese / Chinese |
| Model | large-v3-turbo |
| Translate to English | ✅ Enabled |
| Post Processing | ✅ Enabled |

---

# Tips

### Test First

Always test with a 1–2 minute clip before processing an entire lesson.

---

### Process One Lesson at a Time

For large courses (20–30 hours), process each lesson individually.

Advantages

- Easier to fix errors
- Less chance of failure
- Easier subtitle management

---

### Expected Speed (RTX 4060)

| Backend | Speed |
|----------|-------|
| CPU | Slow |
| Vulkan | Fast |
| **cuBLAS** | **Fastest** |

---

# Useful Links

## Subtitle Edit

https://github.com/SubtitleEdit/subtitleedit/releases

---

## FFmpeg

https://www.gyan.dev/ffmpeg/builds/

---

## VLC Media Player

https://www.videolan.org/vlc/

---

## Whisper (Project)

https://github.com/openai/whisper

---

# Folder Structure Example

```
Subtitles Generator/
│
├── SubtitleEdit-Windows-x64/
│   └── SubtitleEdit.exe
│
├── lesson01.mp4
├── lesson01.srt
│
└── ffmpeg/
    ├── ffmpeg.exe
    ├── ffprobe.exe
    └── ffplay.exe
```

---

# Workflow Summary

```
Download Subtitle Edit
        ↓
Install FFmpeg
        ↓
Open Video
        ↓
Speech to Text
        ↓
Engine → Whisper CPP
        ↓
Backend → cuBLAS
        ↓
Language → Korean/Japanese/Chinese
        ↓
Translate to English ✓
        ↓
Model → large-v3-turbo
        ↓
Transcribe
        ↓
Save .srt
        ↓
Watch with subtitles
```



---

