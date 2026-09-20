# Script v2 — De Verstandhouding, ~60 seconden

Drie bedrijven: **wat de patiënt ziet → wat de praktijk ziet → wat niemand ziet.**
De UI op scherm blijft Nederlands (dat is het echte product). Narratie en redactionele
tekst zijn Engels.

## Vastgelegd

| | |
| :--- | :--- |
| Lengte | ~60s, één film (geen korte social-cut, tenzij later gevraagd) |
| Formaat | 1920×1080, 30fps |
| Muziek | `happy-beats-business-moves-vol-9` — gemeten keuze, zie onder |
| Taal | UI Nederlands (verbatim), narratie + captions Engels |
| Anonimisering | ongewijzigd en strenger toegepast, zie `brag-plan.md` |

### Waarom vol-9

RMS gemeten per 5s-venster over 0–65s van alle vijf gebundelde tracks:

```
 vol-1  164s  ▇▇▇███▆▅▇▇██   spreiding 0.130
vol-10   60s  ▇▇██▇██████    spreiding 0.049
vol-11   88s  ██▇▇███▇▇▆██   spreiding 0.070
vol-12  117s  ▄▅▇▇███▆▇██▇   spreiding 0.150   (huidige track)
 vol-9  114s  ▆▆▆▇██▇███▅▄   spreiding 0.173   ← gekozen
```

vol-9 heeft het grootste dynamische bereik, en belangrijker: de vorm valt samen met de
drie bedrijven. Rustige opening (`▆▆▆`), opbouw (`▇██`), gedragen midden (`▇███`), en een
natuurlijke terugval (`▅▄`) precies waar de outro op 55–60s landt. De muziek doet de
aktestructuur dus mee, in plaats van er dwars doorheen te lopen.

---

## Narratie (Engels, ~140 woorden)

Timings zijn richtinggevend; bij een gesynthetiseerde of opgenomen stem bepaalt de
werkelijke duur van de audio de scèneduur, niet andersom.

| # | ~t | Regel |
| :--- | :--- | :--- |
| 1 | 0:02 | The front door of a Belgian psychology practice. |
| 2 | 0:05 | A patient picks a treatment, a location, and a time. Five steps. |
| 3 | 0:10 | What comes back is already complete — a calendar invite, an ICS file, a video link, a reminder. |
| 4 | 0:17 | Behind it, the practice sees a different screen. |
| 5 | 0:20 | The calendar knows when the practice is open, how long a session runs, and what buffer belongs between two people. |
| 6 | 0:26 | Records live here too. The export button isn't a feature — under Article 15, it's a right. |
| 7 | 0:31 | And then the Belgian part: eight sessions per reference period, twenty for treatment. The performance codes resolve themselves. |
| 8 | 0:38 | None of it matters if two people can take the same slot. |
| 9 | 0:42 | Fifty simultaneous requests. One booking. Forty-nine clean refusals. |
| 10 | 0:47 | Every sensitive field encrypted. Every audit line chained — the database refuses to rewrite its own history. |
| 11 | 0:52 | Queued calendar work survives a restart. A deploy is no reason to lose someone's appointment. |
| 12 | 0:57 | Calm at the front. Discipline underneath. |

---

## Storyboard

### Act I — Wat de patiënt ziet (0:00–0:16)

**S1 · De wachtkamer · 4s** — Ongewijzigd t.o.v. v1. Hero verbatim, logo, kop met accent
op `psychologische flexibiliteit`, CTA `MAAK EEN AFSPRAAK`, foto rechts.
Narratie 1. Muziek fade-in.

**S2 · Vijf stappen · 5s** — De wizard écht gevuld in plaats van vijf bolletjes:
behandelkeuze, de drie locaties (`Praktijk` / `GoogleMeet` / `Telefoon`), het weekrooster.
Cursor kiest `10:15`, chip valt dicht, buren vervagen.
Narratie 2. Beat-grid op de stappenbolletjes.

**S3 · Het komt terug · 7s** — NIEUW. Het patiëntenportaal ná de boeking. Afspraakkaart
met `Consultatie`, locatie, en dan één voor één: `Deelnemen` (Meet), `+ Google Agenda`,
`Apple / Outlook (.ics)`, `15 minuten voor aanvang`.
Narratie 3. Elk kanaal landt op een beat.

### Act II — Wat de praktijk ziet (0:16–0:36)

**S4 · De agenda · 7s** — NIEUW. `Praktijk Agenda`, een week die zich vult met de echte
kleurcodering: `Praktijkuren (Open voor boekingen)`, `Buiten praktijkuren (Gesloten)`,
`ELP Zorgzitting`, `GoogleMeet`, `NoShow`, geblokkeerd. Alleen initialen.
Narratie 4 + 5.

**S5 · Het dossier · 5s** — NIEUW. Patiëntentabel: initialen, `Dossiernummer`,
gemaskeerd `Rijksregisternummer`. Eén rij opent → `Afsprakenhistorie`,
`Gemiste afspraken`, en dan `Dossier Exporteren`.
Narratie 6.

**S6 · De maandafsluiting · 8s** — NIEUW, en het hart van de film. `ELP Maandafsluiting`.
Kolommen: `Datum & Tijd` · `Patiënt & Dossier #` · `INSZ` (gemaskeerd) ·
`Prestatiecode & Omschrijving` · `Traject Teller` · `Status Ingegeven`.
Rijen vullen zich, codes verschijnen vanzelf (`726810`, `726832`, `726854`), de teller
loopt `6/8 → 7/8`, status slaat om van `Ontbreekt - Invullen` naar `Klaar!`, en onderaan
gaat `Te verwerken` naar `Verwerkt`.
Narratie 7. Dit is de scène die laat zien dat je het domein kent.

### Act III — Wat niemand ziet (0:36–0:55)

**S7 · Vijftig tegelijk · 5s** — Harde cut naar donker. Bestaand, iets ruimer.
Narratie 8 + 9. Strong-cue lock op de cut.

**S8 · Versleuteld · 5s** — Bestaand, uitgebreid: naast de dichtvallende velden en
`AES-256-GCM` ook de SHA-256 hash-chain als zichtbare ketting van schakels.
Narratie 10 (eerste helft).

**S9 · ABORT · 4s** — `UPDATE Auditlogboek SET …` typt uit en loopt stuk op `ABORT`.
Bestaand. Narratie 10 (tweede helft).

**S10 · De wachtrij blijft staan · 5s** — NIEUW. Hangfire: een rij agenda-synctaken, de
server herstart (korte onderbreking), de rij staat er nog en loopt door.
Narratie 11.

### Outro (0:55–1:00)

**S11 · Rust aan de voorkant · 5s** — Logo, cijferregel
`1.828 tests · 94,3% dekking · .NET 10 · React 18`, slotregel
**"Calm at the front. Discipline underneath."**
Narratie 12. Muziek fade-out op de natuurlijke terugval van de track.

---

## Geverifieerd bronmateriaal voor de nieuwe scènes

Alles hieronder is uit de code gelezen, niet verzonnen.

### S4 — Praktijk Agenda (`pages/CalendarPage.tsx`)

De agenda heeft een eigen palet naast het zalmroze van de landingspagina:

| Kleur | Betekenis |
| :--- | :--- |
| `#d97767` | Praktijkuren (Open voor boekingen) |
| `#478d96` | `ELP`-badge — ELP Zorgzitting |
| `#1a2c30` | Vandaag-markering (donker), in darkmode `#478d96` |
| `#f4efe6` | Achtergrond kopregel |

Legenda verbatim: `Praktijkuren (Open voor boekingen)` · `Buiten praktijkuren (Gesloten)` ·
`ELP Zorgzitting`. Boekbaarheid per slot komt uit `isBinnenPraktijkuren(settings, day, slot)`.

### S6 — ELP Maandafsluiting (`pages/ElpMaandafsluiting.tsx`)

Kolommen, verbatim en in deze volgorde:

`Datum & Tijd` · `Patiënt & Dossier #` · `Rijksregisternummer` · `Prestatiecode` ·
`Traject Teller` · `Status Ingegeven`

Statuswaarden: `Ontbreekt - Invullen` → `Klaar!`, en onderaan `Te verwerken` → `Verwerkt`.
Zorgfuncties: `Ondersteuning (ELPZ)` · `Behandeling (GPZ)` · `Gemeenschapsgericht`.
Doelgroep: `Alleen rechthebbende` · `Met context (ouders/partner)`.

De hulptekst in de UI zegt letterlijk: *"Kies de zorgfunctie in de kolom **Prestatiecode**;
de code volgt daar automatisch uit."* — dat is precies wat narratieregel 7 beweert.

**Echte RIZIV-pseudocodes** uit `Helpers/ElpConventieHelper.cs` (bron: RIZIV-tarieflijst
per 01-01-2026 en het RIZIV-lexicon pseudocodes 03/2026, zie ADR-036):

| Code | Functie | Sessie | Setting | Doelgroep |
| :--- | :--- | :--- | :--- | :--- |
| `726471` | Ondersteuning (ELPZ) | eerste | Praktijk | alleen rechthebbende |
| `726530` | Ondersteuning (ELPZ) | vervolg | Praktijk | alleen rechthebbende |
| `726574` | Ondersteuning (ELPZ) | vervolg | Praktijk | met context |
| `726714` | Behandeling (GPZ) | eerste | Praktijk | alleen rechthebbende |
| `726773` | Behandeling (GPZ) | vervolg | Praktijk | alleen rechthebbende |
| `726810` | Behandeling (GPZ) | vervolg | Praktijk | met context |
| `726832` | Behandeling (GPZ) | vervolg | Vindplaats | met context |
| `726854` | Behandeling (GPZ) | vervolg | Aan huis | alleen rechthebbende |

Contingenten: **8** individuele ELPZ-sessies per referentieperiode vanaf 24 jaar, **10** tot
en met 23 jaar, **20** GPZ-sessies ongeacht leeftijd. Remgeld: €4,00 met verhoogde
tegemoetkoming, €11,00 standaard, €2,50 per deelnemer aan een groepsessie.

De CSV-export draagt zestien kolommen: `Datum, Starttijd, Eindtijd, Patient, Dossiernummer,
INSZ, Prestatiecode, Zorgfunctie, Doelgroep, Setting, BVT, Remgeld, Remgeld_aangerekend,
ELP_Type, Sessie_Teller, Status`.

### S10 — Duurzame agendawachtrij (`Services/Agenda/CalendarSyncTaskProcessor.cs`)

Concreter dan "de wachtrij overleeft een herstart": de klasse draagt

```csharp
[AutomaticRetry(Attempts = 5, DelaysInSeconds = new[] { 3, 9, 27, 81, 243 })]
```

Die ladder — 3, 9, 27, 81, 243 seconden — is de scène. Een taak die faalt schuift op naar
rechts over een zichtbare trap, en de herstart van de server laat de rij staan.

### Outro
Cijfers gemeten op 20-09-2026: 1248 xUnit + 580 Vitest = 1828 tests, 94,3% lijndekking.

## Openstaand: de stem

Zie het gespreksverslag. Kokoro spreekt geen Nederlands (opgelost: Engels), maar de lokale
synthese loopt op deze machine vast op een verpakkingsbug in `espeakng-loader` 0.2.4.
