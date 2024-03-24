# Utilities

## Converting `.mkv` videos to `.mp4`

```bash
export FF=filename
ffmpeg \
  -i "${FF}.mkv" \
  -c copy \
  -c:a aac \
  -movflags \
  +faststart \
  "${FF}.mp4"
```

Additional useful flags

```bash
# amplify the audio 
-filter:a "volume=2" \

# use only one audio track
# credit: https://superuser.com/a/639430
-map 0:v:0 \
-map 0:a:1 \

```

## Scanning Documents on Linux

### Rotate scanned pages

```bash
compress a PDF (save as optimized)
pdftk scan.pdf rotate 1-endEast output in.pdf
```

or

```bash
pdftk A=scan.pdf shuffle AoddWest AevenEast output in.pdf
```

or

```bash
pdftk in.pdf rotate 2down output in-new.pdf && rm in.pdf && mv in-new.pdf in.pdf
```

### Compress to ebook size

```bash
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dBATCH  -dQUIET -sOutputFile=out.pdf in.pdf
```
