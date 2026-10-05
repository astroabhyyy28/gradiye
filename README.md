# Gradiye

Gradiye is a zero-backend, local-first single-page photo color-grading studio. Open `index.html` in a modern browser (or serve this folder with any static web server).

## Included

- Drag/drop, picker, folder-picker, multi-file, and clipboard image import with magic-byte detection and per-file error messages.
- Non-destructive per-photo adjustments, histogram, before view, split slider, unlimited undo/redo, ratings, copy/paste grade, and a thumbnail filmstrip.
- Curated cinematic and automotive looks, editable local auto-grade and natural-language look suggestions, plus an import surface for `.cube` LUTs.
- Responsive desktop/mobile dark interface, local session-settings save, accessible labels and tooltips, and JPG/PNG/WEBP export with sizing, quality, watermark, and naming options.
- A polished Gradiye logo opening animation, with an immediate skip action and automatic reduced-motion fallback.
- Pinch-to-zoom and pan directly on the photo on touch devices, plus dedicated zoom controls and double-click reset on desktop.

## Mobile and performance pass

On phones, Gradiye uses a focused stacked layout: compact navigation, large touch targets, a dedicated preview area, a horizontal filmstrip, and a bottom inspector for tools. Slider updates are coalesced to the next display frame, while mobile previews are rendered using a smaller proxy (long edge 1050px) to keep adjustments responsive. Full-resolution pixels are still used when exporting.

The preset browser now includes six additional film looks: Faded 35mm, Kodachrome, Portra Soft, Dusty Polaroid, Old Cinema, and Sepia Sunday.

## CDN libraries

All optional browser-side helpers load from jsDelivr:

- `heic2any` — HEIC/HEIF conversion.
- `UTIF.js` — TIFF decode.
- `JSZip` — loaded for multi-file ZIP export integration.

## Honest browser limitations

- RAW formats are detected by extension but modern browsers cannot reliably decode all RAW variants. Gradiye never crashes; it reports the limitation when an embedded preview is unavailable. A production RAW workflow should add a dedicated in-browser RAW/WASM decoder.
- Canvas exports cannot consistently preserve EXIF across browsers. The original `File` is retained in session memory, while the UI makes the export limitation explicit.
- The HSL mixer, tonal-curve range controls, and lift/gamma/gain balance controls are live canvas adjustments. A full Adobe Lightroom-equivalent implementation would additionally need draggable multi-point per-channel curves, visual wheel puck selection, 3D LUT application, and a GPU/WebGL pipeline for high-resolution real-time grading.
- “AI Grade” is a private, local heuristic fallback. A real remote AI service requires an API endpoint and user consent; its output should remain a JSON slider object before being applied.

Photos are not sent to a server by this app.
