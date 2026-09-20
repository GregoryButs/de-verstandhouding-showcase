# Hyperframes Composition Brief: De Verstandhouding

## Objective
Create a short launch-style brag video for **De Verstandhouding**, het praktijk- en
afsprakenplatform voor een Belgische psychologenpraktijk.

## Output
- Composition directory: `brag-output/composition/`
- Rendered video: `brag-output/brag.mp4`
- Format: landscape — 1920x1080
- Duration: 21.0 seconden

## ⚠️ Hard constraint: geen echte patiënt- of medische gegevens
Dit is een zorgtoepassing. Elke UI in de video wordt **nagebouwd in HTML met verzonnen inhoud**.

- De ontwikkeldatabase (`Project/AfsprakenbeheerPsycholoog/Afsprakenbeheer.db`) wordt niet gelezen.
- Geen screenshots of `hyperframes capture` van de draaiende applicatie.
- Namen alleen als initialen: `M. V.`, `L. D.`, `K. B.` — verzonnen.
- Rijksregisternummer staat altijd volledig gemaskeerd op scherm: `••.••.••-•••.••`.
- Geboortedatum/telefoon/e-mail: gemaskeerd (`••/••/••••`) of weggelaten.
- **Consultatienotities, klachten en dossiertekst nooit leesbaar.** Waar het notitieveld in beeld
  komt, staat er ciphertext (`ENC:v2:9f3a…`) of `••••••••••`.
- Geen diagnose, geen aan een persoon gekoppelde prestatiecode, geen ELP-trajectteller per patiënt.
- Dossiernummers zijn zichtbaar fictief (`#0042`).

## Source Material
- Project root: `/home/gregory/project/AD-GregoryButs-2526`
- Primary files read:
  - `Project/AfsprakenbeheerPsycholoog/ClientApp/src/pages/LandingPage/sections/HeroSection.tsx`
  - `Project/AfsprakenbeheerPsycholoog/ClientApp/src/components/booking/WizardProgressBar.tsx`
  - `Project/AfsprakenbeheerPsycholoog/ClientApp/src/components/BookingWizard.tsx`
  - `Project/AfsprakenbeheerPsycholoog/ClientApp/tailwind.config.js`, `src/index.css`
  - `tests/BackendTests/BookingConcurrencyTests.cs`
  - `Project/AfsprakenbeheerPsycholoog/Services/Security/AesEncryptionService.cs`
  - `Project/.../Data/Migrations/20260902195621_VoegAppendOnlyTriggersToeOpAuditlogboek.cs`
  - `FullCoverageReport/Summary.txt`, `README.md`
- Product name: **De Verstandhouding**
- Tagline / strongest claim: vijftig gelijktijdige aanvragen op één tijdslot, precies één boeking
- Key UI moments to recreate: de landingspagina-hero, de vijfstaps boekingswizard met
  tijdslot-grid, een gemaskeerde dossierkaart
- Copy that must appear verbatim (uit de broncode):
  - `Individuele psychologische begeleiding gericht op psychologische flexibiliteit`
    (met `psychologische flexibiliteit` cursief en in `#cf7b7c`, precies zoals `HeroSection.tsx`)
  - `MAAK EEN AFSPRAAK` (CTA, uppercase, `letter-spacing: 0.2em`)
  - `Behandeling` · `Locatie` · `Datum` · `Details` · `Overzicht` (de vijf wizardlabels)

## Creative Direction
- Tone preset: **polished**
- Creative direction: "een zorgproduct dat zich gedraagt alsof er een dossier op het spel staat —
  stil aan de oppervlakte, streng eronder"
- Interpretation: lange holds, weinig beweging, geen grap. Eén harde cut in de hele video
  (scene 2 → 3). Type mag groot en licht met veel ruimte eromheen. Alles buiten die ene cut
  beweegt traag en beheerst.
- Angle: de rust van de voorkant is het resultaat van de strengheid van de achterkant. De video
  legt die twee lagen naast elkaar: een wachtkamer, een boeking, en dan wat er op dat ene
  klikmoment onder de motorkap gebeurt.
- Hook: de echte hero van de landingspagina, verbatim, in gebroken wit met één zalmroze accent.
- Outro / punchline: **"Rust aan de voorkant. Discipline aan de achterkant."**
- Avoid:
  - Generic SaaS language ("streamline", "empower", "seamless")
  - Abstracte filler: kleurwassen, deeltjes, zwevende bollen, equalizerbalken
  - Een visuele herontwerp van het merk — de huisstijl is gegeven, niet te verbeteren
  - Alarm- of foutgeluiden bij de 409-regels; het is geen incident, het is een systeem dat werkt

## Visual Identity
Exact uit `tailwind.config.js`, `src/index.css` en `HeroSection.tsx`:

- Background licht: `#faf7f2` (hero-sectie)
- Background donker: `#1d1d1b` (`brand.950`), `#22201e` (`stone.850`)
- Accent: `#DF8A8B` (CTA), `#cf7b7c` (hover / cursief accent), `#f3b5b4` (dark-variant)
- Tekst licht: `#1a2c30`; tekst donker: `#f5f5f4`
- Display font: **Bodoni Moda** (serif). De echte stack is `Apollo, Bodoni Moda, Georgia, serif`;
  Apollo is commercieel gelicentieerd en staat niet in de repo, dus Bodoni Moda is wat er in
  productie rendert en wat de video gebruikt. Een `@font-face` naar een lokaal bestand is vereist
  (lint: `font_family_without_font_face`) — zelf hosten in `assets/fonts/`.
- Body font: **Inter**. Echte stack `Akkurat, Inter, system-ui`; Akkurat idem niet aanwezig.
- Mono (cijfers, SQL): een zelf gehoste mono of een generieke `monospace` zonder naam.
- Rand-idioom: `border-radius: 0` overal, dunne stone-randen, minimale schaduw. Niets rondt af.
- Visual references: de vierkante CTA-knop met `0.2em` tracking, de vijf genummerde
  stappenbolletjes, de tijdslot-chips.

## Storyboard
Gebruik het storyboard in `brag-output/brag-plan.md` als creatief contract.

Scene summary:
1. **De wachtkamer** — 4.0s — hero verbatim, CTA-knop komt na een hold binnen
2. **De boeking** — 4.5s — vijfstaps balk vult, cursor klikt tijdslot `10:15`, slot valt dicht
3. **Vijftig tegelijk** — 4.0s — 49 regels `409` vallen weg, één `201` blijft; `1 · 49 · 0`
4. **Wat er niet uit komt** — 4.5s — gemaskeerde dossierkaart, `UPDATE Auditlogboek` → `ABORT`
5. **Rust aan de voorkant** — 4.0s — logo, drie cijferitems, slotregel

## Audio
- Audio role: warme, lage bed met sobere accenten
- Audio arc: zacht binnen → doelgericht in scene 2 → duikt weg voor de val in scene 3 → bijna
  stil onder de getypte SQL in scene 4 → fade-out naar stilte onder de slotregel
- Music: `happy-beats-business-moves-vol-12-by-ende-dot-app.mp3` (109,96 BPM, 117,4s)
- Music treatment: `data-start="0"`, basisniveau ≈0.32. Volume-automation lane:
  fade-in 0→0.32 over 0.8s, duck naar ≈0.18 rond 9.0–12.5s (scene 3), terug naar 0.30,
  dieper naar ≈0.14 rond 14.5–17.0s (de typende SQL), en fade-out naar 0 over de laatste 1.5s.
  Implementeer via `data-automation` met één `"target": "volume"` lane — `t` is seconden vanaf
  het **begin van de clip**, en de lane moet een expliciet punt op `t: 0` hebben.
- Music cue guidance: preset gelezen uit
  `<brag-skill>/assets/music/cues/happy-beats-business-moves-vol-12-by-ende-dot-app.music-cues.md`.
  Strong cues: 8.74s, 17.47s, 18.56s, 22.93s, 24.56s. Beat-grid ≈0.54s.
  **Lock maximaal twee**: het bevestigingsmoment in scene 2 op **8.74s**, en het logo in scene 5
  op **18.56s**. Markeer ze met `// beat-locked: 8.74s` / `// beat-locked: 18.56s`.
  Beat-grid: de vijf stappenbolletjes (non-tekst) mogen op elke beat vanaf ≈4.39s; de drie
  **leesbare** cijferitems in scene 5 snappen op elke **tweede** beat (≈1.08s uit elkaar),
  markeer `// beat-grid`.
- Audio-reactive treatment: **subtiel**. Extraheer per-frame data met
  `~/.claude/skills/hyperframes-creative/scripts/extract-audio-data.py` en koppel maximaal twee
  dingen: (a) de zachte gloed achter de CTA-knop in scene 1 (`boxShadow`-intensiteit, klein
  bereik), (b) de aanwezigheid van de dossierkaart in scene 4 (`scale` binnen ±2%). Sample per
  frame met de `tl.call()`-lus uit `hyperframes-creative/references/audio-reactive.md`.
  Geen waveforms, geen equalizerbalken, geen deeltjes, geen strobe, geen regenboog.
  Lukt de extractie niet (geen Python/ffmpeg), documenteer dat en render zonder — niet blokkeren.
- Audio-coupled moments:
  - Scene 1, ≈1.2s — CTA-knop verschijnt — één zeer zachte interface-cue
  - Scene 2, cursorklik op `10:15` — één korte klik-cue op exact hetzelfde frame
  - Scene 2, bevestiging — één ingehouden cue, **beat-locked 8.74s**
  - Scene 3, de val van 49 — **één** lage collectieve cue, geen 49 losse tikken
  - Scene 3, de regel die blijft — één helderdere, hogere cue
  - Scene 4, typende SQL — zachte toetsaanslagen, laag gemixt
  - Scene 4, `ABORT` — één droge afslag, als een deur die dichtvalt
  - Scene 5, logo — één zachte cue, **beat-locked 18.56s**. Daarna niets meer.
- SFX selection guidance: sparse — vier tot zes cues in de hele video. Kies pas ná de animatie,
  en laat sound en beweging op hetzelfde frame landen. Liever één cue te weinig dan één te veel.
- SFX analysis guidance:
  `/home/gregory/.claude/plugins/cache/brag/brag/0.2.2/skills/brag/assets/sfx/sfx-analysis.md`
  (+ `.json`). Kies bestanden met laag hoge-frequentie-risico — de toon is polished, niet scherp.
- Exact SFX choice: Hyperframes kiest bestandsnamen, tijdstempels, dichtheid en volume op basis
  van de daadwerkelijk geïmplementeerde animatie.
- Audio files: kopieer de gekozen muziek en SFX naar `brag-output/composition/assets/`.

## Hyperframes Instructions
Load the composition-building Hyperframes domain skills — `hyperframes-core` (composition contract
+ `data-*` timing), `hyperframes-animation` (motion), `hyperframes-creative` (design spec, beats,
audio-reactive), `hyperframes-keyframes` (seek-safe keyframes), `hyperframes-audio` (volume
automation / ducking) en `hyperframes-cli` (lint/check/render). `/brag` is its own workflow: do not
enter the `hyperframes` entry-point intent interview and do not route into its generic promo /
launch-video workflow. Prefer native Hyperframes conventions over anything in `/brag`.

Requirements:
- Show at least one real UI, copy, or visual element from the source project — de hero en de
  vijf wizardlabels staan verbatim in de video.
- **Geen enkel echt patiënt- of medisch gegeven.** Zie de hard constraint bovenaan.
- Keep all text readable: korte regel ≥0.8s settled, volzin ≥0.3s per woord (min. 1.2s).
  De hero-kop is negen woorden → ≥2.7s volledig zichtbaar.
- Keep the video within 15-25 seconds (doel: 21.0s).
- Include the planned music/SFX layer.
- Treat `/brag` audio notes as guidance, not a fixed cue sheet. Choose SFX after the visual
  animation exists.
- Treat music cue metadata as optional timing hints. Maximaal twee strong-cue locks.
  Leesbaarheid en scene-pacing winnen van een cue.
- Honor the music treatment: fade-in, twee ducks, fade-out onder de slotregel.
- Use local assets for audio, fonts and any runtime dependency.
- Run `npx hyperframes check` before render — it is brag's single gate. Lint-errors schakelen de
  layout- en contrastaudits uit, dus een schone `check` met `0 samples` betekent niets.
- Let op de lint-valkuilen: geen CSS-`transform` op een node die GSAP daarna op dezelfde
  property tweent (gebruik `fromTo`), geen `autoAlpha`/`visibility` op een `.clip`, elke
  `<audio>` heeft een `id`, elke benoemde `font-family` heeft een in-file `@font-face` naar een
  lokaal bestand, geen `crossorigin` op media, geen `repeat: -1`.
