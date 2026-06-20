# Portfolio Website Updates — Implementation Plan

## Background

The current portfolio at [My-Portoflio-main](file:///c:/Users/USER/Music/My-Portoflio-main) is a **pre-built React + Vite + Tailwind + Framer Motion** application. The source code is **not present** — only the production-bundled files exist ([index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js), [index-U3qeWxqM.css](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-U3qeWxqM.css)). All content (text, data, components) lives inside the minified JS bundle.

Since there is no source code to modify, **we must directly edit the minified JS bundle** to implement the requested changes. This is feasible because the data objects and JSX component strings are intact in the bundle (just minified, not obfuscated with encrypted strings).

> [!IMPORTANT]
> **No source code exists.** All changes will be made by surgically editing the minified [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js) bundle. This is brittle but the only option without the original source.

---

## User Review Required

> [!IMPORTANT]
> **Section rename (Item 3):** You asked whether to rename "Programs & Systems Developed" — since you only have one college capstone project (OCR CHRMO Tracking), I recommend renaming it to **"Capstone Project"** or **"Academic Project"**. Please confirm which name you prefer.

> [!WARNING]
> **Item 6 (ui-ux-pro-max-skill):** The `uipro-cli` npm package does not appear to be a real/established tool. Searching for it yields no results. Running `npm install -g uipro-cli` and `uipro init --ai antigravity` would likely fail. I recommend **skipping this step** unless you can confirm the package exists and provide documentation. The portfolio changes can all be done without it.

---

## Open Questions

1. **Section rename for projects:** What should the section be called? Options:
   - "Capstone Project"
   - "Academic Project"
   - "College Project"
   - Keep "Programs & Systems Developed"

2. **Resume file format:** Your resume is a `.docx` file ([Kristopher_Canete_Resume.docx](file:///c:/Users/USER/Music/My-Portoflio-main/Kristopher_Canete_Resume.docx)). Browsers **cannot display `.docx` files inline**. Options:
   - **Convert to PDF** (recommended) — allows in-browser viewing and downloading
   - Keep as `.docx` — only download will work, no preview

3. **Item 6 (uipro-cli):** Should I skip this step since the package doesn't appear to exist?

---

## Proposed Changes

All changes target the single bundled JS file plus the resume file.

### 1. Hero Section — Make welcome text bigger

The hero heading currently uses classes like `text-4xl sm:text-5xl md:text-6xl lg:text-7xl`. We'll increase the font sizes slightly (e.g., `text-5xl sm:text-6xl md:text-7xl lg:text-8xl`) by editing the class strings in the minified bundle for the hero heading component.

#### [MODIFY] [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js)
- Find the hero component's heading class strings and bump up one size level

---

### 2. Remove "Trainings & Seminars" section and navigation link

#### [MODIFY] [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js)
- Remove `{id:"trainings",label:"Trainings"}` from the navigation array `Da`
- Remove the training section component call (`m.jsx(TS,{})` in the main layout)
- Remove the `H0` trainings data array (optional, reduces file size)

---

### 3. Replace Projects section — keep only OCR Capstone

#### [MODIFY] [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js)
- Replace the `$0` projects array with a single entry:
  - Title: "CHRMO Tracking System" (or similar based on your OCR capstone)
  - Category: "Capstone Project"
  - Repo link: `https://github.com/wanderingallen/CHRMO-TRACKING.git`
  - Demo: remove (no demo)
- Update section title from "Programs & Systems Developed" to the agreed-upon name
- Update the `{id:"projects",label:"Projects"}` nav label if needed

---

### 4. Resume Section Updates

#### [MODIFY] [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js)
- Remove the small "Resume" eyebrow text above the section
- Rename "My CV at a Glance" to **"My Personal Resume"**
- Change `F.resumeUrl` from `/resume.pdf` to `./Kristopher_Canete_Resume.docx` (or `.pdf` if converted)
- Update the download button to point to the actual resume file
- Rename nav item from `{id:"resume",label:"Resume"}` to `{id:"resume",label:"Resume"}` (keep label)

#### [NEW] Resume file setup
- If converting to PDF: create `Kristopher_Canete_Resume.pdf` from the `.docx`
- Ensure the file is accessible at the correct relative path

---

### 5. Remove Contact Section + Update Social Links

#### [MODIFY] [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js)
- Remove `{id:"contact",label:"Contact"}` from nav array `Da`
- Remove the contact section component call (`m.jsx(AS,{})` in the main layout)
- Update social links in config object `F`:
  - `github: "https://github.com/wanderingallen"`
  - `facebook: "https://www.facebook.com/hikris.canete/"`
  - `instagram: "https://www.instagram.com/thehollowabyss/"`

---

### 6. ui-ux-pro-max-skill Installation

> [!WARNING]
> **Skipping unless confirmed.** The `uipro-cli` package does not appear to exist in npm. Will skip this step pending user confirmation.

---

### 7. Remove Redundant Name in Footer

#### [MODIFY] [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js)
- In the footer component, remove or simplify the `F.name` display (currently shows "© 2026 Kristopher Allen N. Cañete. Built with ❤ using React + Tailwind.")
- Change to something like "© 2026. Built with ❤ using React + Tailwind." or just remove the full name

---

### 8. Remove "Experience & Projects" line in Resume Section

#### [MODIFY] [index-DOySAlae.js](file:///c:/Users/USER/Music/My-Portoflio-main/assets/index-DOySAlae.js)
- Remove the resume card that reads: `"Built 8+ academic and personal projects — see the Projects section above for full details."`
- This is the `Ri` component with `title:"Experience & Projects"`

---

## Verification Plan

### Manual Verification
- Open [index.html](file:///c:/Users/USER/Music/My-Portoflio-main/index.html) in browser after each major change
- Verify each section visually:
  1. ✅ Hero text is bigger
  2. ✅ No "Trainings & Seminars" section or nav link
  3. ✅ Projects section shows only the capstone with GitHub link
  4. ✅ Resume section says "My Personal Resume", no "Resume" eyebrow, download works
  5. ✅ No Contact section, social links updated in footer
  6. ✅ No redundant full name in footer
  7. ✅ No "Experience & Projects" card in resume section
