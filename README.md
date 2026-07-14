# 🕹️ Gamified Registration Form
### *An immersive, retro-gaming registration page that turns standard form validation into an 80s arcade experience.*

---

> **"Insert Coin to Register"**
> A single-file web application that wraps a functional user registration form inside a fully styled cyberpunk arcade cabinet — complete with CRT scanlines, neon glows, pixel glitch transitions, and arcade-themed vocabulary.

---

## 📋 Table of Contents

1. [Project Description](#-project-description)
2. [Feature List](#-feature-list)
3. [Architecture Overview](#-architecture-overview)
4. [File Structure](#-file-structure)
5. [APIs & Services Used](#-apis--services-used)
6. [Setup Guide](#-setup-guide)
7. [Demo Flow](#-demo-flow)
8. [Form Validation Rules](#-form-validation-rules)
9. [Fallback Explanation](#-fallback-explanation)
10. [Known Limitations](#-known-limitations)
11. [Author](#-author)

---

## 📖 Project Description

The **Gamified Registration Form** is a **Web Technologies lab project** that reimagines a standard HTML registration form as an **80s arcade machine interface**. Instead of a plain white form, users are greeted with:

- A glowing magenta arcade cabinet container
- CRT scanline background effect
- Retro pixel and futuristic Orbitron fonts
- Arcade-themed field labels (*Player Name, Comms Link, Security Cipher*)
- A **pixel glitch screen wipe** animation on successful submission
- A **Player Profile Card** reveal after registration

The project demonstrates core web fundamentals: **HTML5 structure**, **Vanilla CSS** (including gradients, shadows, and animations), and **JavaScript** (DOM manipulation, object constructors, jQuery animations, and regex validation) — all within a single self-contained `.html` file.

---

## ✨ Feature List

| # | Feature | Description |
|---|---------|-------------|
| 1 | 🎨 **CRT Scanline Background** | Layered `linear-gradient` overlays simulate an old cathode-ray tube monitor effect |
| 2 | 🌟 **Neon Glow UI** | Box shadows and text shadows in magenta/fuchsia on all interactive elements |
| 3 | 🔤 **Dual Retro Fonts** | `Orbitron` for headings/inputs (futuristic), `VT323` for labels/subtitles (pixel terminal) |
| 4 | 🎮 **Arcade-Themed Language** | All form labels use in-universe vocabulary: *Player Name, Comms Link, Security Cipher, Gameplay Mode* |
| 5 | 📋 **Dynamic Dropdown** | `<select>` options are injected via JavaScript loop — not hardcoded in HTML |
| 6 | ✅ **5-Layer Form Validation** | Sequential validation with distinct, thematic error messages |
| 7 | ⚠️ **Animated Error Box** | Dashed-border error panel slides down with jQuery `slideDown()` |
| 8 | 💥 **Pixel Glitch Transition** | 1,600-block grid animation fires on successful submit, wiping the screen |
| 9 | 🃏 **Player Profile Card** | Post-registration screen reveals a styled data card with submitted user info |
| 10 | 🔄 **Reboot Terminal Button** | Reloads the page to simulate restarting the arcade machine |
| 11 | 📦 **Zero Dependencies (runtime)** | No backend, no build tools — opens directly in any browser |

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                  BROWSER (Client-Side Only)                 │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐   │
│  │               index: .html file                      │   │
│  │                                                      │   │
│  │   ┌────────────┐  ┌──────────────┐  ┌────────────┐  │   │
│  │   │  HTML5     │  │  CSS (embed) │  │  JS (embed)│  │   │
│  │   │  Structure │  │              │  │            │  │   │
│  │   │            │  │ • Reset      │  │ • jQuery   │  │   │
│  │   │ • Form     │  │ • Body/BG    │  │   DOM ops  │  │   │
│  │   │ • Overlay  │  │ • Cabinet    │  │ • PlayerP  │  │   │
│  │   │ • Success  │  │ • Inputs     │  │   rofile   │  │   │
│  │   │   Screen   │  │ • Buttons    │  │   Object   │  │   │
│  │   │            │  │ • Pixel Grid │  │ • Glitch   │  │   │
│  │   │            │  │ • Profile    │  │   Animation│  │   │
│  │   │            │  │   Card       │  │ • Validator│  │   │
│  │   └────────────┘  └──────────────┘  └────────────┘  │   │
│  └──────────────────────────────────────────────────────┘   │
│                                                             │
│       External CDN Calls (requires internet):               │
│       ┌─────────────────┐   ┌──────────────────────┐        │
│       │  Google Fonts   │   │  jQuery 3.6.0 CDN    │        │
│       │  Orbitron+VT323 │   │  (code.jquery.com)   │        │
│       └─────────────────┘   └──────────────────────┘        │
└─────────────────────────────────────────────────────────────┘
```

### Component Breakdown

#### 1. View Layer (HTML)
Three mutually exclusive panels inside `#arcade-cabinet`:
- **`#form-wrapper`** — The active registration form (visible on load)
- **`#pixel-overlay`** — Hidden absolutely-positioned grid, activated during transition
- **`#success-screen`** — Hidden panel, revealed post-validation

#### 2. Style Layer (CSS — embedded `<style>`)
| Selector | Role |
|---|---|
| `body` | CRT scanline effect via layered `linear-gradient` + `error_bg.png` |
| `#arcade-cabinet` | Main container with dual box-shadow (inner + outer glow) |
| `input:focus`, `select:focus` | Magenta glow on active fields |
| `#pixel-overlay` / `.pixel-block` | 40×40 CSS Grid for glitch effect |
| `.profile-card` / `.profile-line` | Post-success data display card |

#### 3. Logic Layer (JavaScript — embedded `<script>`, jQuery)
| Function / Block | Role |
|---|---|
| `$(document).ready()` | Entry point — bootstraps all logic after DOM loads |
| `while` loop over `availableModes[]` | Dynamically populates `<select>` options |
| `PlayerProfile(n, e, m)` constructor | OOP object storing player data + `renderCard()` method |
| `runGlitchRedraw(callback)` | Creates 1,600 pixel blocks, animates them, calls `callback` at midpoint |
| `$('#reg-form').on('submit')` | Intercepts form submit, runs validation chain, dispatches success/error |

---

## 📁 File Structure

```
Web-Tech Proj/
│
├── Gamified Rejistration Form.html     ← Main application (entire app lives here)
├── error_bg.png                        ← Background texture (CRT noise/static image)
├── Gamified Rejistration Form
│   Presentation.pptx                  ← Project presentation slides
├── Web Proj Report.pdf                 ← Formal project documentation/report
└── README.md                           ← This file
```

> **Note:** The entire application — HTML structure, CSS styles, and JavaScript logic — is self-contained within the single `.html` file. No separate stylesheet or script file is needed.

---

## 🌐 APIs & Services Used

| Service | URL | Purpose | Required? |
|---|---|---|---|
| **Google Fonts** | `fonts.googleapis.com` | Loads `Orbitron` and `VT323` typefaces | ⚠️ Internet required |
| **jQuery 3.6.0** | `code.jquery.com/jquery-3.6.0.min.js` | DOM manipulation, event handling, `.animate()`, `.slideDown()`, `.slideUp()` | ⚠️ Internet required |

> **No backend API calls are made.** The form does not submit data to any server. All processing is purely client-side in the browser.

---

## 🛠️ Setup Guide

### Prerequisites
- A modern web browser (Chrome, Firefox, Edge, Safari)
- An internet connection *(for Google Fonts + jQuery CDN)*
- No Node.js, no npm, no build step required

### Steps

**Option A — Direct Open (Simplest)**
```
1. Navigate to the project folder:
   Web-Tech Proj/

2. Double-click:
   Gamified Rejistration Form.html

3. The file opens in your default browser. Done.
```

**Option B — Via VS Code Live Server**
```
1. Open the project folder in VS Code:
   File → Open Folder → Web-Tech Proj/

2. Install the "Live Server" extension (if not already installed)

3. Right-click "Gamified Rejistration Form.html"
   → Select "Open with Live Server"

4. Browser auto-opens at: http://127.0.0.1:5500/
```

**Option C — Via Python Local Server**
```bash
# Navigate to the folder in terminal
cd "C:\Users\<YourName>\OneDrive\Desktop\Web-Tech Proj"

# Python 3
python -m http.server 8080

# Open browser at:
http://localhost:8080/Gamified%20Rejistration%20Form.html
```

---

## 🎬 Demo Flow

```
┌─────────────────────────────────────────────────────┐
│  STEP 1: Page Load                                  │
│  • CRT scanline background renders                  │
│  • Arcade cabinet glows magenta                     │
│  • "SYSTEM INIT..." subtitle displayed              │
│  • Dropdown auto-populated via JS loop              │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│  STEP 2: User Fills the Form                        │
│  • Player Name  → e.g., "NightRaider"               │
│  • Comms Link   → e.g., "night@arcade.com"          │
│  • Security Cipher → e.g., "Cipher99!"              │
│  • Confirm Cipher  → same as above                  │
│  • Gameplay Mode → "Competitive"                    │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│  STEP 3a: Invalid Input                             │
│  • Red dashed error box slides DOWN                 │
│  • Error message in retro terminal font:            │
│    e.g., "CIPHER MISMATCH DETECTED."                │
│  • User corrects input and retries                  │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│  STEP 3b: Valid Input → Clicks "EXECUTE"            │
│  • Error box slides UP (hides)                      │
│  • PlayerProfile object created in memory           │
│  • runGlitchRedraw() triggers                       │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│  STEP 4: Pixel Glitch Animation                     │
│  • 1,600 pixel blocks flood the screen              │
│  • Random magenta/purple/pink flashes               │
│  • Screen wipe completes in ~400ms                  │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│  STEP 5: Success Screen Revealed                    │
│  • "OVERRIDE SUCCESS" header                        │
│  • "USER DATA LOGGED" subtitle                      │
│  • Profile card displays:                           │
│      ID:   NightRaider                              │
│      LINK: night@arcade.com                         │
│      MODE: COMPETITIVE                              │
│  • "REBOOT TERMINAL" button → reloads page          │
└─────────────────────────────────────────────────────┘
```

---

## 🔐 Form Validation Rules

Validation runs **sequentially** — the first failing rule blocks submission and displays its error.

| Order | Rule | Error Message |
|---|---|---|
| 1 | All fields must be non-empty | `ALL FIELDS MUST BE POPULATED.` |
| 2 | Username must not contain spaces | `NAME CANNOT CONTAIN BLANK SPACES.` |
| 3 | Email must match pattern `x@x.x` | `COMM LINK ESTABLISHMENT FAILED. INVALID FORMAT.` |
| 4 | Password must be ≥ 8 characters | `CIPHER MUST BE AT LEAST 8 CHARACTERS.` |
| 5 | Password and confirm must match | `CIPHER MISMATCH DETECTED.` |

---

## 🛡️ Fallback Explanation

Since the project relies on two **external CDN resources**, here is what happens if they are unavailable:

### 1. Google Fonts (`Orbitron` + `VT323`) — Unavailable
- **Effect:** The browser falls back to `sans-serif` (Orbitron) and `monospace` (VT323) — the system's default fonts
- **Impact:** Visual aesthetic degrades — text will no longer look retro/futuristic, but the form remains **fully functional**
- **Fallback defined in CSS:** `font-family: 'Orbitron', sans-serif` and `font-family: 'VT323', monospace`

### 2. jQuery 3.6.0 CDN — Unavailable
- **Effect:** `$` is undefined → **all JavaScript logic fails silently**
- **Impact:** The dropdown will not populate, form submission will not be intercepted, validation will not run, and the glitch animation will not fire. The raw HTML form may still render but will be non-functional as intended.
- **Workaround (offline use):** Download jQuery locally and replace the CDN link:
  ```html
  <!-- Replace this: -->
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

  <!-- With this (after saving jquery-3.6.0.min.js to the project folder): -->
  <script src="jquery-3.6.0.min.js"></script>
  ```

> ✅ **Best practice for offline resilience:** Download both `jquery-3.6.0.min.js` and self-host the fonts using `@font-face` declarations pointing to locally saved `.woff2` files.

---

## ⚠️ Known Limitations

- **No data persistence** — submitted registration data is not saved anywhere (no localStorage, no backend)
- **No real email validation** — the regex checks format only, not whether the email actually exists
- **Not mobile-responsive** — the cabinet is fixed at `480px` width; no media queries implemented
- **Typo in filename** — "Rejistration" is a misspelling of "Registration" (original filename preserved for project continuity)
- **No accessibility (a11y)** — missing ARIA labels, focus management, and screen reader support

---

## 👩‍💻 Author

**NeuraHals** — © 2026 Gamified Portal 
Web Technologies — Theory Project

*Building immersive digital experiences, one pixel at a time.*

---

<div align="center">

```text
 ██╗     ███████╗██╗   ██╗███████╗██╗          ██╗   ██╗██████╗ 
 ██║     ██╔════╝██║   ██║██╔════╝██║          ██║   ██║██╔══██╗
 ██║     █████╗  ██║   ██║█████╗  ██║          ██║   ██║██████╔╝
 ██║     ██╔══╝  ╚██╗ ██╔╝██╔══╝  ██║          ██║   ██║██╔═══╝ 
 ███████╗███████╗ ╚████╔╝ ███████╗███████╗     ╚██████╔╝██║     
 ╚══════╝╚══════╝  ╚═══╝  ╚══════╝╚══════╝      ╚═════╝ ╚═╝
```

*INSERT COIN TO CONTINUE*

</div>
