---
date: 2026-07-15T22:18
tags: []
---




# Translating Generated Subtitles to English (Subtitle Edit)

After generating subtitles with Whisper, you can translate them into English directly inside Subtitle Edit.

---

# Step 1 - Open the Generated Subtitle

If you just finished transcription, the subtitle will already be open.

Otherwise:

```
File
    → Open...
```

Select your generated subtitle file (`.srt`).

Example:

```
2. Tool Introduction.srt
```

---

# Step 2 - Open the Translate Menu

Go to

```
Translate
    → Auto translate...
```

---

# Step 3 - Configure Translation

Set the translation options.

## Source Language

```
Korean
```

(or Japanese / Chinese depending on the video)

## Target Language

```
English
```

## Translation Provider

Choose any available provider.

Recommended order:

- Google Translate
- Microsoft Translator
- DeepL (requires API key)
- LibreTranslate

---

# Step 4 - Start Translation

Click

```
Translate
```

Subtitle Edit will automatically translate every subtitle line.

---

# Step 5 - Verify the Translation

After translation you'll notice two columns.

| Column | Content |
|----------|---------|
| **Text** | English Translation |
| **Original text** | Original Korean |

Example:

| English | Original |
|----------|----------|
| Blender is a free, open source software... | 블렌더는 무료 오픈소스 프로그램입니다... |

This allows you to compare the translation with the original.

---

# Step 6 - Review the Translation

AI translations are usually very good but may occasionally:

- Split sentences awkwardly
- Miss technical terminology
- Produce unnatural wording

For example

### AI Translation

```
3D programs such as 3DMAX or Maya

As a major 3D tool, the number of users is increasing.
```

A more natural version would be

```
Compared to 3ds Max and Maya,
Blender has become one of the most widely used 3D tools.
```

You can edit any subtitle manually by clicking the text box at the bottom of Subtitle Edit.

---

# Step 7 - Save the English Subtitle

Go to

```
File
    → Save As...
```

Recommended filename

```
2. Tool Introduction.en.srt
```

This keeps the translated subtitles separate from the originals.

Example

```
2. Tool Introduction.mp4
3. Tool Introduction.srt      ← Original Korean
4. Tool Introduction.en.srt   ← English Translation
```

---

# Step 8 - Watch the Video

Open the video in your preferred media player.

Recommended:

- VLC Media Player
- MPC-HC
- PotPlayer

If the English subtitle has the same base filename as the video, most players will load it automatically.

---

# Batch Processing (Recommended for Large Courses)

If your course contains many videos (for example, 53 lessons), use Batch Mode.

Go to

```
Video
    → Speech to text...
        → Batch mode
```

Batch Mode allows you to:

- Select multiple videos
- Generate subtitles automatically
- Save all `.srt` files at once

This is ideal for large courses.

---

# Recommended Workflow

```
Video (.mp4)
        │
        ▼
Speech to Text (Whisper)
        │
        ▼
Generate Original Subtitle (.srt)
        │
        ▼
Translate
        ▼
Auto Translate
        │
        ▼
English Subtitle (.en.srt)
        │
        ▼
Review & Edit (Optional)
        │
        ▼
Save
        │
        ▼
Watch with English Subtitles
```

---

# -> Final Folder Structure

```
Course/
│
├── 01. Introduction.mp4
├── 01. Introduction.srt
├── 01. Introduction.en.srt
│
├── 02. Tool Introduction.mp4
├── 02. Tool Introduction.srt
├── 02. Tool Introduction.en.srt
│
├── 03. Modeling.mp4
├── 03. Modeling.srt
├── 03. Modeling.en.srt
│
└── ...
```

---

# Tips

- Keep the original subtitle (`.srt`) as a backup.
- Save translated subtitles with the `.en.srt` suffix.
- Review technical terms (e.g., Blender, Unity, Substance Painter, 3ds Max) to ensure they haven't been mistranslated.
- For long courses, process one lesson at a time or use Batch Mode to automate subtitle generation.
```