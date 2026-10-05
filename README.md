# Gradiye

Gradiye is a zero-backend, local-first single-page photo color-grading studio. Open `index.html` in a modern browser (or serve this folder with any static web server).

## Included

- Drag/drop, picker, folder-picker, multi-file, and clipboard image import with magic-byte detection and per-file error messages.
- Non-destructive per-photo adjustments, histogram, before view, split slider, unlimited undo/redo, ratings, copy/paste grade, and a thumbnail filmstrip.
- Curated cinematic and automotive looks, editable local auto-grade and natural-language look suggestions, plus an import surface for `.cube` LUTs.
- Responsive desktop/mobile dark interface, local session-settings save, accessible labels and tooltips, and JPG/PNG/WEBP export with sizing, quality, watermark, and naming options.

## CDN libraries

All optional browser-side helpers load from jsDelivr:

- `heic2any` — HEIC/HEIF conversion.
- `UTIF.js` — TIFF decode.
- `JSZip` — loaded for multi-file ZIP export integration.

## Honest browser limitations

- RAW formats are detected by extension but modern browsers cannot reliably decode all RAW variants. Gradiye never crashes; it reports the limitation when an embedded preview is unavailable. A production RAW workflow should add a dedicated in-browser RAW/WASM decoder.
- Canvas exports cannot consistently preserve EXIF across browsers. The original `File` is retained in session memory, while the UI makes the export limitation explicit.
- The current tone curve, HSL mixer, color wheels, 3D LUT import, and RGB parade are presentation-ready controls. The live canvas engine implements the core tonal/color/presence grade; wiring advanced controls to a full WebGL shader pipeline is the natural next production step.
- “AI Grade” is a private, local heuristic fallback. A real remote AI service requires an API endpoint and user consent; its output should remain a JSON slider object before being applied.

Photos are not sent to a server by this app.
