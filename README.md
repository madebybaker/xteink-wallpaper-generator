# Xteink X3 / X4 Wallpaper Generator

Turn any image into a sleep-screen wallpaper for the **Xteink X3** and **Xteink X4**
e-readers (CrossPoint firmware). Drop an image in, frame and tune it, and download a
file that's ready for the device.

**See it here: [xtwallgen.madebybaker.dev](https://xtwallgen.madebybaker.dev/)**

It's one self-contained file, `app.html`. It has no dependencies and no build step,
and it works offline. Everything runs in your browser, so your images are never
uploaded.

## Usage

1. Open `app.html` in a modern browser. You can double-click it or host it on any
   static server.
2. Drop an image onto **Input**, or click to choose one. PNG, JPEG, WebP and GIF
   all work.
3. Pick your **Device** and **Portrait / Landscape**.
4. Frame the image. Drag or use the arrow keys to move the crop, and scroll to
   zoom. You can also rotate it, or fit the whole image with white or black bars.
5. Tune it with a **Preset**, or set dither, brightness, contrast, gamma and
   sharpen yourself. The output preview updates live.
6. Click **Download**, then copy the file to the `/.sleep/` folder on the
   device's SD card.

## Devices

| Device | Resolution |
| ------ | ---------- |
| X3     | 528 × 792  |
| X4     | 480 × 800  |

Both panels show only four greys (0 / 85 / 170 / 255).

## Export formats

- **4-bit BMP** (default). The dither is baked in, and the palette maps 1:1 to
  the four panel greys.
- **PXC**. This is CrossPoint's native 2-bit format. It uses the same four levels
  and makes smaller files.
- **24-bit greyscale BMP**. It stays smooth in the browser, but the firmware
  hard-thresholds it without dithering, so gradients may show bands on the device.

## Why pre-dither?

CrossPoint doesn't dither. When a BMP's palette matches the four native greys
exactly, the firmware shows it as-is. Any other image gets snapped to the nearest
grey, which blows out highlights and bands gradients. That's why this tool dithers
to the native palette at the exact panel resolution before you export.

Dither options: Atkinson, Floyd–Steinberg, Jarvis–Judice–Ninke, Stucki,
Bayer 8×8, blue noise, or none.

## Notes

- HEIC/HEIF isn't supported because browsers can't decode it. Convert it to JPEG
  or PNG first.
- Phone photos are rotated automatically based on their EXIF orientation.

---

If you find this useful, you can [☕ buy me a coffee](https://buymeacoffee.com/madebybaker).
