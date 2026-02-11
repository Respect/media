# TheRespectPanda media files

 - logo_orig.svg: The original logo in SVG with distinct layers to be edited with Inkscape.
 - logo_optim.svg: SVG-optimized version with merged layers and optimized for the web.

### Converting to raster

Common commands (PNG, JPEG, WebP, AVIF) and optimization options:

**Fast rasterize with librsvg**

```bash
# width/height in px
rsvg-convert -w 1024 -h 1024 -o logo.png logo_orig.svg
```

**ImageMagick (conversion + flatten for JPEG)**

```bash
# PNG with transparent background
magick -background none -density 300 logo_orig.svg -resize 1024x1024 -quality 90 logo.png

# JPEG (flatten to white background)
magick -background white -alpha remove -density 300 -resize 1024x1024 -quality 85 logo.jpg
```

**WebP / AVIF (modern compressed formats)**

```bash
# WebP using cwebp from a PNG source
cwebp -q 80 logo.png -o logo.webp

# AVIF using libavif's avifenc
avifenc --min 20 --max 40 --speed 6 logo.png logo.avif
```

**Optimize PNGs**

```bash
# lossy quantization (very effective)
pngquant --quality=65-80 --output logo-pq.png -- logo.png

# lossless optimization
zopflipng --iterations=500 --lossy_8bit logo.png logo-zopf.png
```

**Generate multiple sizes (example)**

```bash
for s in 64 128 256 512 1024; do
  rsvg-convert -w $s logo_orig.svg -o "logo-${s}.png"
done
```

## Copyright

**Copyright (c) The Respect Project Contributors. All rights reserved.**

The images and logo assets in this repository may NOT be used, copied, modified, or redistributed without **explicit written permission** from the rights holder. If you need to use these files (for example, in marketing, apps, or third-party sites), please contact the repository owner to request permission.


