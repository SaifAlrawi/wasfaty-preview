# Vendored pdf.js (pdfjs-dist 4.6.82) — self-hosted, no CDN

pdfx 2.9.2 renders PDFs on web via **pdf.js (pdfjs-dist)**. Its installer
(`flutter pub run pdfx:install_web`) wires these files from a public CDN
(jsdelivr). We do NOT use the CDN: this is a health app, and loading a
runtime dependency from a third party would break offline viewing and leak
a request to an external host every time a patient opens a medical PDF.

These files are therefore **vendored locally** and served same-origin.

- Version: **4.6.82** — the exact version pdfx 2.9.2 targets
  (`pdfx/lib/src/renderer/web/constants.dart` + `bin/install_web.dart`).
- Files:
  - `pdf.min.mjs`         — the pdf.js library (sets `globalThis.pdfjsLib`)
  - `pdf.worker.min.mjs`  — the render worker (`GlobalWorkerOptions.workerSrc`)
  - `cmaps/*.bcmap`       — CID cmaps (Arabic / CJK fonts in real reports)
  - `LICENSE`             — Apache License 2.0 (pdf.js is Apache-2.0)
- Wired in `web/index.html` with LOCAL relative paths only.
- Upgrade path: if pdfx's targeted version changes, re-vendor the matching
  pdfjs-dist build and bump the paths — never point at a CDN.
