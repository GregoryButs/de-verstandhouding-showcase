# Launch video — bron en render

Een film van 66 seconden over De Verstandhouding, met de volledige bron waarmee hij gemaakt is.
De compositie is HTML plus één GSAP-tijdlijn; [HyperFrames](https://hyperframes.heygen.com)
rendert die frame voor frame naar MP4.

De film is opgebouwd in drie bedrijven — **wat de patiënt ziet → wat de praktijk ziet → wat
niemand ziet** — met Engelse narratie over de echte, Nederlandse interface. Dat is bewust: het
product spreekt zijn eigen taal, de stem legt uit.

| Bestand | Wat het is |
| :--- | :--- |
| `brag.mp4` | De film. 1920×1080, 30fps, 66,0s, narratie + muziek + SFX. Het posterframe is als frame 0 ingebakken, zodat elke thumbnail-grabber dat beeld pakt. |
| `brag.jpg` | Het posterframe los, voor `<video poster>` en platforms die een eigen thumbnail accepteren. |
| `brag-short.mp4` | De eerdere cut van 23s, zonder narratie. Bruikbaar waar 66s te lang is. |
| `composition/index.html` | De volledige compositie: elf scènes, één `gsap.timeline({paused:true})`, dertien audiotracks. |
| `script-v2.md` | Het script: narratie, storyboard, en het geverifieerde bronmateriaal per scène. |
| `brag-plan.md` | Het oorspronkelijke plan van de korte versie. |
| `share-copy.txt` | De bijschrifttekst. |

## De elf scènes

| # | Scène | Venster | Wat er te zien is |
| :--- | :--- | :--- | :--- |
| 1 | De wachtkamer | 0:00–0:04 | De echte hero van de landingspagina, verbatim |
| 2 | Vijf stappen | 0:04–0:09 | De boekingswizard: behandeling, locatie, tijdslot |
| 3 | Het komt terug | 0:09–0:15 | Eén boeking vult vier kanalen: Meet, Google Agenda, `.ics`, herinnering |
| 4 | De agenda | 0:15–0:25 | Praktijkuren, gesloten uren, ELP-zittingen, no-show |
| 5 | Het dossier | 0:25–0:31 | Gemaskeerde dossiers en `Dossier exporteren` (AVG art. 15/20) |
| 6 | De maandafsluiting | 0:31–0:39 | RIZIV-prestatiecodes, trajecttellers, CSV voor het eHealth-portaal |
| 7 | Vijftig tegelijk | 0:39–0:48 | 49 aanvragen vallen weg met `409`, één blijft staan met `201` |
| 8 | Versleuteld | 0:48–0:52 | AES-256-GCM per veld, plus de SHA-256 hash-chain van het auditlogboek |
| 9 | ABORT | 0:52–0:55 | `UPDATE Auditlogboek` loopt stuk op de append-only trigger |
| 10 | De wachtrij blijft staan | 0:55–1:01 | De herpogingsladder 3 · 9 · 27 · 81 · 243, en een herstart die niets kost |
| 11 | Rust aan de voorkant | 1:01–1:06 | Logo, cijfers, slotregel |

De harde cut naar het derde bedrijf ligt op **39,49s**: een strong cue van de muziek, en precies
het moment waarop de narratie *"None of it matters if two people can take the same slot"* inzet.
Beeld, stem en beat vallen samen.

## Opnieuw renderen

```bash
cd composition
npx hyperframes check      # lint, runtime, layout, motion en WCAG-contrast in één gate
npx hyperframes preview    # studio met tijdlijn op localhost
npx hyperframes render --quality delivery --output ../brag.mp4
```

Vereist Node 22+, FFmpeg en een Chrome. `check` moet groen zijn vóór een render; een lint-fout
schakelt de layout- en contrastaudits uit, en dan meldt `check` `0 samples` — dat leest als
schoon maar betekent dat er niets gedraaid heeft.

De narratie is vooraf gegenereerd en zit als `assets/vo/narration.wav` in de compositie. Opnieuw
maken kan met Kokoro-82M (stem `bf_emma`, en-GB); dat vraagt `kokoro-onnx`, `soundfile` en een
werkende `espeak-ng` op het systeem. De dertien regels zijn apart gesynthetiseerd, gemeten en met
vaste stiltes aan elkaar gezet — de scèneduren volgen uit de audio, niet andersom.

## Geen patiëntgegevens

Dit is een zorgtoepassing, dus dat is geen detail. Elke interface in de film is nagebouwd in HTML
met verzonnen inhoud. De ontwikkeldatabase is niet gelezen, gequeryd of gerenderd, en er zijn geen
screenshots van de draaiende applicatie gebruikt.

- Namen alleen als initialen (`M. V.`, `L. D.`, `K. B.`), dossiernummers zichtbaar fictief
- Rijksregisternummer staat overal volledig gemaskeerd: `••.••.••-•••.••`
- De consultatienotitie toont ciphertext (`ENC:v2:9f3a…`), nooit leesbare tekst
- Geen geboortedatum, telefoon, e-mail of diagnose
- De prestatiecodes in scène 6 zijn echt, maar de rijen waarin ze staan zijn verzonnen
- Op scherm staat het er ook: *"Voorbeeldgegevens — geen echte patiënt."*

## Wat er op scherm beweerd wordt, en waar het vandaan komt

Elk cijfer is vóór de render tegen de code getoetst, niet overgenomen uit documentatie.

| Op scherm | Bron |
| :--- | :--- |
| 50 aanvragen → 1 toegekend, 49 geweigerd | `tests/BackendTests/BookingConcurrencyTests.cs` |
| AES-256-GCM per veld | `Services/Security/AesEncryptionService.cs` |
| Auditlogboek weigert `UPDATE` | migratie `…VoegAppendOnlyTriggersToeOpAuditlogboek.cs`, `RAISE(ABORT)` |
| Herpoging 3 · 9 · 27 · 81 · 243 | `Services/Agenda/CalendarSyncTaskProcessor.cs`, `[AutomaticRetry]` |
| Prestatiecodes `726810` · `726530` · `726832` · `726574` | `Helpers/ElpConventieHelper.cs` (RIZIV-tarieflijst 01-01-2026, lexicon 03/2026) |
| Contingenten 8 / 10 / 20 sessies | idem, `MaximumOndersteuningVolwassene` / `…Kind` / `MaximumBehandeling` |
| Agendakleuren en legenda | `ClientApp/src/pages/CalendarPage.tsx` |
| ELP-kolommen en statuswaarden | `ClientApp/src/pages/ElpMaandafsluiting.tsx` |
| 1.828 tests · 94,3% dekking | gemeten op 20-09-2026: 1248 xUnit + 580 Vitest |
| .NET 10 · React 18 | `csproj` → `net10.0`, `package.json` → `react ^18.3.1` |

## Herkomst en licenties van de assets

| Asset | Herkomst | Licentie |
| :--- | :--- | :--- |
| `fonts/inter-300-800-latin.woff2` | [Inter](https://rsms.me/inter/), rsms | SIL Open Font License 1.1 |
| `fonts/bodoni-moda-400-900-latin.woff2` | [Bodoni Moda](https://github.com/indestructible-type/Bodoni), indestructible type* | SIL Open Font License 1.1 |
| `sfx/*.ogg`, `sfx/*.wav` | [Kenney](https://kenney.nl/) | Kenney publiceert zijn asset packs onder CC0 — controleer het pack zelf als het ertoe doet |
| `images/*` | De Verstandhouding | Eigen beeldmateriaal van de praktijk, ook op deverstandhouding.be |
| `vo/narration.wav` | Gegenereerd met [Kokoro-82M](https://github.com/thewh1teagle/kokoro-onnx), stem `bf_emma` | Apache-2.0 model; de tekst is eigen werk |
| `music/happy-beats-business-moves-vol-9…mp3` | ["Happy Beats / Business Moves", ende.app](https://ende.app/en) | **Voorwaarden niet gedocumenteerd** — zie hieronder |

> [!important] De muziektrack draagt geen vastgelegde licentie.
> De track komt uit de bundel van de `/brag`-skill, en de `README.md` daarvan zegt expliciet dat de
> exacte voorwaarden geverifieerd en gedocumenteerd moeten worden vóór publicatie of
> herdistributie. Dat is niet gebeurd. Het bestand staat hier omdat de compositie zonder muziek
> niet rendert zoals bedoeld; gebruik het niet elders zonder de voorwaarden bij ende.app na te gaan.

De fonts staan onder OFL, wat herdistributie toestaat mits de licentietekst meegaat: zie
[`LICENSES-FONTS.md`](LICENSES-FONTS.md).

## Vormgeving

De kleuren komen uit de applicatie zelf: `tailwind.config.js` voor het zalmroze van de
landingspagina, en `CalendarPage.tsx` voor het terracotta en teal van de agenda. Twee tinten zijn
bewust donkerder dan op de site — wit op `#DF8A8B` haalt 2,58:1 en zakt door de WCAG-contrastgate
van `hyperframes check`. Zelfde kleurfamilie, wel leesbaar.

De muziek is gekozen op gemeten dynamiek in plaats van op gehoor: van de vijf beschikbare tracks
heeft vol-9 het grootste bereik, en zijn natuurlijke terugval rond 55–65s valt samen met de outro.
Onder de stem zakt de muziek naar 0.12 en komt kort omhoog in de gaten tussen de bedrijven, zodat
je de aktegrenzen hoort.
