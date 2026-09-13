# CV & LinkedIn Snippets – De Verstandhouding Case Study

Gebruik onderstaande kant-en-klare teksten op je **Curriculum Vitae**, **LinkedIn Profiel** of in **Sollicitatiebrieven**.

---

## 🇳🇱 1. Nederlands (Voor CV & Sollicitaties)

### Korte Versie (Voor 1-pagina CV of Compacte Ervaringsectie)
> **De Verstandhouding – Praktijkbeheer & Patiëntenportaal (Lead Full-Stack Architect)**  
> *Stack: ASP.NET Core 10 LTS Web API, C# 13, Entity Framework Core 10, React 18/19, TypeScript, Tailwind CSS, Hangfire, HL7 FHIR R4*  
> * Ontwierp een modulair zorgplatform volgens **Domain-Driven Design (DDD)** met rijke *Afspraak* aggregate, asynchrone repositorylaag en CQRS-modelscheiding.  
> * Implementeerde een atomaire beschikbaarheidsengine (`SlotCalculator`) en centrale conflictdetector met `System.Threading.Lock` die *double-bookings* 100% uitsluit.  
> * Waarborgde medische data-privacy (GDPR) via **AES-256 GCM veld-encryptie**, een onweerlegbare **append-only audit trail met database triggers** en HMAC consent validatie.  
> * Integreerde realtime 2-weg **Google Calendar API** synchronisatie met duurzame Hangfire achtergrondwachtrij, health checks en automatische Google Meet generatie.  
> * Behaalde **92,1% geautomatiseerde testdekking** (1.064 xUnit backend tests, 524 Vitest frontend tests — 1.588 tests totaal) met een complete GitHub Actions CI/CD pipeline.

---

### Uitgebreide Versie (Voor LinkedIn Projectsectie / Portfolio Beschrijving)
> **Lead Architect & Full-Stack Developer – De Verstandhouding**  
> *Full-Stack .NET 10 LTS & React Platform voor Psychologenpraktijken*  
> 
> **Doel & Impact**:  
> Ontwerp en realisatie van een end-to-end afspraken- en praktijkbeheersysteem voor de eerstelijnspsychologische zorg, ter vervanging van foutgevoelige handmatige planning en sessieopvolging.
> 
> **Belangrijkste Technische Prestaties**:  
> 1. **Architectuur & DDD**: CQRS-scheiding tussen lees- en schrijfmodellen, asynchrone repositorylaag, en een rijke `Afspraak` aggregate root met expliciete domein-invariants onder .NET 10 LTS.  
> 2. **Concurrency & Thread-Safety**: Zero double-booking garantie via geharmoniseerde conflictvalidatie, buffertijden en 50-thread multi-threaded xUnit stress tests.  
> 3. **Privacy & Compliance**: Transparante AES-256 GCM veldencryptie (met startup backfill), SQLite database triggers die mutaties op het auditlogboek fysiek blokkeren, en geautomatiseerde 2-jarige GDPR-retentie.  
> 4. **Belgische Zorgwetgeving (ELP/RIZIV)**: Sessieteller per referentieperiode van twaalf maanden, zorgfunctie en prestatiecode per sessie, inclusie in een Mental Health Care-netwerk, groepssessies met deelnemerregistratie en uitnodigingen, plus registratie-export voor het eHealth/ELP-portaal.  
> 5. **Interoperabiliteit & Resilientie**: HL7 FHIR R4 compatibele endpoints, duurzame Hangfire kalenderwachtrij en `GoogleCalendarHealthCheck` met graceful degradation.  
> 6. **Kwaliteitsborging**: 92,1% testdekking (1.064 backend + 524 frontend tests, 1.588 tests totaal), EF Core Model Snapshot drift tests, en geautomatiseerde zero-downtime deployment pipelines.

---

## 🇬🇧 2. English (For International CVs & Global LinkedIn Reach)

### Short Version (For English Resume)
> **De Verstandhouding – Clinical EHR & Patient Booking Platform (Lead Full-Stack Architect)**  
> *Stack: ASP.NET Core 10 LTS, C# 13, Entity Framework Core 10, React 18/19, TypeScript, Tailwind CSS, Hangfire, HL7 FHIR R4*  
> * Architected a modular clinical management platform with **CQRS read/write model separation**, async repository patterns, and a rich Domain-Driven Design (DDD) Appointment aggregate.  
> * Built a high-performance, concurrency-safe booking engine (`SlotCalculator`) with unified conflict detection and transaction isolation, preventing 100% of double-bookings.  
> * Enforced strict GDPR/medical data privacy through **AES-256 GCM field-level encryption**, tamper-proof **append-only audit trails with database triggers**, and server-side HMAC consent verification.  
> * Integrated two-way **Google Calendar API** sync with durable Hangfire background queues, resilient health checks, and dynamic Google Meet provisioning.  
> * Established **92.1% automated test coverage** across 1.064 xUnit tests, multi-threaded concurrency suites, and 524 Vitest tests (1.588 tests total) within a GitHub Actions CI/CD pipeline.

---

## 🔗 3. Hoe link je dit op je CV?

Plaats onder de projecttitel op je CV een klikbare link naar je portfolio-case study of LinkedIn:
*   `Portfolio: https://gregorybuts.github.io/de-verstandhouding-showcase/`
*   `Case Study Document: [Bekijk Technische Architectuur & Metrieken]`
