# DermaComp
DermaComp — Dermal Compounding Intelligence Platform- Graduation Project

> **皮膚調合** · Egypt's first integrated dermal compounding intelligence platform  
> **Status:** Graduation Project — Team 1C, Faculty of Pharmacy, Modern University for Technology and Information (MTI)  
> **Supervisor:** Dr. Rehab Hamed · [Rehab.hamid@pharm.mti.edu.eg](mailto:Rehab.hamid@pharm.mti.edu.eg)  
> **Web Development:** Dr. Aliaa Omar

---

## Table of Contents

- [Overview](#overview)
- [Live Demo](#live-demo)
- [Features](#features)
- [Module Reference](#module-reference)
  - [Smart Calculator (PHI)](#smart-calculator-phi)
  - [Formulary Database](#formulary-database)
  - [Compatibility Checker](#compatibility-checker)
  - [API / Ingredient Database](#api--ingredient-database)
  - [Pharmacist Dashboard](#pharmacist-dashboard)
- [Pharmacopeial Standards](#pharmacopeial-standards)
- [Tech Stack](#tech-stack)
- [File Structure](#file-structure)
- [Getting Started](#getting-started)
- [User Authentication](#user-authentication)
- [Formulary Entries](#formulary-entries)
- [API Ingredient Database](#api-ingredient-database)
- [Responsive Design](#responsive-design)
- [Known Limitations & Roadmap](#known-limitations--roadmap)
- [Team](#team)
- [License & Disclaimer](#license--disclaimer)

---

## Overview

DermaComp is a single-file, browser-based compounding intelligence platform designed for pharmacists and pharmacy students working in dermal (topical and semi-solid) compounding. It consolidates the tools most needed at the compounding bench — precise formulation calculation, a curated formulary, ingredient compatibility checking, and an active pharmaceutical ingredient (API) reference database — into a single, offline-capable HTML application.

The platform is built around the **PHI (Pharmaceutical Intelligence)** engine, a modular calculation workspace that covers the full range of pharmaceutical calculations required by BP 2024, USP \<795\>, Ph.Eur. 11, ISO 22716:2007, ICH Q3C(R8), and WHO TRS guidelines.

---

## Live Demo

Open `dc_pro_v202.html` directly in any modern browser — no server or installation required.

```bash
# Clone and open
git clone https://github.com/<your-username>/dermacomp.git
cd dermacomp
open dc_pro_v202.html   # macOS
xdg-open dc_pro_v202.html  # Linux
start dc_pro_v202.html  # Windows
```

---

## Features

| Feature | Description |
|---|---|
| **Smart Calculator** | 10-tab PHI workspace covering formulation weights, dilution, concentrations, PPM, molarity, osmolarity, HLB, displacement value, suppository DV, and pH/buffer calculations |
| **Formulary Database** | Curated visual card library of dermal compound formulas with ingredients, preparation steps, BUD, storage, and pharmacopeial references |
| **Compatibility Checker** | AI-assisted drug-excipient compatibility screening with mechanism and clinical notes |
| **API Database** | 40 pharmaceutical-grade active ingredients with pH ranges, solubility profiles, safe topical concentrations, and regulatory status (Rx/OTC) |
| **Pharmacist Dashboard** | Personalised session tracking, calculation history, module analytics, and saved calculations (requires account) |
| **User Auth** | Sign-up / login with per-user localStorage persistence of activity, saved calculations, and visit stats |

---

## Module Reference

### Smart Calculator (PHI)

The PHI (Pharmaceutical Intelligence) workspace is the core of DermaComp. It is accessible via the **Calculator** section and contains 10 independent calculation modules, each aligned to a specific pharmacopeial reference.

| Tab | Module | Reference Standard |
|---|---|---|
| **Cream** | Cream/Ointment/Gel formulation weight calculator | BP 2024, USP \<795\>, ISO 22716 |
| **Suppository** | Suppository formulation with mold capacity | BP 2024 App. XI |
| **Solution** | Aqueous solution/suspension batch weight | BP 2024, Ph.Eur. 11 |
| **Serum** | O/W · W/O · Aqueous · Gel-Cream emulsion calculator | ISO 22716:2007, BP 2024 |
| **BUD** | Beyond-Use Date calculator | USP \<795\> 2023, ICH Q1A, WHO TRS Zone IVb |
| **Converter** | % w/v ↔ mg/mL, % w/v ↔ ppm, mg/mL ↔ molar, dose mg/kg → mL | BP/SI, ICH Q3C(R8) |
| **Dilution** | C₁V₁ = C₂V₂ dilution solver (any unknown) | IUPAC, BP 2024 App. XI |
| **Concentration** | % w/v, % w/w, % v/v calculators | BP 2024, USP, Ph.Eur. 11 |
| **PPM/Molarity** | ppm/ppb conversions, molarity/molality/normality | ICH Q3C · ECHA, SI Units |
| **Displacement/Osmolarity** | Suppository displacement value, osmolarity (mOsmol/L), HLB | USP \<785\>, BP/Ph.Eur. |

Each module outputs:
- Precise ingredient weights with percentage contributions
- A batch summary panel
- A pharmacopeial citation strip
- Export to PDF / Copy / Save buttons

#### PHI Sidebar Assistant

The sidebar includes a natural-language prompt input with suggested quick queries (e.g. "cream base for hydrocortisone 1%") that pre-populate the relevant module.

---

### Formulary Database

The formulary is a searchable, filterable card grid of curated compound formulas. Each card contains:

- **Formula name** and specialty label
- **Formulation type** (cream, ointment, solution, gel, serum, suppository, etc.)
- **pH** and **BUD label** with colour-coded BUD indicator (green / amber / red)
- A **thumbnail image** of the finished preparation

Clicking a card opens a **detail modal** with:

| Field | Content |
|---|---|
| Ingredients | Full ingredient list with exact quantities and roles |
| Preparation steps | Numbered compounding procedure |
| Storage | Container type, temperature, light conditions |
| BUD | Numerical expiry with USP/BP category reference |
| Pharmacopeial references | Linked citations |
| Warning | Rx restrictions, contra-indications, counselling points |

#### Filtering

The sidebar provides filter options by:

- Specialty (dermatology, pain, antifungal, anti-inflammatory, hormonal, etc.)
- Formulation type
- BUD level (green / amber / red)
- Rx / OTC status

---

### Compatibility Checker

A two-compound selector that returns a verdict (Compatible / Incompatible / Conditional) with:

- Mechanism of incompatibility
- pH sensitivity notes
- Clinical significance
- Reference tags

---

### API / Ingredient Database

A searchable table of 40 pharmaceutical-grade active ingredients with columns:

| Column | Description |
|---|---|
| Ingredient | INCI / BP name |
| Category | Brightening, Retinoid, Exfoliant, Acne, Moisturising, Antioxidant, Steroid, etc. |
| pH Range | Optimal pH window |
| Safe Concentration | Typical topical concentration range |
| Solubility | Vehicle compatibility notes |
| Regulatory Status | Rx or OTC badge |
| Notes | Stability, photosensitivity, vehicle preference |

Clicking any row expands a detail drawer with full specification fields including INCI name, molecular weight, storage requirements, and formulation notes.

Filter pills: All · Brightening · Exfoliant · Retinoid · Acne · Moisturising · Antioxidant · Steroid · Rx-only

---

### Pharmacist Dashboard

The dashboard is locked behind user authentication and tracks:

| Metric | Description |
|---|---|
| Total Calculations | Cumulative calculation count across all sessions |
| This Session | Calculations run in the current browser session |
| Total Visits | Number of sessions logged |
| Member Since | Days since account creation |
| Monthly Activity | Progress bar tracking calculations against a 30/month milestone |
| Module Breakdown | Bar chart of calculations per PHI module |
| Recent Activity | Timestamped log of last calculations |
| Saved Calculations | User-bookmarked calculation results |
| Full Activity Log | Scrollable complete history |

---

## Pharmacopeial Standards

DermaComp references the following standards throughout:

| Standard | Scope |
|---|---|
| **BP 2024** | Formulation, storage, beyond-use dating, percentage concentrations |
| **USP \<795\> 2023** | Non-sterile compounding, BUD categories (Table 1), repackaging limits |
| **USP \<785\>** | Osmolarity |
| **Ph.Eur. 11** | Emulsions (Crema), concentration conventions, App. 1.1 |
| **ISO 22716:2007** | GMP for cosmetics / topical preparations, INCI nomenclature |
| **ECHA Reg. 1223/2009** | Cosmetic ingredient regulation |
| **ICH Q1A** | Stability zones (IVb) |
| **ICH Q3C(R8)** | Residual solvent limits, ppm-molar conversion |
| **WHO TRS** | Zone IVb storage, paediatric dosing |

---

## Tech Stack

DermaComp is a **single HTML file** with no runtime dependencies or build process.

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | Custom CSS with CSS variables (Japandi/neutral palette) |
| Typography | Shippori Mincho (display), Noto Serif JP (Japanese), DM Mono (monospace), Inter, Mulish |
| Icons | Font Awesome 6.5.1 (CDN) |
| Charts | Chart.js (CDN, dashboard analytics) |
| Logic | Vanilla JavaScript (ES6+) |
| Auth / Storage | Browser `localStorage` (per-device persistence) |
| Deployment | Any static host (GitHub Pages, Netlify, local file system) |

---

## File Structure

```
dermacomp/
└── dc_pro_v202.html    # Entire application — single self-contained file
```

All CSS, JavaScript, formulary data, ingredient database, and embedded images are inlined within the single HTML file. No external files, build tools, or server are required.

---

## Getting Started

### Prerequisites

- Any modern browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- No Node.js, Python, or other runtime required

### Running Locally

```bash
# Option 1 — Direct file open
double-click dc_pro_v202.html

# Option 2 — Simple local server (avoids any browser file restrictions)
npx serve .
# or
python3 -m http.server 8080
# then open http://localhost:8080/dc_pro_v202.html
```

### Deploying to GitHub Pages

```bash
git init
git add dc_pro_v202.html
git commit -m "Initial deploy"
git branch -M main
git remote add origin https://github.com/<your-username>/dermacomp.git
git push -u origin main
# Enable GitHub Pages from repo Settings > Pages > Deploy from branch (main, root)
```

---

## User Authentication

DermaComp includes a lightweight client-side auth system. Credentials and usage data are stored in **browser localStorage** only — no server, no database, no cloud sync.

| Action | Behaviour |
|---|---|
| Sign Up | Creates a localStorage entry; immediately unlocks dashboard |
| Sign In | Validates against localStorage; restores saved calculations and history |
| Sign Out | Clears session state; dashboard re-locks |

> **Note:** Because auth data is device-local, clearing browser storage will delete the account. This is intentional for a standalone educational tool — no personal data leaves the browser.

---

## Formulary Entries

The built-in formulary includes compounds across the following specialties:

- Dermatology & Wound Care
- Pain & Muscle Relief
- Antifungal
- Anti-inflammatory & Steroid
- Hormonal / Compounded HRT
- Ophthalmology & ENT (topical)
- Paediatric formulations
- Cosmeceuticals

Each entry is traceable to at least one pharmacopeial reference and includes a BUD assigned per USP \<795\> 2023 Table 1 categories.

---

## API Ingredient Database

The 40 ingredients span:

| Category | Examples |
|---|---|
| Brightening | Kojic acid, Vitamin C (ascorbic acid), Azelaic acid, Niacinamide |
| Retinoids | Tretinoin, Retinol, Adapalene |
| Exfoliants | Glycolic acid, Lactic acid, Salicylic acid |
| Acne agents | Benzoyl peroxide, Clindamycin, Erythromycin |
| Moisturising | Hyaluronic acid, Ceramides, Urea |
| Antioxidants | Tocopherol, Ferulic acid, Resveratrol |
| Steroids | Hydrocortisone, Betamethasone, Clobetasol |
| Protective / Soothing | Zinc oxide, Allantoin, Bisabolol |

---

## Responsive Design

DermaComp is fully responsive across three breakpoints:

| Breakpoint | Layout changes |
|---|---|
| ≥ 1100 px | Full desktop: sidebar + multi-column formulary, full nav |
| 768–1100 px | Tablet: stacked sidebar, 2-column formulary, collapsed nav (hamburger) |
| < 768 px | Mobile: single-column everything, tab font scaling, action button stacking |

---

## Known Limitations & Roadmap

### Current limitations

- **Client-side auth only** — no multi-device sync; account data lost on localStorage clear
- **No printing** — PDF export shows an alert ("available in full build")
- **Offline-only** — compatibility checker uses hardcoded rules rather than a live database
- **Single file** — all formulary data is embedded; adding new formulas requires editing the source HTML

### Roadmap (proposed)

- Backend auth (Firebase / Supabase) for cross-device sync
- Full PDF export of calculation reports with pharmacopeial headers
- Expanded formulary (100+ formulas)
- Live drug-drug interaction API integration
- Barcode / QR label generation for compounded preparations
- Batch record PDF generation compliant with USP \<795\>

---

## Team

**Faculty of Pharmacy, Modern University for Technology and Information (MTI) — Team 1C**

| Role | Name | Contact |
|---|---|---|
| Research Supervisor | Dr. Rehab Hamed | [Rehab.hamid@pharm.mti.edu.eg](mailto:Rehab.hamid@pharm.mti.edu.eg) |
| Web Development | Dr. Aliaa Omar | [LinkedIn](https://www.linkedin.com/in/aliaashalabyy/) |
| Data Collection | Amani | amani.95604@pharm.mti.edu.eg |
| Data Collection | Aliaa | aliaa.95402@pharm.mti.edu.eg |
| Data Collection | Abdel | abdel.95058@pharm.mti.edu.eg |
| Data Collection | Ahmed | Ahmed.95134@pharm.mti.edu.eg |
| Data Collection | Amani | amani.94235@pharm.mti.edu.eg |
| Data Collection | Ahmed | ahmed.9430@pharm.mti.edu.eg |
| Data Collection | Ammal | ammal.94457@pharm.mti.edu.eg |
| Data Collection | Shorouk | shos20564@gmail.com |
| Data Collection | Afnan | afnan.95143@pharm.mti.edu.eg |
| Data Collection | Abadeer | abadeersefein010@gmail.com |

---

## License & Disclaimer

This project is a **graduation academic project** submitted to the Faculty of Pharmacy, MTI University.

**All formulas, calculations, and pharmacopeial references are provided for educational purposes only.** DermaComp is not a substitute for professional compounding judgement, a licensed pharmacist's review, or an officially validated compounding system. All calculations must be independently verified before any compounded preparation is dispensed to a patient.

The authors make no warranty of accuracy, completeness, or fitness for clinical use.

---

*Built with precision. Built for safety. Built by pharmacists, for pharmacists.*
