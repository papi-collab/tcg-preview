# Papi OS — Build Handover
### Master orientation for the developers (NuaWeb) and any Claude Code session working on the build
*Casa Julia Group. Prepared by Randy Davila. Last updated 28 July 2026.*

---

## 0. How to use this document

This is the single entry point to the Papi build. Read this first, then open the files it points to, in the order below. Every path is relative to the folder root:

```
~/Desktop/CJG_Pack/
```

**If you are a Claude Code session:** treat this file as the map. The governing scope is a PDF (`Papi/PapiOS-Consolidated-Build-Scope.pdf`); the build rules and module list live there. This handover tells you what each file is, what wins when two conflict, and what must not be touched or shared until the NDA is signed.

**Read order:** 1) this file, 2) the Consolidated Build Scope, 3) the Papi Brain Specification, 4) the Module Manifest, 5) the Channel Build Spec and the Sound Module Spec, 6) the CJG Standard Library (IP-gated, see Section 4).

---

## 1. What Papi is

Papi is a multi-tenant AI hospitality operating system. Each venue is a tenant. It connects a venue's real operation (POS, menu, schedule, reviews, guest messages), measures it against the Casa Julia Standard, and every day finds the gap, recommends the fix, and helps install the discipline. Built for Casa Julia Group's own clients and resold as its own SaaS.

Operating principle, locked: **AI recommends, a human approves, the backend enforces.** Nothing sends to a guest and no booking confirms without a human tap. Missing data shows as "incomplete," never guessed.

## 2. The engine and the three standards (canonical language)

**Five-step engine, one discipline, every domain:** Ingest, Diagnose (Red/Amber/Green against a written standard), Recommend, Install (the fix becomes an owned task), Prove (rolls into the Health Score, tracked over time). Use these five verbs everywhere. Do not reintroduce "Grade / Route / Roll Up."

**Three standards, one engine, kept strictly isolated so no score contaminates another:**

1. Venue Operating Standard — Revenue, Profit, Operations, People, Guest. Continuous, feeds the live Health Score.
2. Digital Growth Standard — the paid entry diagnostic; can run on a prospect before they sign.
3. Deep Inspection Standard — periodic physical walkthrough, every item carries a Responsible Role.

## 3. Non-negotiable build rules

These are locked. They are both safety model and sales line.

- **Human gate on every send.** AI drafts; a person confirms. Auto-send may unlock per venue later, once trust is earned.
- **Tenant isolation is an allowlist**, never a loose default. Cross-tenant knowledge leakage is a release blocker (it happened in the current build; reproduce, fix, make it an acceptance test).
- **Payments are real or they hard-fail.** No stubbed links, no fake URLs, no refund that moves ledger state without moving money.
- **The concierge must auto-fire** on every inbound message via the live webhook path. The current build's auto path is a stub (923 inbound → 4 drafts). This is the single most important functional fix.
- **POS is a dynamic connector layer.** Connect to whatever POS a venue already runs (API/OAuth where one exists, email-report fallback where it does not). Moka live; Lightspeed prioritized for the beta. Stays open-ended until Papi's own POS ships.
- **Music/streaming licensing.** Consumer Spotify/Apple/YouTube personal accounts are not licensed for commercial venue playback. Papi curates and recommends; the venue plays through a commercially licensed source (e.g. Soundtrack Your Brand).
- **IP gate.** The Papi brain prompt, the CJG/CJS standards, and full client files do not change hands until the NDA and IP assignment are signed and the demo credential is rotated. See Section 4 for which files are gated.

## 4. Build order

1. Concierge auto-fire wired to the live inbound path (highest priority).
2. Real payments (Stripe, Xendit incl. Indonesian QR, PayPal).
3. Tenant isolation hardening + retire the shared demo credential.
4. Then the module scope in `PapiOS-Consolidated-Build-Scope.pdf`, Section 4, delivered across the engagement.

---

## 5. File manifest

Root: `~/Desktop/CJG_Pack/`. Status key: **LIVE** = current, use it. **GATED** = do not share with NuaWeb until NDA signed. **REF** = reference/superseded, context only.

### A. Start here — governing build docs

| File | Location | What it is | Status |
|---|---|---|---|
| Papi-BUILD-HANDOVER.md | `Papi/` | This document | LIVE |
| PapiOS-Consolidated-Build-Scope.pdf | `Papi/` | THE governing scope. Merges current build + NuaWeb proposal + operator review. Supersedes the module list in the proposal | LIVE |
| Papi-Rebuild-Module-Manifest.md | `Papi/Build_Specs/` | Port / Fix / Wish lists so nothing from the old build is quietly dropped | LIVE |
| CJG-Exec-Meeting-GapLog-and-Manifest-Additions.md | `Papi/Build_Specs/` | Gaps surfaced in the Dan/Dorian exec review, folded into scope | LIVE |
| papi-os-channel-build-spec.md | `Papi/Build_Specs/` | WhatsApp/Instagram/Meta channel architecture on the draft-for-approval engine | LIVE (arch) |
| Papi-Sound-Module-Spec-and-Wireframe.md | `Papi/` | The new music/BPM module: Q&A flow, engine, streaming, data model, 6 screen wireframes | LIVE |
| Papi-QA-Checklist-Lovable.md | `Papi/Build_Specs/` | Five things to verify before trusting the build at scale | REF (prior build) |

### B. The Papi brain and the standard — GATED (post-NDA only)

| File | Location | What it is | Status |
|---|---|---|---|
| CJG_Claude_Master_Prompt_v2.txt | root | The Papi persona + brain: three divisions, the engine, the three standards, Music Control Theory, CJD | GATED |
| Papi-Brain-Specification.md | `Papi/Build_Specs/` | The portable "constitution" any Casa Julia OS runs on, stack-independent | GATED |
| CJG-Standard-Library.md | `Papi/Build_Specs/` | The operating standard Papi diagnoses every venue against. Internal, do not distribute | GATED |
| CJG-Music-Control-Theory.md | `Papi/` | The BPM room-control standard behind the Sound module | GATED |

### C. Product and positioning

| File | Location | What it is | Status |
|---|---|---|---|
| Papi-Capabilities.pdf | `Papi/` | The 2-page capabilities sheet (12 capabilities incl. Sound; POS-agnostic) | LIVE |
| Papi-Pitch-1-One-Line.pdf | `Papi_Drive_Upload/` | One-line pitch | LIVE |
| Papi-Pitch-2-30-Second.pdf | `Papi_Drive_Upload/` | 30-second pitch | LIVE |
| Papi-Pitch-3-2-Minute.pdf | `Papi_Drive_Upload/` | 2-minute pitch | LIVE |

### D. Commercial / investment

| File | Location | What it is | Status |
|---|---|---|---|
| Papi-Investment-Proposal-Jordie.pdf | `Papi_Drive_Upload/` | Investor proposal (250k / 10–15% / 2.5M). Awaiting advisor input on structure | LIVE (draft terms) |
| Papi-Investor-Meeting-Prep.pdf | `Papi/` | Internal walk-in playbook for Jordie & Pablo. Do not circulate | GATED (internal) |
| Papi-Budget-and-Projections.xlsx | `Papi_Drive_Upload/` | 4-tab model: assumptions, market, 36-mo projections, scenarios. Awaiting advisor input | LIVE (draft) |

### E. Legal — sign before deep IP moves

| File | Location | What it is | Status |
|---|---|---|---|
| CasaJulia-NDA-and-IP-Assignment-Rev3.pdf | `Papi_Drive_Upload/` | The NDA + IP assignment to sign with NuaWeb | LIVE |
| CasaJulia-NDA-Bilingual-EN-ID.pdf | `Papi_Drive_Upload/` | Side-by-side EN/ID version | LIVE |
| CasaJulia-NuaWeb-Schedule-A-SOW.pdf | `Papi_Drive_Upload/` | Statement of work referencing the build scope | LIVE |

### F. Operating standard — Dorian ingestion (adopted enhancements)

| File | Location | What it is | Status |
|---|---|---|---|
| Dorian-Ingestion-Map.xlsx | `Papi/Standard_and_Ingestion/` | Triage of Dorian's 13 files against the CJG standard | LIVE |
| Dorian-SOP-Index-Mapped-to-CJG.md | `Papi/Standard_and_Ingestion/` | His SOP library mapped to our standard; what to adopt vs protect | LIVE |
| CJG-Standard-Enhancements-from-Dorian.md | `Papi/Standard_and_Ingestion/` | The three new domains adopted: Maintenance & Assets, Security, IT & Systems, plus supplier scorecard + SOP governance | LIVE |
| Papi-Nightly-Report-Template.md | `Papi/Standard_and_Ingestion/` | The nightly report template (feeds Section 4 reporting) | LIVE |

### G. Reference client — NDC concierge (live CJS build)

| File | Location | What it is | Status |
|---|---|---|---|
| NDC-Concierge-Handover.zip | `Papi_Drive_Upload/` | The Nico Dives Cool concierge: README, handover, live system prompt, inbox fix plan | REF (live client) |

---

## 6. Pending inputs — do not start these until the inputs land

- **Dan Segall (chef partner):** recipe and true-costing spreadsheet, menu-writing style rules and word lists, food-safety standards. When these arrive, the Papi Master Prompt gets rewritten in ONE pass to fold in Dan's kitchen material together with Dorian's three new domains. Do not piecemeal-edit the prompt before then.
- **Investor advisor:** feedback on the deal structure (priced round vs. convertible) and on the projections. When it lands, the proposal, the meeting prep, and the model get updated together so all three stay in lockstep.

## 7. Mirror status

The text/analysis docs are mirrored to the CJG Notion hub and the Google Drive folder "Casa Julia — Papi & CJG (Mirror)". The designed binaries (PDFs, xlsx) are dragged in manually; `Papi_Drive_Upload/` is the staging set. After today's edits, the Drive copies of the Build Scope and Capabilities are stale and should be re-dragged, and the new files (Master Prompt v2, Sound spec, Music Control Theory, this handover) added.

## 8. One-line summary for a new dev

Build the platform in `PapiOS-Consolidated-Build-Scope.pdf`. Concierge auto-fire and real payments first. Tenant isolation is an allowlist. AI drafts, a human confirms. POS is a dynamic connector. Nothing gated moves before the NDA is signed.
