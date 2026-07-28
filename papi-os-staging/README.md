# Papi OS

Papi is a multi-tenant AI hospitality operating system built by **Casa Julia Group**. Each venue is a tenant. Papi connects a venue's real operation (POS, menu, schedule, reviews, guest messages), measures it against the Casa Julia Standard, and every day finds the gap, recommends the fix, and helps install the discipline.

**Operating principle (locked):** AI recommends, a human approves, the backend enforces. Nothing sends to a guest and no booking confirms without a human tap.

This repository is the home for the Papi OS build files, specifications, and documentation.

## Start here

- **[Papi-BUILD-HANDOVER.md](./Papi-BUILD-HANDOVER.md)** — the master orientation document. Read this first; it maps every other file, states what wins when two conflict, and flags what is IP-gated until the NDA is signed.

## The engine

Five-step engine, one discipline, every domain:

1. **Ingest**
2. **Diagnose** — Red / Amber / Green against a written standard
3. **Recommend**
4. **Install** — the fix becomes an owned task
5. **Prove** — rolls into the Health Score, tracked over time

## Non-negotiable build rules

- Human gate on every send.
- Tenant isolation is an allowlist, never a loose default.
- Payments are real or they hard-fail.
- The concierge must auto-fire on every inbound message via the live webhook path.
- POS is a dynamic connector layer.
- Music/streaming playback runs through a commercially licensed source.
- IP gate: the Papi brain prompt, the CJG/CJS standards, and full client files do not change hands until the NDA and IP assignment are signed.

## Build order

1. Concierge auto-fire wired to the live inbound path (highest priority).
2. Real payments (Stripe, Xendit incl. Indonesian QR, PayPal).
3. Tenant isolation hardening + retire the shared demo credential.
4. The module scope in the Consolidated Build Scope.

---

*Prepared by Randy Davila, Casa Julia Group.*
