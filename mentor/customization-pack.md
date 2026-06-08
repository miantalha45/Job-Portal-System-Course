**MENTOR ONLY — do not share this file with the mentee.**

> This file lives outside the mentee's numbered reading path on purpose. Nothing in here — no menu, no option list, not the word "personalisation" — ever appears on the mentee's pages. The mentee sees only the *result* of your choices, woven into their intro as one natural sentence and carried through the build.

# Job Portal — Customization Pack

## 1. How personalisation works here

The core course teaches a **generic job portal**: companies post jobs, candidates browse the whole board and shortlist across companies, one application per job, snapshots at apply time, slow work in background workers. That core is the same for everyone.

What makes each mentee's build unique is what *you* assign them:

- **1 domain** — the kind of hiring the portal serves. This is the important one: it must change real schema fields, validation, screening, search, and gating — not just the title.
- **1 design language** — how the screens should look and feel.
- **5 reading themes** — mixed kinds, with at least one off-syllabus, to deepen the work.

The mentee then **names their own portal**. Two mentees on the same course should never be able to hand in the same build: different name, different domain-driven schema, different look, different reading. If you assigned the same domain to two mentees by accident, their job tables, validation, and filters would look near-identical — so vary the domain first.

Where you don't have a strong preference, random-recommend one of each from the menus below and confirm it with the mentee.

## 2. The domain menu

Pick **one**. For each domain below: a one-line description, then the concrete *"how it changes real decisions"* — the schema fields / JSONB attributes, validation rules, screening specifics, search filters, and any gating it introduces. The test (guide §5): if swapping the domain wouldn't change the schema or features, it's only a rename — so each entry here genuinely changes the build.

### A. Remote-first tech

A board for remote engineering, design, and product roles at distributed companies.

How it changes real decisions:
- **Fields / JSONB attributes:** salary band (min/max + currency), required timezone-overlap window, seniority level, tech-stack / skill tags, employment type (full-time / contract), portfolio or GitHub link on the candidate.
- **Validation:** salary min ≤ max; timezone window expressed as UTC offsets; skill tags from a controlled vocabulary so search stays clean.
- **Screening:** free-text and multiple-choice questions per job (e.g. "years with Postgres?", "are you within UTC-2 to UTC+3?").
- **Search filters:** by skill tag, seniority, salary floor, and timezone-overlap with the candidate.
- **Gating:** none beyond standard auth.

### B. Healthcare / clinical staffing

A board for nurses, physicians, and allied-health roles, where who can legally work a shift is regulated.

How it changes real decisions:
- **Fields / JSONB attributes:** required license type, **license number + expiry date** on the candidate, specialty/credential list, shift pattern (day/night/rotating), facility type, hourly rate.
- **Validation:** license expiry must be in the future at apply time; license number format checked per type; shift selection required.
- **Screening:** credential and compliance questions (vaccination status, background-check consent).
- **Search filters:** by specialty, shift type, license type, and credential-verified status.
- **Gating (special):** **credential verification gates the apply action** — a candidate whose license is missing, expired, or unverified is blocked from submitting (a real branch the generic course doesn't have). Roles are **shift-based**, so a job can list multiple dated shift slots.

### C. Skilled trades / local

A board for electricians, plumbers, carpenters, and similar, where work is local and certified.

How it changes real decisions:
- **Fields / JSONB attributes:** required certifications / licenses (trade card numbers), job site **location (lat/long + postcode)**, **day-rate** instead of (or alongside) annual salary, availability windows / start date, tools-provided flag.
- **Validation:** certification required for gated trades; location must geocode; day-rate range sane.
- **Screening:** "do you hold X certification?", "can you start within N days?", "do you have own transport/tools?".
- **Search filters:** **location-radius search** ("within 20 miles of me"), certification held, day-rate range, availability window overlap.
- **Gating:** apply blocked when the role requires a certification the candidate hasn't recorded.

### D. Creative / design freelance

A board for designers, illustrators, writers, and video editors hired per project.

How it changes real decisions:
- **Fields / JSONB attributes:** **project/gig-based postings** (deliverables, duration, fixed budget or rate range) rather than permanent posts, required disciplines, **rate card** on the candidate, portfolio links/media.
- **Validation:** budget or rate range required; portfolio URL required to apply; project duration bounded.
- **Screening:** portfolio-centric — "link three relevant pieces", "what's your day rate for this scope?".
- **Search filters:** by discipline, budget range, project duration, and remote/on-site.
- **Gating:** apply requires a **portfolio** present on the candidate profile (a profile-completeness gate the generic course lacks).

### E. Hospitality / seasonal

A board for restaurants, hotels, and events hiring high-volume, short-term staff.

How it changes real decisions:
- **Fields / JSONB attributes:** **high-volume short-term roles** (many openings per posting → a vacancy-count field), **start-date window** and end date, shift availability, location, hourly/tip-inclusive pay.
- **Validation:** start-date window must be valid and future-ish; vacancy count ≥ 1; right-to-work confirmation.
- **Screening:** availability calendar, "can you work weekends/nights?", language/service experience.
- **Search filters:** by start-date window, location, role type, and shift availability.
- **Gating:** none special, but the **one-application-per-job rule meets multi-vacancy postings** — a recruiter fills many seats from one posting, which changes how applications are grouped and reviewed.

### F. Academic / research

A board for university and lab roles — postdocs, lecturers, research fellows.

How it changes real decisions:
- **Fields / JSONB attributes:** **fixed-term post** (contract length, funding source / **grant** reference), required **publications** record on the candidate, research area, degree requirements, teaching load.
- **Validation:** contract length and funding fields required for fixed-term posts; degree level from a controlled list.
- **Screening:** "list relevant publications", "name your funding body", references-on-request.
- **Search filters:** by research area, contract length, degree level, and funded/unfunded.
- **Gating:** apply may require a minimum publications count or a CV plus a research statement attachment.

(Need a seventh? Education/tutoring, public-sector/government, or logistics/driving all change real fields too — apply the same test before adding one.)

## 3. The design-language menu

Pick **one**. This sets how the mentee describes and styles screens; it is not a design-systems lecture.

- **Minimal editorial** — generous whitespace, calm serif/sans pairing, content-first (Linear / Vercel feel).
- **Bold maximalist** — large type, strong colour blocks, confident and loud.
- **Swiss grid** — strict columns, tight alignment, restrained palette, very ordered.
- **Neo-brutalist** — hard edges, visible borders, raw and high-contrast.
- **Soft pastel** — rounded corners, muted colours, friendly and approachable.
- **Dark mono** — dark surfaces, monochrome accents, dense data-tool aesthetic.

## 4. The reading-themes menu

Assign **five total**, mixing the *kinds* below, with **at least one off-syllabus** (guide §5). Examples drawn to fit a job portal:

1. **Concept deep-dive** — e.g. how PostgreSQL JSONB indexing actually works (the domain-attributes field leans on this).
2. **Real-world post-mortem** — an outage write-up about a background-job queue backing up or a cache going stale.
3. **X vs Y comparison** — cursor vs offset pagination, or BullMQ vs a database-backed queue.
4. **Opinionated best-practice piece** — a strong take on multi-tenant data isolation, or on idempotency keys.
5. **One off-syllabus topic** (choose one): observability / structured-logging culture · accessibility (the candidate-facing forms are a great target) · infrastructure-as-code · an event-driven paradigm (so they understand what this course deliberately *didn't* use) · design systems.

## 5. How to assign

1. Pick one domain, one design language, and five reading themes — or random-recommend one of each and confirm with the mentee.
2. Confirm the **project name** with the mentee (they choose the brand; you just lock it in).
3. Record the choices in a short assignment note you hand to the mentee. Keep it to the fill-in line below — do not hand over this pack.

Copy-and-fill template:

```
Project name: ____ · Domain: ____ · Design language: ____ · Readings: ____, ____, ____, ____, ____
```

## 6. How the assignment reaches the mentee

**Crucial: the mentee-facing chapters (01–05 and the build chapters) are written domain-neutral. They contain NO "domain," "Apply your domain," or "domain-specific" language at all** — the personalization mechanism is invisible to the mentee. The chapters teach a clean, generic job portal and never reveal that the project is customized to a domain. So nothing in the course text will prompt the mentee to apply a domain; **that's your job.**

You convey the assigned domain, the project framing, and the visual style to the mentee **directly** — in the assignment brief, the kickoff conversation, and the mentee's own README — **not via the course text.** Never as a menu, never with the word "personalisation," never as "this was assigned." It reaches them as **one natural sentence** they fold into their README — for example:

> "You're building Shiftline, a clinical-staffing job portal, in a calm dark-mono style — credentials matter here, so a candidate's license is checked before they can apply."

That's it. The mentee's intro tells them, in plain prose, to name their own portal and make the build genuinely theirs (see `01-introduction/01.01-what-youre-building.md`, the "Make it yours" section) — but it says nothing about a domain. Your one sentence, in the brief/README, is what supplies the domain, framing, and style. The mentee carries that through everything they build.

## 7. Where the domain matters — brief your mentee at these points

Because the chapters no longer prompt the domain themselves, **you must tell your mentee to apply their assigned domain at each point below.** Build them into your brief/kickoff and spot-check them in review:

- **Ch 9 — Modeling job postings (JSONB attributes):** tell your mentee to model *their* domain's attributes here, not the generic salary/skills default.
- **Ch 10 / splitting in Ch 46 — Applications & screening answers:** tell them the screening questions and any domain gating (credential check, portfolio requirement) belong here.
- **Ch 32 — Posting & editing jobs:** tell them validation must enforce their domain's rules (license expiry future-dated, day-rate range, vacancy count, etc.).
- **Ch 39 — Search & filtering:** tell them the filters must be domain-appropriate (location-radius for trades, shift type for clinical, budget for freelance).
- **Ch 34 / 50 / 53 — the panels (Company, Applicant, Admin):** tell them the UI must reflect the assigned design language.

When reviewing or at the viva, confirm the domain genuinely shaped the schema and features. If the mentee's build would be identical with any other domain, the personalisation didn't land — send them back to the points above.
