# Brag Plan: De Verstandhouding

## What is this app?
Een praktijkplatform voor een Belgische psychologenpraktijk: patiënten boeken zelf een consultatie
via een vijfstaps wizard, de psycholoog beheert agenda, dossiers en de RIZIV/ELP-maandafsluiting —
op versleutelde dossiervelden en een auditlogboek dat de database zelf weigert te wijzigen.

## The angle
De voorkant is opzettelijk stil: Japandi, gebroken wit, een serif kop met één zacht zalmroze accent.
Die rust is geen decoratie — ze is het resultaat van wat eronder is vastgezet. Eén tijdslot, vijftig
gelijktijdige aanvragen, precies één boeking. Elk gevoelig veld versleuteld. Een auditregel die niet
terug te nemen is. De video legt die twee lagen naast elkaar: **rust aan de voorkant, discipline
aan de achterkant.** Dat is specifiek voor dit project en voor geen enkel ander.

## ⚠️ Anonimiseringsregel (hard, geldt voor elke scene)
Dit is een zorgtoepassing. In de video verschijnt **geen enkel echt patiënt- of medisch gegeven**.

- De echte ontwikkeldatabase (`Afsprakenbeheer.db`) wordt **niet** gelezen, gequeryd of gerenderd.
- Alle namen zijn fictief en gereduceerd tot initialen: `M. V.`, `L. D.`, `K. B.`
- Rijksregisternummer op scherm is altijd volledig gemaskeerd: `••.••.••-•••.••`
- Dossiernummers zijn zichtbaar fictief: `#0042`, `#0043`, `#0044`
- Geboortedata, telefoonnummers en e-mailadressen worden gemaskeerd (`••/••/••••`) of weggelaten.
- **Consultatienotities, klachten en vrije tekst uit het dossier komen niet in beeld.** Waar het
  notitieveld getoond wordt, staat er ciphertext (`ENC:v2:…`) of `••••••••••`, nooit leesbare inhoud.
- Diagnoses, prestatiecodes gekoppeld aan een persoon, en ELP-trajecttellers per patiënt worden
  alleen als anonieme rij getoond (initialen + gemaskeerd rijksregisternummer), nooit herleidbaar.
- Screenshots of captures van de draaiende applicatie worden **niet** gebruikt; elke UI in de video
  wordt nagebouwd in HTML met verzonnen, gemaskeerde inhoud.

## Hook (first 2-3 seconds)
De echte landingspagina-hero, verbatim en in de echte huisstijl: gebroken wit `#faf7f2`, het
Bodoni-serif kopje met het cursieve zalmroze accent op *psychologische flexibiliteit*, en de echte
CTA-knop `MAAK EEN AFSPRAAK` in `#DF8A8B` met uppercase tracking. Geen beweging behalve een zachte
settle. Het beeld moet voelen als een wachtkamer, niet als een dashboard — juist dat maakt de cut
naar scene 3 hard.

## Key moments (the middle)
- De vijfstaps voortgangsbalk met de echte labels (Behandeling · Locatie · Datum · Details ·
  Overzicht) die stap voor stap invult, en een cursor die één tijdslot in het weekrooster kiest.
- Vijftig gelijktijdige aanvragen op hetzelfde tijdslot: 49 regels vallen grijs weg met `409`,
  één regel blijft staan in zalmroze met `201`. Geverifieerd in `BookingConcurrencyTests`.
- De dossierkaart waarin de gevoelige velden ter plekke dichtvallen naar `••.••.••-•••.••` en
  `ENC:v2:…`, gevolgd door een `UPDATE Auditlogboek` die stukloopt op `ABORT`.

## Outro / punchline
Het logo, een korte cijferregel die klopt, en de slotzin:
**Rust aan de voorkant. Discipline aan de achterkant.**

## User flow worth showing
Entry → key action → result, uit de echte wizard (`BookingWizard.tsx` + `useBookingWizard`):
1. Patiënt kiest een behandeling en een locatie (Praktijk / Google Meet / Telefoon).
2. Patiënt kiest een tijdslot in het weekrooster (stap 3, `Step3DateTimeSelection`).
3. Bevestiging: de afspraak staat vast en de agenda schuift dicht op dat slot.
Scene 2 is die flow. Scene 3 laat zien wat er op dat ene klikmoment onder de motorkap gebeurt.

## Tone
- Preset: **polished**
- Creative direction: "een zorgproduct dat zich gedraagt alsof er een dossier op het spel staat —
  stil aan de oppervlakte, streng eronder"
- Interpretation: lange holds, weinig scenes, geen grap. Type mag groot en licht zijn met ruimte
  eromheen. De enige energie in de video zit in één cut (scene 2 → 3) en in de 49 regels die
  wegvallen. Alles daarbuiten beweegt traag en beheerst. Vijf scenes in plaats van de gebruikelijke
  drie à vier, omdat de video zowel de flow als de payoff moet dragen; de holds blijven lang.

## Format: landscape — 1920x1080
## Duration: 23.0 seconden (definitief; in de compositie verlengd t.o.v. de eerste raming van 21.0s
zodat de harde cut op de strong cue 8.74s valt en de slotregel 2,25s stil op scherm blijft)

## Visual identity (from the project)
Bron: `ClientApp/tailwind.config.js`, `ClientApp/src/index.css`, `sections/HeroSection.tsx`.

- Achtergrond (licht): `#faf7f2` — de hero-sectie van de landingspagina
- Achtergrond (donker, scene 3/4): `#1d1d1b` (`brand.950`) / `#22201e` (`stone.850`)
- Accent: `#DF8A8B` (CTA), hover `#cf7b7c`, dark-variant `#f3b5b4`
- Tekst: `#1a2c30` op licht, stone-100 op donker
- Display font: Bodoni Moda (serif) — de echte stack is `Apollo, Bodoni Moda, Georgia, serif`;
  Apollo is commercieel gelicentieerd en niet in de repo, dus Bodoni Moda is de renderende keuze
- Body font: Inter — echte stack `Akkurat, Inter, system-ui`; Akkurat is niet gelicentieerd aanwezig
- Rand-idioom: `rounded-none`, dunne stone-randen, `shadow-xs`. Niets rondt af, niets zweeft.
- Sterkste visuele element: de CTA-knop in `#DF8A8B`, uppercase, `tracking-[0.2em]`, vierkante hoeken

## Share copy (draft)
De Verstandhouding: praktijkplatform voor een psychologenpraktijk. Vijftig gelijktijdige aanvragen
op hetzelfde tijdslot — precies één komt erdoor. Dossiervelden AES-256-GCM versleuteld, een
auditlogboek dat de database zelf weigert te wijzigen. .NET 10 · React 18 · 94,1% lijndekking.

## Audio direction
- Role: warme, lage bed met sobere accenten — de muziek draagt, ze duwt niet
- Music: `happy-beats-business-moves-vol-12-by-ende-dot-app.mp3` (109,96 BPM, 117,4s) — de rustigste
  van de vijf gebundelde tracks en lang genoeg voor de volledige video
- Music treatment: start op 0.0s, laag gemixt (≈0.30–0.35), korte fade-in over de eerste 0.8s,
  merkbaar dieper (duck naar ≈0.18) tijdens scene 3 zodat de 49 wegvallende regels ruimte krijgen,
  daarna terug omhoog, en een fade-out over de laatste ≈1.5s onder het logo
- Music cue guidance: preset gelezen uit
  `assets/music/cues/happy-beats-business-moves-vol-12-by-ende-dot-app.music-cues.md`.
  Strong cues in het venster: **8.74s**, **17.47s**, **18.56s**, 22.93s, 24.56s.
  Lock maximaal drie: de harde cut naar scene 3 op **8.74s** en het landen van het **logo** in scene 5 op **18.56s**.
  Beide zijn in de compositie gemarkeerd met `// beat-locked`.
  Beat-grid (≈0.54s tussenruimte, te snel voor leestekst): sequentiële **tekst** snapt op elke
  tweede beat (≈1.08s), non-tekst accenten (de 49 regels, de stapbolletjes) mogen op elke beat.
- Audio-reactive treatment: subtiel. Alleen de zachte gloed achter de CTA-knop in scene 1 en de
  aanwezigheid (opacity/scale, max ±2%) van de dossierkaart in scene 4 mogen op muziek-RMS ademen.
  Geen waveforms, geen equalizerbalken, geen deeltjes, geen strobe.
- SFX posture: sparse. Hooguit vier tot zes cues in de hele video, laag gemixt, altijd op hetzelfde
  frame als de beweging die ze ondersteunen. Liever één cue te weinig dan één te veel.
- Audio-coupled moments: het aanklikken van het tijdslot (scene 2), het bevestigingsmoment
  (scene 2, strong cue), de 49 regels die wegvallen (scene 3, één korte collectieve val — geen
  49 losse tikken), de `ABORT` die stukloopt (scene 4, één droge afslag), het logo (scene 5).
- Restraint rule: geen zweverige pads, geen "corporate succes"-fanfare, geen alarm- of
  foutgeluiden bij de 409-regels. Het is geen incident dat je ziet, het is een systeem dat werkt.
  De `ABORT` klinkt als een deur die dichtvalt, niet als een crash.

## Music cue guidance
- Track: `happy-beats-business-moves-vol-12-by-ende-dot-app.mp3` — 109,96 BPM
- Strong cues te overwegen: **8.74s** (bevestiging scene 2), **18.56s** (logo scene 5)
- Beat-grid vensters voor sequentiële reveals:
  - Scene 2 stappenbalk (5 bolletjes, non-tekst): elke beat vanaf ≈4.39s
  - Scene 3 de 49 regels (non-tekst): mag op de beat, maar liever als één golf
  - Scene 5 cijferregel (3 leesbare items): elke **tweede** beat vanaf ≈17.47s → 17.47 / 18.56 / 19.66
- Restraint: polished-tone. Maximaal twee locks. Als een lock de leesbaarheid of het holdmoment
  schaadt, wint de natuurlijke timing.

## Storyboard

### Scene 1 — De wachtkamer — 0.00 → 4.00s (clip 4.50s, 0.5s overlap voor de crossfade)
Volledig scherm `#faf7f2`. Het echte wordmark-logo links boven op klein formaat. Daaronder, in
Bodoni Moda light, de echte hero-kop verbatim over twee regels:
**"Individuele psychologische begeleiding gericht op _psychologische flexibiliteit_"** — waarbij
`psychologische flexibiliteit` cursief en in `#cf7b7c` staat, exact zoals in `HeroSection.tsx`.
Onder de kop verschijnt na een hold de echte CTA-knop: vierkant, `#DF8A8B`, wit, uppercase,
`tracking-[0.2em]`, tekst `MAAK EEN AFSPRAAK`, met het pijltje dat 6px naar rechts schuift.
Leestijd: de kop is negen woorden → minimaal 2.7s volledig zichtbaar en uitgeanimeerd.
Sequential/interaction: ja — kop settelt eerst, CTA-knop komt ≈1.2s later binnen en de pijl schuift.
Audio intent: de muziek start zacht; het beeld mag bijna stil zijn.
Audio-coupled idea: één zeer zachte interface-cue op het verschijnen van de CTA-knop. Verder niets.
Music: warm, laag, fade-in 0.8s.
Transition mood: soft (crossfade 0.6s) → Scene 2

### Scene 2 — De boeking — 4.00 → 8.74s (clip 4.74s, eindigt exact op de strong cue)
Nagebouwd wizardvenster op `#faf7f2`: witte kaart, `rounded-none`, dunne stone-rand, `shadow-xs`.
Bovenaan de echte voortgangsbalk met de vijf echte labels **Behandeling · Locatie · Datum ·
Details · Overzicht** (uit `WizardProgressBar.tsx`); de bolletjes vullen zich één voor één in
`#DF8A8B` op de beat. Daaronder een weekrooster met tijdslot-chips (`09:00`, `10:15`, `11:30`,
`14:00`, `15:15`). Een cursor beweegt naar `10:15` en klikt; die chip wordt zalmroze en de
omliggende chips vervagen — het slot is weg voor iedereen. Tekstregel onderaan, klein:
**"Vijf stappen. Eén tijdslot."**
Alle inhoud is fictief; er staat geen naam, geen dossiernummer en geen notitie in beeld.
Sequential/interaction: ja — vijf stappenbolletjes op de beat, daarna een gesimuleerde cursorklik
op de chip `10:15`, gevolgd door het dichtvallen van de omliggende chips.
Audio intent: lichte doelgerichtheid; het moet voelen als iets dat afgerond wordt.
Audio-coupled idea: een zachte klik-cue exact op het cursormoment, en één ingehouden
bevestigingscue op het vastzetten van het slot — beat-locked richting **8.74s**.
Transition mood: hard cut (0.0–0.1s) → Scene 3. Dit is de enige harde cut in de video.

### Scene 3 — Vijftig tegelijk — 8.74 → 12.74s (clip 4.40s, harde cut in)
Cut naar donker: `#1d1d1b`. Rechts één enkele slot-regel `dinsdag 10:15`. Links vallen vijftig dunne
aanvraagregels binnen als één golf. Binnen ≈0.7s worden er 49 grijs en krimpen weg, elk met een klein
`409` label; precies één blijft staan in `#f3b5b4` met `201`.
Tekst boven, in Bodoni Moda: **"Vijftig aanvragen. Eén tijdslot."**
Tekst onder, in mono, verschijnt nadat de golf is gevallen en houdt vast tot het einde van de scene:
**`1 toegekend · 49 geweigerd · 0 dubbele afspraken`**
Bron: `tests/BackendTests/BookingConcurrencyTests.cs` — 50 parallelle threads, `Assert.Equal(1, …)`
en `Assert.Equal(49, …)`. Geen enkel gegeven in deze scene is persoonsgebonden.
Leestijd: de kopregel is vier woorden → ≥1.2s; de cijferregel is de payoff → ≥1.5s settled.
Sequential/interaction: ja — één collectieve golf naar binnen, dan één collectieve val van 49.
Niet 49 losse animaties met 49 losse geluiden.
Audio intent: de muziek duikt weg zodat de val ruimte krijgt; daarna komt ze terug.
Audio-coupled idea: één korte, lage collectieve val-cue op het wegvallen van de 49. Eén enkele,
helderdere cue op de regel die blijft staan.
Transition mood: clean (crossfade 0.4s) → Scene 4

### Scene 4 — Wat er niet uit komt — 12.74 → 17.74s (clip 5.40s)
Blijft donker (`#22201e`). Eén dossierkaart, vierkante hoeken, dunne rand. De velden staan er eerst
leesbaar in fictieve vorm en vallen dan zichtbaar dicht:
- `Dossier` `#0042` (blijft, is fictief)
- `Patiënt` `M. V.` (initialen, blijft)
- `Rijksregisternummer` `••.••.••-•••.••` (staat direct gemaskeerd, valt niet "van echt naar masker")
- `Consultatienotitie` `ENC:v2:9f3a…` — ciphertext, nooit leesbare tekst
Label onder de kaart: **"AES-256-GCM, veld per veld."**
Daarna, onder de kaart, één mono-regel die intypt: `UPDATE Auditlogboek SET …` gevolgd door een
droge stempel `ABORT` in `#f3b5b4`, met daaronder klein: **"De database weigert het."**
Bron: `Services/Security/AesEncryptionService.cs` en migratie
`20260902195621_VoegAppendOnlyTriggersToeOpAuditlogboek` (`RAISE(ABORT, …)`).
Sequential/interaction: ja — de kaartvelden komen regel voor regel op elke tweede beat binnen,
daarna typt de SQL-regel uit en slaat `ABORT` erop.
Audio intent: ingehouden. Dit is de zwaarste claim van de video en hij mag het stilst klinken.
Audio-coupled idea: zachte toetsaanslagen onder de typende SQL-regel, en één droge afslag op
`ABORT` — als een deur, niet als een fout.
Transition mood: soft (crossfade 0.6s) → Scene 5

### Scene 5 — Rust aan de voorkant — 17.74 → 23.00s (clip 5.26s)
Terug naar `#faf7f2`. Het logo komt centraal binnen — **beat-locked op ≈18.56s**. Daaronder, op elke
tweede beat (≈17.47 / 18.56 / 19.66 → verschoven zodat ze ná het logo landen), drie korte
cijferitems in mono, klein en grijs:
`.NET 10 · React 18` — `94,1% lijndekking` — `1 conflictdetector · 0 dubbele afspraken`
Daarna, in Bodoni Moda, de slotregel die tot het einde blijft staan:
**"Rust aan de voorkant. Discipline aan de achterkant."**
Elk cijfer is geverifieerd: `net10.0` in de csproj, `react ^18.3.1` in package.json, 94,1% uit
`FullCoverageReport/Summary.txt` (17-09-2026), `AfspraakConflictDetector` als één klasse.
Leestijd: drie items × ≥0.8s, slotregel zes woorden → ≥1.8s settled tot de laatste frame.
Sequential/interaction: ja — drie cijferitems één voor één op elke tweede beat.
Audio intent: de muziek zakt weg onder de slotregel; de laatste seconde is bijna stil.
Audio-coupled idea: één zachte cue op het landen van het logo. Daarna niets meer.
Transition mood: n.v.t. — fade to hold op de slotregel.

**Music mood for this video:** ingehouden, warm, laag gemixt — aanwezig maar nooit sturend.
**Audio summary:** een lage warme bed die in scene 3 wegduikt voor de val van 49 regels, in scene 4
bijna helemaal terugtreedt voor een getypte SQL-regel en één droge `ABORT`, en onder de slotregel
uitfadet naar stilte.

## Verificatienotitie
Elk cijfer en elke technische bewering in deze video is vóór opname tegen de code getoetst:

| Bewering op scherm | Bron | Status |
| :--- | :--- | :--- |
| 50 aanvragen → 1 toegekend, 49 geweigerd | `tests/BackendTests/BookingConcurrencyTests.cs:70,140,142` | geverifieerd |
| AES-256-GCM veldencryptie | `Services/Security/AesEncryptionService.cs` | geverifieerd |
| Auditlogboek weigert UPDATE/DELETE | migratie `…VoegAppendOnlyTriggersToeOpAuditlogboek.cs:39,48` | geverifieerd |
| 94,1% lijndekking | `FullCoverageReport/Summary.txt` (17-09-2026) + `docs/coverage-badge.svg` | geverifieerd |
| .NET 10 | `AfsprakenbeheerPsycholoog.csproj:4` (`net10.0`) | geverifieerd |
| React 18 | `ClientApp/package.json:22` (`^18.3.1`) | geverifieerd — README zegt "18/19", de lockfile zegt 18 |
| Eén conflictdetector | `Services/Planning/AfspraakConflictDetector.cs` | geverifieerd |
| Wizardlabels, hero-kop, CTA-tekst, kleuren | `WizardProgressBar.tsx`, `HeroSection.tsx`, `tailwind.config.js` | verbatim overgenomen |

Bewust **niet** op scherm: het testaantal (README zegt 1.587; niet nagerekend zonder de suite te
draaien) en het RIZIV-sessiecontingent gekoppeld aan een persoon.
