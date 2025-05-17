# Utilities

## Scanning Documents on Linux

### Great built-in Linux commands to work with text

`cut`, `sort`, `split`, `paste`, `join`, `wc`



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

## Images

### Bake updated metadata dates of images into the actual files

```bash
exiv2 -S .jpg.xmp insert FILE_NAME.jpg
```
