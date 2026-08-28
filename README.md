# Clinical Healthcare & EHR Practice Platform – Case Study

[![.NET 10 LTS](https://img.shields.io/badge/ASP.NET%20Core-10.0%20LTS-512BD4?logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![React 18/19](https://img.shields.io/badge/React-18%2F19-61DAFB?logo=react&logoColor=black)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.4-38B2AC?logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![HL7 FHIR R4](https://img.shields.io/badge/HL7_FHIR-R4-E36209.svg)](https://hl7.org/fhir/R4/)
[![Test Coverage](coverage-badge.svg)](./api.html)
[![Security](https://img.shields.io/badge/Security-AES--256-emerald.svg)]()

> **Architect & Full-Stack Developer**: Gregory Buts  
> **Platform**: De Verstandhouding – Clinical Appointment & Practice Management System  
> **Runtime**: .NET 10 LTS (C# 13) met Long-Term Support tot november 2028  
> **Interactive Showcase**: Open [`[index.html]`](https://gregorybuts.github.io/de-verstandhouding-showcase/index.html) in any browser or visit the live deployment.

---

## 🏛️ Systeemarchitectuur & Domeinmodel (CQRS-modelscheiding)

```mermaid
graph TD
    subgraph ClientApp ["Client Layer (React 18 + Vite + TypeScript)"]
        LP[Publieke Landingspagina]
        BW[5-Staps Boekingswizard]
        PD[Psycholoog Agenda & Dashboard]
        PT[Patiëntenbeheer & Dossiers]
        ELP[ELP Maandafsluiting Module]
    end

    subgraph API ["Backend API Gateway (ASP.NET Core 10 LTS)"]
        AC[Afspraak & Slot Controllers]
        PC[Patiënten & Portaal Controllers]
        FC[FHIR R4 Interop Controller]
        AuthC[Auth & OAuth2 / OIDC Handler]
    end

    subgraph Domain ["Domein & Services (CQRS-modelscheiding / C# 13)"]
        SC[SlotCalculator Engine]
        PBS[PatientBookingService]
        GCS[GoogleCalendarService]
        AES[AesEncryptionService - AES-256]
        RBG[Hangfire Reminder Worker]
    end

    subgraph Data ["Data & Storage Layer"]
        EF[EF Core 10 Repositories]
        DB[(Encrypted SQLite Database / WAL Mode)]
    end

    ClientApp -->|REST API / Axios / SameSite Cookies| API
    API --> Domain
    Domain --> EF
    EF --> DB
    Domain -->|Google APIs Client| Ext1[Google Calendar & Meet]
    Domain -->|SMTP / MailKit| Ext2[Transactionele E-mail]
```

---

## ⚡ Belangrijkste Technische Hoogtepunten

### 1. Concurrency Control & Double-Booking Preventie
*   Atomaire beschikbaarheidsengine (`SlotCalculator`) met instelbare openingstijden, pauzes en vaste 10–15 minuten buffertijden.
*   Transactie-isolatie in Entity Framework Core waardoor overlappende boekingen direct worden afgevangen (`HeeftConflict()`).
*   **Resultaat**: 0% race-conditions en double-bookings in multi-threaded xUnit stress tests.

### 2. Privacy-by-Design & AES-256 Encryptie (GDPR)
*   Gevoelige medische en persoonsgegevens (PII) worden transparant versleuteld met **AES-256** (met unieke IV's en multi-key rotatie) via een custom EF Core `EncryptedStringConverter`.
*   Data wordt uitsluitend in-memory gedecrypt voor geautoriseerde verzoeken, met strikte mitigatie van BOLA / IDOR.

### 3. RIZIV / ELP Conventie Contingent Tracking
*   Real-time domeinbewaking van het 8-sessies contingent per cliënt volgens de Belgische eerstelijnspsychologische zorgconventie.
*   1-Click export van maandafsluitingen en RIZIV-facturatielijsten.

### 4. 2-Weg Realtime Google Calendar Sync & Asynchrone Jobs
*   Bi-directionele synchronisatie met Google Calendar v3 API en dynamische Google Meet linkaanmaak voor videoconsultaties.
*   Asynchrone achtergrondworkers via **Hangfire** voor 24u-herinneringsmails met ICS-kalenderbijlagen.

---

## 📁 Showcase Structuur
```text
├── index.html                  # Interactieve showcase webpagina in officiële praktijkhuisstijl
├── PORTFOLIO_CASE_STUDY.md     # Volledige technische documentatie & architectuurbeschrijving
├── cv_summary_snippets.md      # CV en LinkedIn teksten (Nederlands & Engels)
└── assets/                     # Officiële merklogo's, vector assets en praktijkfoto's
```

---

## 👤 Auteur & Contact
**Gregory Buts**  
*Lead Full-Stack .NET & React Software Architect*  
GitHub: [github.com/GregoryButs](https://github.com/GregoryButs)
