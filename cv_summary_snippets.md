# CV & LinkedIn Snippets – De Verstandhouding Case Study

Gebruik onderstaande kant-en-klare teksten op je **Curriculum Vitae**, **LinkedIn Profiel** of in **Sollicitatiebrieven**.

---

## 🇳🇱 1. Nederlands (Voor CV & Sollicitaties)

### Korte Versie (Voor 1-pagina CV of Compacte Ervaringsectie)
> **De Verstandhouding – Praktijkbeheer & Patiëntenportaal (Lead Full-Stack Architect)**  
> *Stack: ASP.NET Core 10 LTS Web API, C# 13, Entity Framework Core 10, React 18/19, TypeScript, Tailwind CSS, Hangfire, HL7 FHIR R4*  
> * Ontwierp en bouwde een modulair zorgplatform met **CQRS-scheiding tussen lees- en schrijfmodellen** en een expliciet gemodelleerd domein.  
> * Implementeerde een atomaire beschikbaarheidsengine (`SlotCalculator`) met `System.Threading.Lock` en database-isolatie die *double-bookings* en race-conditions 100% uitsluit.  
> * Waarborgde medische data-privacy (GDPR) via **AES-256 veld-encryptie** in de database (met unieke IV's en multi-key rotatie) en strikte BOLA/IDOR autorisatie.  
> * Integreerde realtime 2-weg **Google Calendar API** synchronisatie, automatische Google Meet generatie en asynchrone e-mail herinneringen via **Hangfire**.  
> * Behaalde **90%+ geautomatiseerde testdekking** (624 xUnit backend tests, 370 Vitest frontend tests — 994 tests totaal) met een complete GitHub Actions CI/CD pipeline.

---

### Uitgebreide Versie (Voor LinkedIn Projectsectie / Portfolio Beschrijving)
> **Lead Architect & Full-Stack Developer – De Verstandhouding**  
> *Full-Stack .NET 10 LTS & React Platform voor Psychologenpraktijken*  
> 
> **Doel & Impact**:  
> Ontwerp en realisatie van een end-to-end afspraken- en praktijkbeheersysteem voor de eerstelijnspsychologische zorg, ter vervanging van foutgevoelige handmatige planning en facturatie.
> 
> **Belangrijkste Technische Prestaties**:  
> 1. **Architectuur & Schaalbaarheid**: CQRS-scheiding tussen lees- en schrijfmodellen, met ontkoppelde C# controllers, application services en repositories onder .NET 10 LTS.  
> 2. **Concurrency & Thread-Safety**: Zero double-booking garantie via geavanceerde database lock-validaties, buffertijden en 50-thread multi-threaded xUnit stress tests.  
> 3. **Privacy & Beveiliging**: Transparante AES-256 veldencryptie op patiëntgegevens via EF Core ValueConverters en mitigatie van OWASP Top 10 kwetsbaarheden.  
> 4. **Belgische Zorgwetgeving (ELP/RIZIV)**: Geautomatiseerde opvolging van het 8-sessies contingent per cliënt inclusief 1-click facturatie export voor zorgnetwerken.  
> 5. **Interoperabiliteit**: HL7 FHIR R4 compatibele endpoints voor koppeling met Elektronische Patiënten Dossiers (EPD/EHR).  
> 6. **Kwaliteitsborging**: 90%+ testdekking (624 backend + 370 frontend tests, 994 tests totaal), EF Core Model Snapshot drift tests, en geautomatiseerde zero-downtime deployment pipelines.

---

## 🇬🇧 2. English (For International CVs & Global LinkedIn Reach)

### Short Version (For English Resume)
> **De Verstandhouding – Clinical EHR & Patient Booking Platform (Lead Full-Stack Architect)**  
> *Stack: ASP.NET Core 10 LTS, C# 13, Entity Framework Core 10, React 18/19, TypeScript, Tailwind CSS, Hangfire, HL7 FHIR R4*  
> * Architected a modular clinical management platform with **CQRS read/write model separation** and an explicitly modelled domain.  
> * Built a high-performance, concurrency-safe booking engine (`SlotCalculator`) with transaction isolation, preventing 100% of double-bookings.  
> * Enforced strict GDPR/medical data privacy through **AES-256 field-level database encryption** (with unique IVs and multi-key rotation) and fine-grained IDOR authorization checks.  
> * Integrated two-way **Google Calendar API** sync with dynamic Google Meet provisioning and asynchronous background job queues via **Hangfire**.  
> * Established **90%+ automated test coverage** across 624 xUnit tests, multi-threaded concurrency suites, and 370 Vitest tests (994 tests total) within a GitHub Actions CI/CD pipeline.

---

## 🔗 3. Hoe link je dit op je CV?

Plaats onder de projecttitel op je CV een klikbare link naar je portfolio-case study of LinkedIn:
*   `Portfolio: https://gregorybuts.be/projects/de-verstandhouding`
*   `Case Study Document: [Bekijk Technische Architectuur & Metrieken]`
