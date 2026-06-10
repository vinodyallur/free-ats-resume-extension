# 📄 Free ATS Resume Builder — Chrome Extension

Convert **any** resume (PDF, DOCX, or TXT) into a clean, single‑column, **ATS‑friendly**
one‑page `.docx` — entirely **inside your browser**. No server, no sign‑up, nothing is
uploaded anywhere. Free & open source.

> This is the browser‑extension version of
> [free-ats-resume-builder](https://github.com/vinodyallur/free-ats-resume-builder)
> (the Python CLI/web‑app). The extension re‑implements the parser and DOCX generator
> in pure JavaScript so everything runs locally — required by Chrome's Manifest V3,
> which forbids running remote code.

---

## Why it's ATS‑friendly

Applicant Tracking Systems choke on tables, columns, text boxes, and images. The
generated DOCX uses only what parsers read reliably:

- Single column, plain selectable text
- Standard section headings (Experience, Education, Skills…)
- Real bullet lists, common font (Calibri), 0.5" margins
- No tables / images / text boxes / headers‑footers

---

## Install it (Load unpacked — for everyone, free)

1. Download this folder (clone the repo or download the ZIP and unzip it).
2. Open **chrome://extensions** in Chrome (or Edge: **edge://extensions**).
3. Turn on **Developer mode** (top‑right).
4. Click **Load unpacked** and select the `free-ats-resume-extension` folder.
5. Pin the **A** icon from the toolbar puzzle menu.

That's it — click the icon, choose your resume, and download the ATS version.

> Works in any Chromium browser: Chrome, Edge, Brave, Opera, Arc.

---

## How to use

1. Click the toolbar icon to open the popup.
2. Choose (or drag & drop) your `.pdf`, `.docx`, or `.txt` resume.
3. Click **Build ATS resume** — the `*_ATS.docx` downloads automatically.
4. Open it in Word/Google Docs, proofread, then **export to PDF** for applications.

---

## What's inside

```text
free-ats-resume-extension/
├── manifest.json          # Manifest V3
├── popup.html / .css / .js  # the toolbar UI + download flow
├── src/
│   ├── extract.js         # PDF/DOCX/TXT -> text (pdf.js + fflate)
│   ├── parse.js           # heuristic section parser
│   ├── docx.js            # ATS-friendly DOCX generator (OOXML + fflate)
│   └── convert.js         # file in -> DOCX blob out
├── lib/                   # vendored libraries (bundled locally for MV3)
│   ├── fflate.min.js      # MIT — zip/unzip
│   ├── pdf.min.js         # Apache-2.0 — pdf.js
│   └── pdf.worker.min.js  # Apache-2.0 — pdf.js worker
└── icons/                 # toolbar icons
```

---

## Privacy

100% client‑side. Your resume never leaves your computer — there is no network call
and no analytics. You can verify this in **chrome://extensions → Details → Inspect
views** (the Network tab stays empty during conversion).

---

## Publish to the Chrome Web Store (optional)

1. Zip the **contents** of this folder (so `manifest.json` is at the zip root).
2. Go to the [Chrome Web Store Developer Dashboard](https://chrome.google.com/webstore/devconsole)
   (one‑time \$5 registration fee charged by Google).
3. Click **Add new item**, upload the ZIP, fill in screenshots/description, and submit
   for review.

You can keep distributing it free via "Load unpacked" without paying anything.

---

## Limitations

- Scanned/image‑only PDFs have no selectable text, so they can't be parsed (no OCR).
- The parser is heuristic; always review the output and fix any mis‑sorted lines.
- Heavily designed resumes may need minor manual cleanup after conversion.

## License

[MIT](LICENSE). Bundled libraries keep their own licenses: pdf.js (Apache‑2.0),
fflate (MIT).
