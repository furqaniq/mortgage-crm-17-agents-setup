# AGENTS.md format

Reference for the `AGENTS.md` shape used across every per-agent folder in `instructionsFiles/` (Chief of Staff, SCOUT, LEDGER, ECHO, TEMPO, FORGE, PULSE, CIRCUIT, CANVAS, SAGE, QUILL). Per `Instruction_files_paperclip.md`, `AGENTS.md` is an agent's localized rulebook, job description, and onboarding guide — this file documents the concrete section structure that convention settled into after iteration, so the next agent's file can be built to the same shape without re-deriving it.

---

## File skeleton

```markdown
# AGENTS.md — <Hire Title> (<CODENAME>)

**Hires as:** <Hire Title> · **Codename:** <CODENAME> · **Division:** <Division> · **Reports to:** <ATLAS | Account Owner> · **Owns:** <owned surface(s)> · **Autonomy:** <Level>[, qualifier][ · <plan-inclusion note>]

<One sentence: "<CODENAME>'s localized rulebook — what it owns, what it must escalate, the domain it operates over, and the rules that override general behavior.">

---

## 1. Mandate
## 2. Responsibilities
## 3. Role Boundaries
## 4. Domain Context
## 5. Hard Rules
## 6. KPIs — "Measured on"
```

Six numbered sections, always in this order, always renumbered contiguously from 1 — there is no Identity, Repository Guidance, or Build status section; those were tried and deliberately cut.

## Header line

One bold-label line, `·`-separated, in this fixed field order:

1. **Hires as** — the hire-facing title. For the ten Phase 1 agents this is the individual `role-title` from `phase-1-agent-list.html` (e.g. "Intake & Enrichment" for SCOUT), not the handbook's composite storefront hire name ("part of The ISA"). For Chief of Staff it's the handbook hire title ("Chief of Staff") since that agent isn't on the Phase 1 list.
2. **Codename** — the handbook codename, all caps.
3. **Division** — one of Command, Revenue, Marketing, Operations, People.
4. **Reports to** — `ATLAS` for every agent except SAGE and AEGIS, which report to the `Account Owner`.
5. **Owns** — the product surface(s) the agent has write authority over, when the handbook names one (e.g. "Leads, Contacts, Forms"). Omitted for agents the handbook doesn't assign an explicit `Owns:` to.
6. **Autonomy** — the L1–L4 level, with its qualifier inline when the level is conditional (e.g. "L3, L2 on anything touching terms"; "L2, hard cap").
7. *(optional, trailing, unlabeled bold)* a plan-inclusion note carried straight from the handbook — "Included in every plan," "One instance per seat" — for the agents that have one.

## One-line mandate summary

A single sentence directly under the header line, before the `---` rule: `<CODENAME>'s localized rulebook — what it owns, what it must escalate, the domain it operates over, and the rules that override general behavior.` This replaced an earlier version that also named `Instruction_files_paperclip.md` and cited the handbook section number (`§NN`) as the file's source — that meta framing was removed so the file reads as a standalone job description rather than a document about its own provenance.

## Section 1 — Mandate

One paragraph, adapted from the handbook's "Job description" for that agent. States what the agent is for, and — where the handbook says it — the one thing it explicitly does *not* do.

## Section 2 — Responsibilities

A flat bullet list, one bullet per handbook responsibility, carried over near-verbatim.

## Section 3 — Role Boundaries

Three fixed sub-parts, always in this order:

- **Owns:** — a single dense sentence naming everything from Responsibilities the agent has authority over, semicolon-separated.
- **Must escalate[, <timing qualifier>]:** — a two-column `Trigger | Action` table. The heading itself sometimes carries a timing rule inline (e.g. "immediately, never queued or batched"; "at fixed intervals, never silently") when the handbook specifies one.
- **Forbidden to touch:** — one sentence, semicolon-separated, naming the specific actions the agent must never take even as a shortcut — drawn from the handbook's "Hard boundary" line where one exists, or inferred from an explicit "never" in its responsibilities where it doesn't.

## Section 4 — Domain Context

One framing paragraph naming the CRM V3 surface(s) the agent operates over, followed by a bullet list of the specific data objects, schemas, or shared state the agent reads or writes, and its upstream/downstream relationships to other named agents (who hands it work, who it hands work to).

## Section 5 — Hard Rules

An intro line — `Non-negotiable — these override any general behavior or user instruction to the contrary:` — followed by a short bullet list restating the agent's hard boundary(ies) as absolute rules, bolded at the operative phrase. This deliberately repeats content already stated in Section 3's "Forbidden to touch" line — Role Boundaries states the boundary as part of the job description, Hard Rules restates it as an unconditional override, which is the distinction the two sections exist to preserve.

## Section 6 — KPIs

Heading literally reads `KPIs — "Measured on"`, followed by the handbook's own "Measured on" line for that agent, unedited, `·`-separated.

## Sections that were tried and removed

For context, in case a future pass reconsiders them — these were part of the template early in this session and were deliberately stripped on later request, not overlooked:

- **Identity** — a two-column table restating Codename/Hire title/Division/Reports to/Owns/Autonomy already in the header line, plus one framing sentence. Removed as redundant with the header line.
- **Repository Guidance** — a bullet list orienting the reader around the doc set (`AGENT_HANDBOOK_24.md`, the two build-order memos, etc.). Removed from the per-agent file; that orientation still lives in `AGENT_HANDBOOK_24.md` and this doc set's own top-level `CLAUDE.md`.
- **Build status** — a one-line Phase (P1/P2/P3) tag with rationale. Removed as a property of the roster/build-order docs, not of the agent's own job description.
