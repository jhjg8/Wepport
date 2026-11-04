# Portfolio Overhaul Plan — `phuriwat_portfolio.html`

> [!NOTE]
> **Plan only — no files have been modified.** Everything below comes from reading `skill.md`, `skill (1).md`, every `Description.txt` / `GameDescription.txt` / `Plan.txt`, the current HTML, and looking at all 38 project images plus the decoration folder.

---

## 0. What I found (inspection summary)

### Skill files
There are **two** skill files: `skill.md` (v1.0) and `skill (1).md` (v1.1, which includes everything in v1.0). I'll follow **v1.1**. It was written for *data-presentation sites* built with React, Tailwind and Framer Motion. That clashes with your rules: one HTML file, no unnecessary dependencies. So I'll **keep its design and interaction rules but build everything in plain HTML/CSS/JS** (details in §5).

### Folder inventory

| Folder | Description says | Images (what they actually show) | Link |
|---|---|---|---|
| `Game/BlackFlash` | Movement-based, fast | `(12)` red/black stylized menu "BLACK FLASH 黒閃" · `(11)` tentacle enemy in a checkered corridor, editor view · `(10)` first-person shot with camera/film · `(9)` "STYLE +675" capture HUD · `AllForOneCer.jpg` = All For One University, Hamster Hub, 22–25 Oct 2026 | **new:** phuriw.itch.io/blackflash |
| `Game/MEOW_LOSTONSHIP` | 2D singleplayer | `(6)` cockpit, fiery asteroid field · `(7)` chaotic hit-effects gameplay · `(5)` "You're so HOT!" restart screen · `(4)` Unity editor with hand-drawn menu · `LostShipGameJamCer.png` = **Finalist, Hamster Hub GameJam X, 26–28 Apr 2026** (4 MB) | **new:** kolobit.itch.io/meowlostship |
| `Game/Sentai Minus 1` | Multiplayer, parkour, action | `SentaiMinus2` gameplay (robot in a low-poly city, L-ARM/R-ARM/L-LEG/R-LEG HUD, "physics-based robot brawler… each player controls one limb") · `SentaiMenu` title screen with katakana · `SentaiMainus1` city overview (has a Snipping-Tool toast in the corner) · `SentaiMinus1` full Unity 6 editor | yelmee.itch.io/sentaiminus1 (kept) |
| `Game/SrongNam` | 3D third-person, inspired by Songkran: you play as water, splashing people to spread happiness | `(8)` bright beach menu with a slime in sunglasses · `(13)` sunset beach gameplay · `(14)` costume/wardrobe screen · `(15)` itch jam results page (Creativity #80, Overall #109; team LuckyNakroth, chatchanok, Phuriw, yelmee, Noxer007) · `(16)` blurry editor capture | luckynakroth.itch.io/srongnam (kept) |
| `Game/Divine Deck` | Deck builder, card game, roguelike | `RnJam1` key art (hooded player vs. crowned card demon in a tavern) · `RnJam` sunny title screen · `RnJam0` gameplay (parchment cards, Attack/Defend) · `Screenshot…205638` 3D tavern card shop in the editor · `RainyJamCer.png` = RainyGameJam | seeiwdum.itch.io/divine-deck (kept) |
| `Game/LastWitness` | Puzzle, detective | `(17)` subway title screen · `(18)` tall portrait: detective in yellow trench coat behind bars · `(19)` sunset-lit bedroom crime scene · `(20)` Thai suspect dossier card UI · `Global game jam 2026Cer.jpg` | ace-of-spades2566.itch.io/last-witness (kept) |
| `Game/GhostSimulator` | Platformer, simulation, quirky indie | `(22)` possessed object with QWEASD key prompts and the "Money loss / Score" HUD · `(21)` editor (TV prop, NetworkObject) · `(23)` grey prototype block · `image0.jpg` = CAMT Digital Contest 2026 Game Design Contest, 8 Aug 2569 | "Under development" → **no link**, shows an *In development* badge |
| `Game/Sword` | Turn-based | `sswt1` painted blue forest battle (party vs. purple beasts) · `sswt0` title screen **"Sword Sharpened With Tear"** · `Game DEV tournament.png` = Game Dev Tournament, 19–28 Dec 2025 | phuriw.itch.io/sword (kept) |
| `Activity/Assets` | Turn-Based Template for beginners: Partial classes, 3 variants (unit position, status effects, simple), combinable; used for real in a TA event. *"Save a spot for certificate"* | `(24)` editor: unit cards plus combat-unit inspector · `(25)` prototype with "Timeline Order" and Current Unit | — |
| `Activity/Ta` | TA at Roblox Boot Camp, Sci Game, AI Kick Starter 1 & 2; helped learners with duplicate AI classes and Input Package setup. *"NO IMAGE YET"* | none | — |
| `Decoration image` | "Use for background decoration if you want" | Tech logos (C#, ISO C++, Visual Studio, Claude, CAMT, CMU) **and** fan art of third-party characters (Limbus Company: Yi Sang, Hong Lu, Don Quixote, Rodion, Sinclair, Heathcliff, Dante; Helluva Boss: Loona, Stolas; plus `roman-…png`) | — |

Two existing entries have **no folder**: *C Language training (CMU Science)* and *CAMT Summer Course*. I'll keep their current text and give them CSS fallback art.

---

## 1. Filters → All / Game / Activity

Each entry gets **exactly one** category (`data-category="game"` or `"activity"`). "All" shows everything, so nothing can be left out.

| Game (8) | Activity (4) |
|---|---|
| Black Flash · MEOW_LOSTSHIP · Sentai Minus 1 · SrongNam · Divine Deck · Last Witness · Ghost Simulator · Sword | Turn-Based Template (Event Assets) · Teaching Assistant @ Hamster Hub · C Language Training (CMU Science) · CAMT Summer Course |

- The 4 activities move out of the "Beyond Projects" list and into the filterable grid.
- Buttons show live counts: `All 12 · Game 8 · Activity 4`. They also get `aria-pressed`, and switching filters uses a fade/scale animation (transform/opacity only).
- **Guard:** a small JS check counts the cards in each category at load time and logs a console warning if any card has no category or an unknown one.

---

## 2. Assets: optimized copies (originals untouched)

Many source files are heavy (Sentai 0.9–1.2 MB, Sword 1.7–2.0 MB, MEOW certificate 4 MB). They also have Thai names with spaces (`ฉันเอง (10).png`), which break easily on web hosts. My plan:

- Create **`d:\Wepport\assets\`** with **resized, ASCII-named copies** using a PowerShell/System.Drawing script saved in `scratch/`. Example: `assets/blackflash/menu.jpg`, `assets/sentai/gameplay.jpg`.
  - Thumbnails ≈ 800 px wide, gallery/banner ≈ 1600 px, JPEG q≈85. Images that need transparency or crisp UI stay PNG.
- **Original folders are never modified, renamed or deleted.**
- Every `<img>` gets `width`/`height` (no layout shift), `loading="lazy"`, `decoding="async"`, `object-fit: cover` inside `aspect-ratio` boxes, and a per-image `object-position` where a crop needs it (e.g. hiding the Snipping-Tool toast).

### Image → entry mapping (no image used outside its own project)

| Entry | Card thumbnail | Detail gallery | Certificate |
|---|---|---|---|
| Black Flash | `(12)` menu | `(11)`, `(10)`, `(9)` | AllForOneCer |
| MEOW_LOSTSHIP | `(6)` asteroid cockpit | `(7)`, `(5)`, `(4)` | LostShipGameJamCer |
| Sentai Minus 1 | `SentaiMinus2` | `SentaiMenu`, `SentaiMainus1` (cropped), `SentaiMinus1` (labelled "in-engine") | — |
| SrongNam | `(8)` beach menu | `(13)`, `(14)`, `(15)` (jam results) — skip blurry `(16)` | — |
| Divine Deck | `RnJam1` key art | `RnJam`, `RnJam0`, `Screenshot…205638` | RainyJamCer |
| Last Witness | `(17)` subway | `(18)` (tall slot), `(19)`, `(20)` | Global game jam 2026Cer |
| Ghost Simulator | `(22)` | `(21)`, `(23)` | image0.jpg (CAMT) |
| Sword | `sswt1` battle | `sswt0` title | Game DEV tournament |
| Turn-Based Template | `(24)` | `(25)` | **"Certificate coming soon" placeholder slot** (per description) |
| TA / C Training / CAMT Summer | CSS fallback art (chat bubbles + bug icons / `printf` terminal / top-down grid) | — | — |

---

## 3. Visual design direction

**Overall vibe: a "player profile / game launcher" personal site.** I'll keep the existing dark base and lime brand color and add game-UI touches: a HUD-style nav, a "Press Start" hero, XP-bar style skill meters, a level-select project grid, and a certificate "trophy wall". It should feel playful and expressive, not corporate.

### Per-project themes (each card gets a `data-theme`, which sets CSS custom properties)

| Project | Palette (taken from the artwork) | Decoration |
|---|---|---|
| Black Flash | crimson `#d8203a` / ink black / white, teal tentacle accent | diagonal slashes, halftone dots, slanted label chip (like its menu) |
| MEOW_LOSTSHIP | fire orange `#ff6a1f` / deep space navy | starfield, hand-drawn flame scribble, "You're so HOT!" handwritten accent |
| Sentai Minus 1 | tokusatsu red / yellow / green / navy | speed lines, katakana `センタイ マイナス ワン`, 4-limb HUD chips |
| SrongNam | aqua `#2ec4e6` / sand / sunset coral | wavy water border, splash bubbles on hover |
| Divine Deck | tavern brown / candle gold / demon red | card-frame border, slight card-tilt on hover, suit icons ♠♥♦♣ |
| Last Witness | noir black / amber `#f2a516` | film grain, case-file tag, magnifier cursor ring on hover |
| Ghost Simulator | ghost purple `#7a2a8c` / prompt green | gentle floating wobble, QWEASD key-cap chips |
| Sword | watercolor blue `#0f4c75` / steel | brush-stroke edge, blade-glint sweep on hover |
| Activities | blueprint grid / lime | class-diagram line art, "quest log" styling |

### Site-wide improvements
- **Hero:** keep the "From player to creator." headline and copy. Add a scrolling marquee of real game thumbnails behind the hero card, and count-up metrics.
- **Story / Skills / Education / Goals:** content kept and lightly tightened. Skills cards get real tech logos (C#, C++, Visual Studio, Claude) from the decoration folder. Education shows the CAMT and CMU logos.
- **New "Journey" timeline**, built only from dates printed on the certificates: Game Dev Tournament (Dec 2025) → Global Game Jam 2026 → GameJam X Finalist (Apr 2026) → CAMT Digital Contest (Aug 2026) → RainyGameJam → All For One University (Oct 2026). Entries without a printed date show no date.
- **Project detail modal** (upgrades the existing unused modal): banner, gallery with thumbnails and keyboard arrows, role / what I built / tools / genre (from `GameDescription.txt`), certificate viewer, play link. Closes with Esc, backdrop click or ×; focus is trapped and restored on close.
- **Typography:** Kanit (Thai body) + IBM Plex Mono (HUD labels), both already loaded. I'll add **one** display font for headings. Skill rule: body 1.125rem / 1.7 line-height.

---

## 4. Content edits (no invented facts)

- Keep all existing text; shorten card blurbs to about 2 lines. The full text moves into the modal.
- Additions, each backed by the folder materials:
  - Black Flash and MEOW links
  - Sword full title "Sword Sharpened With Tear"
  - Sentai's "each player controls one limb" (from its tutorial text)
  - SrongNam's Songkran premise and jam ranks (Creativity #80)
  - Event names and dates from the certificates
  - Genre tags from each `GameDescription.txt`
  - Ghost Simulator marked *In development*
- I won't add any responsibility, award or feature that isn't in the HTML, a description or an image.

---

## 5. How `skill.md` applies (vanilla implementation)

| Skill rule | How I'll do it |
|---|---|
| Spotlight cards following the cursor | `--mouse-x/y` set on `pointermove` → `radial-gradient` |
| Magnetic buttons, tap feedback, ripple | Small JS helper; `:active` scale 0.96 |
| Staggered scroll-in animations | `IntersectionObserver` + CSS classes |
| Scroll progress bar | Thin gradient bar at the top |
| Click-to-expand details | Modal with a transform/opacity morph |
| 60 fps: animate only transform/opacity; zero CLS | Followed; every media box uses `aspect-ratio` |
| WCAG AA contrast; mobile tap instead of hover | Text over images sits on a gradient scrim; hover effects wrapped in `@media (hover:hover)` |
| Separate data from markup | Cards stay as **static HTML** (visible even without JS); gallery and certificate details live in one `PROJECT_DETAILS` JS object |
| *Not adopted:* React/Next, Tailwind, Framer Motion, charts, CSV export, dark-mode toggle | Conflicts with single-file / no-dependency rules, or doesn't fit a portfolio (the site is dark by default) |

Also: `prefers-reduced-motion` turns animations off. Breakpoints at about 1024 / 800 / 560 px; the grid goes 3 → 2 → 1 columns.

---

## 6. Verification plan

1. A script parses every `src`/`href` in the HTML and confirms each local file exists (no broken paths).
2. Serve the folder with `python -m http.server`, then take headless Edge screenshots at 1440, 820 and 390 px widths and review them.
3. Test filters: All = 12, Game = 8, Activity = 4. The load-time guard logs to the console; I'll check for zero warnings and errors.
4. Confirm all 7 external itch links and all in-page nav anchors resolve.
5. Final summary listing integrated entries, assets used, design changes and anything skipped.

---

## ❓ Decisions needed before I start

1. **Image optimization:** OK to create a new `assets/` folder with resized, ASCII-named *copies* (originals untouched)? *(Recommended.)* The alternative is linking the original Thai-named full-size files directly.
2. **Fan-art characters in `Decoration image`** (Limbus Company / Helluva Boss): these are third-party copyrighted characters, and this looks like a university-admission portfolio. My recommendation is to use **only the tech and university logos**. Alternatives: a few small character "stickers" as background accents, or use them freely.
3. **Game-jam games under Activity too?** I recommend **Game only**: the competitions still show through certificates, badges and the Journey timeline, without duplicate cards.
4. **Naming:** keep the display name **MEOW_LOSTSHIP** (current HTML and itch URL) rather than the folder's "MEOW_LOSTONSHIP"? And show Sword as **"Sword Sharpened With Tear"**, with "Sword" as a subtitle?
