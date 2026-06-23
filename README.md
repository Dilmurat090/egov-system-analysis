# E-Government Portal — System Analysis & Requirements Engineering

A personal system analysis project examining citizen-facing e-government service portals.  
Analysed: **eGov.kz**, **enpf.kz**, and **gosuslugi.ru** as reference implementations.

---

## Project Goal

Identify functional gaps and usability issues in existing e-government service flows,  
then produce system analysis artefacts (SRS, BPMN process models, UML use case diagram)  
that could serve as a foundation for portal improvement.

---

## Scope

Five service categories were analysed:
1. Citizen registration & identity verification
2. Application submission (permits, certificates)
3. Application status tracking
4. Document storage & retrieval
5. Notifications (SMS / email / push)

---

## Deliverables

| Artefact | File | Description |
|---|---|---|
| System Requirements Specification | [`SRS.md`](./SRS.md) | 20 functional + 5 non-functional requirements |
| BPMN Process Model (AS-IS) | [`diagrams/application-submission-asis.drawio`](./diagrams/application-submission-asis.drawio) | Current-state application submission flow |
| BPMN Process Model (TO-BE) | [`diagrams/application-submission-tobe.drawio`](./diagrams/application-submission-tobe.drawio) | Improved target-state flow |
| Use Case Diagram | [`diagrams/use-cases.drawio`](./diagrams/use-cases.drawio) | 6 actors, 14 use cases |

---

## Key Findings

- **No unified status tracking** across service categories — citizens must check each service separately
- **Identity verification repeated** at every service entry point instead of using a single SSO session
- **No API contract** between document storage and application processing — integrations are point-to-point
- **Notification flow broken** in 2 of 3 portals analysed — users receive no confirmation after submission

---

## Tools Used

- **draw.io** — BPMN 2.0 process modelling, UML Use Case diagrams
- **Markdown** — SRS documentation
- **eGov.kz / enpf.kz** — source portals for AS-IS analysis

---

## How to View Diagrams

Open `.drawio` files directly on [diagrams.net](https://app.diagrams.net/) (File → Open from → Device),  
or view them rendered in GitHub (GitHub renders `.drawio` files natively).
