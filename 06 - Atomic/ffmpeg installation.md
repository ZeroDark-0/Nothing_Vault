---
date: 2026-07-15T21:57
tags: []
---
# FFmpeg Install & JFIF → PNG/JPG Conversion Cheatsheet

## 1. Installing FFmpeg

### Option A — via winget (quick, default location)

```powershell
winget install "FFmpeg (Essentials Build)"
```

Check it worked:

```powershell
ffmpeg -version
```

### Option B — via scoop

```powershell
scoop install ffmpeg-essentials
```

Scoop install script (if scoop itself isn't installed yet): https://get.scoop.sh

### Option C — Manual install to a custom location (e.g. `E:\ffmpeg`)

1. Download the zip from the gyan.dev builds page (release essentials or full): https://www.gyan.dev/ffmpeg/builds/
2. Extract it so you end up with:
    
    ```
    E:\ffmpeg\bin\ffmpeg.exeE:\ffmpeg\bin\ffprobe.exe
    ```
    
3. Add `E:\ffmpeg\bin` to PATH (current user):
    
    ```powershell
    $oldPath = [Environment]::GetEnvironmentVariable('Path', 'User')[Environment]::SetEnvironmentVariable('Path', $oldPath + ';E:\ffmpeg\bin', 'User')
    ```
    
    Or via GUI: Start Menu → "Environment Variables" → Edit env vars for your account → User variables → `Path` → Edit → New → `E:\ffmpeg\bin` → OK.
4. Restart your terminal, then verify:
    
    ```powershell
    ffmpeg -version
    ```
    

### Check which ffmpeg is actually running / its location

```powershell
Get-Command ffmpeg
```

or

```powershell
where.exe ffmpeg
```

(`where.exe` lists _all_ matches on PATH, in priority order — the first one is what actually runs.)

---

## 2. Opening a terminal directly in a folder

1. Open the folder in File Explorer.
2. Right-click in an empty area (not on a file).
3. Select **"Open in Terminal"** (or "Open PowerShell window here" on older Windows 10).

Alternative: click the File Explorer address bar, type `powershell` or `wt`, hit Enter.

---

## 3. Converting JFIF → JPG or PNG

### Single file

```powershell
ffmpeg -i "input.jfif" -update 1 "output.jpg"
```

```powershell
ffmpeg -i "input.jfif" -update 1 "output.png"
```

> `-update 1` tells ffmpeg this is a single image, not an image sequence — avoids the "does not contain an image sequence pattern" error.

### All JFIF files in a folder → JPG

```powershell
Get-ChildItem -Filter *.jfif | ForEach-Object {
    ffmpeg -i $_.FullName -update 1 ($_.BaseName + ".jpg")
}
```

### All JFIF files in a folder → PNG

```powershell
Get-ChildItem -Filter *.jfif | ForEach-Object {
    ffmpeg -i $_.FullName -update 1 ($_.BaseName + ".png")
}
```

### Convert + match "Date modified" in one pass (recommended for future batches)

```powershell
Get-ChildItem -Filter *.jfif | ForEach-Object {
    $out = $_.BaseName + ".png"
    ffmpeg -i $_.FullName -update 1 $out
    $pngFile = Get-Item $out
    $pngFile.CreationTime   = $_.CreationTime
    $pngFile.LastWriteTime  = $_.LastWriteTime
    $pngFile.LastAccessTime = $_.LastAccessTime
}
```

---

## 4. Verifying all JFIF files were converted

### Quick count check

```powershell
$jfif = (Get-ChildItem -Filter *.jfif).Count
$png  = (Get-ChildItem -Filter *.png).Count
Write-Host "JFIF: $jfif   PNG: $png"
```

### List any JFIF missing a matching PNG

```powershell
Get-ChildItem -Filter *.jfif | ForEach-Object {
    $target = $_.BaseName + ".png"
    if (-not (Test-Path $target)) {
        Write-Host "Missing: $target"
    }
}
```

---

## 5. Fixing "Date modified" after the fact (if originals still exist)

```powershell
Get-ChildItem -Filter *.jfif | ForEach-Object {
    $png = Get-Item ($_.BaseName + ".png") -ErrorAction SilentlyContinue
    if ($png) {
        $png.CreationTime   = $_.CreationTime
        $png.LastWriteTime  = $_.LastWriteTime
        $png.LastAccessTime = $_.LastAccessTime
    }
}
```

---

## 6. Deleting original JFIF files (only after verifying conversions!)

⚠️ `Remove-Item` deletes **permanently** — it does NOT use the Recycle Bin.

```powershell
Remove-Item *.jfif
```

Safer version — sends files to Recycle Bin instead:

```powershell
Get-ChildItem *.jfif | ForEach-Object {
    [Microsoft.VisualBasic.FileIO.FileSystem]::DeleteFile($_.FullName, 'OnlyErrorDialogs', 'SendToRecycleBin')
}
```

---

## Notes

- JFIF is essentially a JPEG under the hood, so `.jfif → .jpg` conversion is lossless-ish (no re-compression by default); `.jfif → .png` re-wraps it losslessly but won't recover quality already lost in the original JPEG compression.
- Always spot-check a few converted files before deleting originals.

---

## References / Links

|Purpose|Link|
|---|---|
|FFmpeg Windows builds (gyan.dev)|https://www.gyan.dev/ffmpeg/builds/|
|FFmpeg official site|https://ffmpeg.org|
|FFmpeg official documentation|https://ffmpeg.org/documentation.html|
|Scoop installer|https://scoop.sh|
|Scoop install script|https://get.scoop.sh|
|Winget docs (Microsoft)|https://learn.microsoft.com/windows/package-manager/winget/|
|Chocolatey (alt package manager, also listed on gyan.dev page)|https://chocolatey.org|
|PowerShell `Get-ChildItem` docs|https://learn.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem|
|PowerShell `Remove-Item` docs|https://learn.microsoft.com/powershell/module/microsoft.powershell.management/remove-item|
|PowerShell environment variables docs|https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables|