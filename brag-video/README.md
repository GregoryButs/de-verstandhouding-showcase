# Launch video — bron en render

Een video van 23 seconden over De Verstandhouding, met de volledige bron waarmee hij gemaakt is.
De compositie is HTML plus één GSAP-tijdlijn; [HyperFrames](https://hyperframes.heygen.com)
rendert die frame voor frame naar MP4.

| Bestand | Wat het is |
| :--- | :--- |
| `brag.mp4` | De render. 1920×1080, 30fps, 23,0s, met muziek en SFX. Het posterframe is als frame 0 ingebakken, zodat elke thumbnail-grabber dat beeld pakt. |
| `brag.jpg` | Het posterframe los, voor `<video poster>` en platforms die een eigen thumbnail accepteren. |
| `composition/index.html` | De volledige compositie: vijf scènes, één `gsap.timeline({paused:true})`, tien audiotracks. |
| `brag-plan.md` | Het plan en het storyboard, inclusief de tabel waarin elke bewering tegen de broncode getoetst is. |
| `composition-brief.md` | De brief waarmee de compositie is gebouwd. |
| `share-copy.txt` | De bijschrifttekst. |

## Opnieuw renderen

```bash
cd composition
npx hyperframes check      # lint, runtime, layout, motion en WCAG-contrast in één gate
npx hyperframes preview    # studio met tijdlijn op localhost
npx hyperframes render --quality delivery --output ../brag.mp4
```

Vereist Node 22+, FFmpeg en een Chrome. `check` moet groen zijn vóór een render; een lint-fout
schakelt de layout- en contrastaudits stil uit, en dan meldt `check` `0 samples` — dat leest als
schoon maar betekent dat er niets gedraaid heeft.

## Geen patiëntgegevens

Dit is een zorgtoepassing, dus dat is geen detail. Elke interface in de video is nagebouwd in HTML
met verzonnen inhoud. De ontwikkeldatabase is niet gelezen, gequeryd of gerenderd, en er zijn geen
screenshots van de draaiende applicatie gebruikt.

- Namen alleen als initialen (`M. V.`), dossiernummers zichtbaar fictief (`#0042`)
- Rijksregisternummer staat volledig gemaskeerd: `••.••.••-•••.••`
- De consultatienotitie toont ciphertext (`ENC:v2:9f3a…`), nooit leesbare tekst
- Geen geboortedatum, telefoon, e-mail, diagnose of aan een persoon gekoppelde prestatiecode
- Op scherm staat het er ook: *"Voorbeeldgegevens — geen echte patiënt."*

## Wat er op scherm beweerd wordt, en waar het vandaan komt

Elk cijfer is vóór de render tegen de code getoetst, niet overgenomen uit documentatie. De README
van de hoofdrepository liep op twee punten achter; die zijn hier gecorrigeerd.

| Op scherm | Bron | Opmerking |
| :--- | :--- | :--- |
| 50 aanvragen → 1 toegekend, 49 geweigerd | `tests/BackendTests/BookingConcurrencyTests.cs` | 50 parallelle threads, `Assert.Equal(1, …)` en `Assert.Equal(49, …)` |
| AES-256-GCM per veld | `Services/Security/AesEncryptionService.cs` | |
| Auditlogboek weigert `UPDATE` | migratie `…VoegAppendOnlyTriggersToeOpAuditlogboek.cs` | SQLite-trigger met `RAISE(ABORT, …)` |
| 94,1% lijndekking | `FullCoverageReport/Summary.txt`, 17-09-2026 | een latere run gaf 94,3%; het getal in de video onderschat dus |
| .NET 10 | `AfsprakenbeheerPsycholoog.csproj` → `net10.0` | |
| React 18 | `ClientApp/package.json` → `react ^18.3.1` | de hoofd-README zegt "18/19"; de lockfile zegt 18 |
| 1 conflictdetector | `Services/Planning/AfspraakConflictDetector.cs` | |

Bewust **niet** in beeld: het testaantal uit de README, omdat dat niet na te rekenen was zonder de
suite te draaien op het moment van maken.

## Herkomst en licenties van de assets

| Asset | Herkomst | Licentie |
| :--- | :--- | :--- |
| `fonts/inter-300-800-latin.woff2` | [Inter](https://rsms.me/inter/), rsms | SIL Open Font License 1.1 |
| `fonts/bodoni-moda-400-900-latin.woff2` | [Bodoni Moda](https://fonts.google.com/specimen/Bodoni+Moda), indestructible type* | SIL Open Font License 1.1 |
| `sfx/*.ogg`, `sfx/*.wav` | [Kenney](https://kenney.nl/) | Kenney publiceert zijn asset packs onder CC0 — controleer het pack zelf als het ertoe doet |
| `images/*` | De Verstandhouding | Eigen beeldmateriaal van de praktijk, ook op deverstandhouding.be |
| `music/happy-beats-business-moves-vol-12-by-ende-dot-app.mp3` | ["Happy Beats / Business Moves", ende.app](https://ende.app/en) | **Voorwaarden niet gedocumenteerd** — zie hieronder |

> [!important] De muziektrack draagt geen vastgelegde licentie.
> De track komt uit de bundel van de `/brag`-skill, en de `README.md` daarvan zegt expliciet dat de
> exacte voorwaarden geverifieerd en gedocumenteerd moeten worden vóór publicatie of
> herdistributie. Dat is niet gebeurd. Het bestand staat hier omdat de compositie zonder muziek
> niet rendert zoals bedoeld; gebruik het niet elders zonder de voorwaarden bij ende.app na te gaan.

De fonts staan onder OFL, wat herdistributie toestaat mits de licentietekst meegaat: zie
[`LICENSES-FONTS.md`](LICENSES-FONTS.md).

## Hoe hij in elkaar zit

Vijf scènes, één harde cut. De toon is bewust ingehouden — het is een zorgproduct, geen SaaS-launch.

| # | Scène | Venster | Wat er gebeurt |
| :--- | :--- | :--- | :--- |
| 1 | De wachtkamer | 0,00 – 4,00s | De echte hero van de landingspagina, verbatim |
| 2 | De boeking | 4,00 – 8,74s | De vijfstaps wizard vult; een cursor kiest een tijdslot |
| 3 | Vijftig tegelijk | 8,74 – 12,74s | 49 aanvragen vallen weg met `409`, één blijft staan met `201` |
| 4 | Wat er niet uit komt | 12,74 – 17,74s | Gemaskeerd dossier; `UPDATE Auditlogboek` loopt stuk op `ABORT` |
| 5 | Rust aan de voorkant | 17,74 – 23,00s | Logo, cijfers, slotregel |

De harde cut naar scène 3 ligt op 8,74s en het logo landt op 18,56s: allebei sterke beats van de
muziek (109,96 BPM), in de compositie gemarkeerd met `// beat-locked`. De vijf stappenbolletjes
lopen mee op het beat-raster. Leestekst niet — dat raster ligt op 0,54s en dat is te snel om te
lezen, dus regels houden een ondergrens van 0,8s volledig stil op scherm.

Twee dingen ademen subtiel mee op de muziek, gevoed door vooraf geëxtraheerde amplitudedata
(`assets/audio-data/music-reactive.js`): de gloed achter de knop in scène 1 en de dossierkaart in
scène 4, die laatste binnen ±2%. Geen waveforms, geen equalizerbalken.

De kleuren komen uit `tailwind.config.js` van de applicatie. Het accent en de knop zijn één tint
donkerder dan op de site: wit op `#DF8A8B` haalt 2,58:1 en zakt door de WCAG-contrastgate van
`hyperframes check`. Zelfde kleurfamilie, wel leesbaar.
