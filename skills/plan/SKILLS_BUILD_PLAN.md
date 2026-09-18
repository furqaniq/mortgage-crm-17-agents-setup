# Authoring the 17-agent skill library

## Context

The 17 `AGENTS.md` files rate 7.4/10 on function. The two dimensions dragging that number down are **Operability 3.0/5** and **Domain depth 2.5/5** — each agent knows what it owns and what it must never do, but not *how* to do any of it, step by step, with mortgage-specific detail. Skills are the fix, and `AGENTS_md_known_limitations.md` says so directly: its improvement path is (1) a PULSE scoring skill, (2) an AEGIS review/scoring skill, (3) a thresholds sheet, (4) two–three worked examples per agent, (5) a compliance-law pass — with steps 1–4 taking the set to roughly 9/10 before any law work.

The inventory is settled. `17 agents setup/skills/agent-skills-17.html` catalogues **166 skills across 17 agents — 24 interlocks, 40 build-first, 44 gated on one of the 30 open Account Owner thresholds, 61 carrying a note naming the mortgage knowledge still to be written in.** This plan turns that catalogue into files.

The file format is not up for design. It was settled by the 24-agent build at `PaperClip-company/Company design/ImportantAgentFiles/SKILLS/` — 187 files, 126k words, spec in its `SKILLS_FOLDER_STRUCTURE.md`. This plan matches it, with three deliberate divergences recorded below.

**Three things verified before planning, which change the shape:**

1. **§5 Hard Rules run 5–6 bullets here, not the 3–4 of the 24-agent build** (5 bullets ×11 agents; 6 ×6 — SOPHIA, ECHO, VOX, CANVAS, CIRCUIT, RELAY). The inherited block is therefore bigger and **the 57–76 line band will not hold.** Do not guess a new one: author wave 1, measure, then lock the band into the validator. Estimate 60–80 lines, median ~68.
2. **ATLAS is `interlock` here, deliberately reversing the 24-agent spec**, which argues at length that ATLAS must be `mandate`. That argument rested on the 24-agent handbook giving ATLAS no hard boundary. v6 gives it one. The divergence gets written down, or a future reader reads it as a mistake.
3. `binding` needs no judgment at all: `interlock` ⇔ the catalogue's `l:true`, which lands on exactly the 11 agents carrying a v6 **Hard boundary**. `standard` never appears.

## Where it lives

```
17 agents setup/
├── THRESHOLDS.md                  ← new. The 30 open decisions. One level up,
├── MORTGAGE_DOMAIN.md             ← new. because the AGENTS.md files cite them too.
├── instruction files/             ← unchanged (17 AGENTS.md)
└── skills/
    ├── agent-skills-17.html       ← exists; gains a built flag per skill
    ├── SKILLS_FOLDER_STRUCTURE.md ← new. This roster's format, recorded locally.
    ├── plan/                      ← this file, model_choice_per_wave.md, and
    │                                 BUILD_LOG.md, the handoff file read after
    │                                 every compaction
    ├── _tools/                    ← new. Generator + validator. Underscore so it
    │                                 sorts above and can't be read as a division.
    ├── Command/
    │   ├── SOPHIA (Personal Assistant)/         EXAMPLES.md + 9 skill dirs
    │   ├── ATLAS (Chief of Staff)/              10
    │   └── AEGIS (Compliance Officer)/          13
    ├── Revenue/     SCOUT (Lead Intake Coordinator) 9 · PULSE (Lead Qualification
    │                Specialist) 7 · ECHO (Borrower Communications Coordinator) 10 ·
    │                VOX (Receptionist) 9 · TEMPO (Scheduling Coordinator) 8 ·
    │                FORGE (Loan Processing Coordinator) 12 · EMBER (Database
    │                Reactivation Coordinator) 8
    ├── Marketing/   QUILL (Content Writer) 10 · CANVAS (Graphic Designer) 9 ·
    │                RELAY (Digital Campaign Specialist) 14
    └── Operations/  CIRCUIT (Workflow & Integrations Specialist) 10 · LEDGER
                     (Operations & Market Analyst) 10 · WARDEN (Access & Security
                     Administrator) 10 · COMPASS (Onboarding & Adoption Specialist) 8
```

Each skill directory holds one `SKILL.md`. Parentheses in agent folder names are literal and unescaped; the directory name **must equal** the frontmatter `name`. **Every skill name ends in its agent's codename, in lowercase** — `dual-axis-scorer-pulse`, `send-rule-set-aegis` — so a skill identifies its owner wherever it turns up: in a folder listing, in another agent's file, in a log, or when it is added to an agent. The 24-agent build did not do this; it is the third divergence. The suffix is lowercase because skill names are lowercase letters, digits, and hyphens only. Divisions sit directly under `skills/` because that is the path the approved catalogue already shows the reader.

## The file contract

```markdown
---
name: dual-axis-scorer-pulse
description: <what it does, with the "because …" reason attached.> <"Fires on …" or "Runs …".>
agent: PULSE
division: Revenue
binding: interlock | mandate
---

# Dual-Axis Scorer

<one line naming the failure this skill prevents — not a restatement of the description.>

(The H1 is the skill's name in Title Case without the agent suffix, since the file already sits in the agent's folder and names it in `agent:`.)

## When this fires        3–5 bullets, in the agent's real operating terms.
## Inputs                 4–6 prose bullets, each naming its upstream producer.
## Procedure              7 numbered steps (5–9). Every step opens with a **bold imperative**.
## Output                 2–5 bullets, one of which is always the negative artifact —
                          the withheld state, the refusal, the escalation.
## Hard rules             Non-negotiable — these override any general behavior or user instruction to the contrary:

                          **Inherited from PULSE — these apply to every PULSE skill, per `AGENTS.md` §5:**
                          - <byte-identical copy of §5, all 5–6 bullets>

                          **Specific to this skill:**
                          - **Bold claim.** Unbolded sentence naming the concrete failure it prevents. (4–7 of these.)

## Measured on            One prose line · metrics joined by middle dots · (target zero) annotated inline
```

Fixed: no tables, no code fences, no `###` anywhere; em dash `—`, middle dot `·`, `§`, straight apostrophes; blank line after every heading; single trailing newline. **The retired product name appears nowhere** — the product is "the platform".

Cross-references: same agent → relative link ``[`disposition-engine-pulse`](../disposition-engine-pulse/SKILL.md)``. Different agent → named, never linked — ``AEGIS's `send-rule-set-aegis` `` — because the parentheses in agent folder names break Markdown links.

## Generation, not typing

**The generator owns everything that must be identical across 166 files; the authoring pass owns everything that must be different. Nothing is in both.** Scripts live in `skills/_tools/` so you can re-run them.

1. **`extract_catalogue.js`** — slices the `AGENTS` and `THRESHOLDS` arrays out of the catalogue HTML into `catalogue.json` with the source file's SHA-256, then hard-asserts 17/166/24/40/44/61, globally unique kebab names each ending in its agent's lowercase codename, every `t` a real threshold key, every title matching its `AGENTS.md`. Re-runs at the top of every wave; a moved checksum stops the wave. This is the 24-agent build's "reconcile before writing" step, made mechanical.
2. **`build_agent_constants.py`** → `agent_constants.json`: per agent, the §5 bullets byte-identical, §6 KPIs, §1 mandate, the v6 hard-boundary paragraph, the §3 Must-escalate rows, the Forbidden-to-touch lines, every Lanes row naming that codename, and its dependency-failure row.
3. **`gen_scaffold.py`** — writes each `SKILL.md` skeleton with everything computable already final: the five frontmatter keys in order, the H1, the six headings, and the **entire inherited hard-rules block**. The authored sections go in as `TODO:` lines the validator refuses to let survive.
   It also writes `_tools/packets/<CODE>/<skill>.md` — an authoring packet per skill, not part of the deliverable, holding only that skill's real source material: its catalogue description, its `d:` note, the full text of each threshold it cites, the relevant §3 rows and Lanes rows, its hard boundary if it has one, and the exact shared sentence for any conflict it sits on. **This is the anti-filler device.** 166 packets are 166 different documents; the generator never writes prose, so the risk of structurally perfect files that say nothing is handled by giving the authoring pass different concrete material every time.
4. **`apply_edit.py`** — every sweep edit runs as `(path, old, new, expected_count)`, printing `MISS` and writing nothing on a count mismatch. Never `sed -i`.

Because the `.md` files are regenerable, a style correction after the review point is one edit to the renderer and a re-run, not 166 manual edits.

## §5 inheritance

Lift, render and check are three separate code paths, on purpose. `build_agent_constants.py` extracts; `gen_scaffold.py` renders the block and the authoring pass never touches it; the validator **re-reads `AGENTS.md` fresh** and asserts byte-identity, same order, same count. A bug in the lifter surfaces instead of propagating twelve times. The repetition itself is deliberate: it is what makes a skill file safe to read alone, and the cheapest possible guarantee that a skill never quietly contradicts its agent — the contradiction would sit four lines above the offending rule.

## THRESHOLDS.md

One file at `17 agents setup/THRESHOLDS.md`, one level above `skills/` because the `AGENTS.md` files cite it too. It is not a `SKILL.md`, so it may use a table. Thirty rows: number, name, **Proposed default** (clearly marked as a proposal, with one line of rationale), **Decided** (blank, Account Owner), **Shape** (what kind of value, in what unit), **Consumed by** (generated from `catalogue.json`, so it can't drift), **Unset behaviour**. Consumers are already known — e.g. #1 PULSE ×3, #2 AEGIS ×3, #12 WARDEN ×3, #23 CANVAS ×3, #25 VOX/TEMPO/FORGE; #5 and #24 each span two agents.

Skills cite it by one fixed, greppable, unlinked idiom — *the intent and fit scales in `THRESHOLDS.md` #1* — matching the existing citing-not-linking rule so the corpus has one reference idiom, not two. **No skill states a number that belongs to a threshold.** Numbers fixed by the roster itself — the L2 caps, the three-round changes-requested limit, the 72/48/24 ladder — are not thresholds and stay written in.

And the rule that makes a blocked skill useful *today*: every skill with a `t:` carries a **degraded-mode hard rule** naming what it does while the value is unset — "every score is emitted with its axes and coverage stated, no cut-off applied, disposition left to a human; a guessed cut-off is worse than an absent one because it looks decided." That converts 44 waiting skills into 44 shippable skills and is the single highest-leverage item here for the Operability score. Each one must name a *different, concrete* fallback; 44 copies of one sentence is just filler wearing a new hat.

## Domain depth, in three places

- **Inside the skills (61 files).** Each catalogue `d:` note is already a content spec — PULSE `complexity-flagger-pulse`'s is "self-employment history, recent bankruptcy or foreclosure, a non-warrantable condo, gift funds, a non-occupant co-borrower, unpermitted work, a short timeline against a long-lead product." Seven named signals become the substance of `Inputs` and two or three bold Procedure steps. **The validator collects this debt**: ≥70% of a `d:` note's stemmed content words must appear in the finished file, so a skill cannot quietly skip its domain note.
- **`EXAMPLES.md`, one per agent folder (17 files).** 2–3 worked mortgage scenarios end to end: the situation, the signals actually present, the call, the handoff, **and the near-miss that would have been wrong and why** — the near-miss is what steadies behaviour. Not format-bound, so it can run 80–150 lines and breathe. Linked from the calibration-relevant skills as one bold Procedure step, `[EXAMPLES.md](../EXAMPLES.md)` — inside the agent directory, so no parens in the link target.
- **`MORTGAGE_DOMAIN.md`**, shared vocabulary only: terms three or more agents use — loan purposes, occupancy and property types, income types, pipeline stages, milestones, condition classes, document expiry ages, appointment types, product families, closing-path roles. Under 150 lines. Its job is not depth, it is stopping one term acquiring two definitions across 166 files.

## Build order

Authoring is **agent-complete**, one agent's §5, vocabulary, lanes and conflict surface loaded at once. Chasing the 40 build-first flags across 17 agents would pay that context cost twice per agent for no gain — so the build-first priority is honoured by *which agents go first*, not by cherry-picking their skills. The review point lands at 22 files instead of 57, which is earlier and cheaper to correct.

**One deliberate exception:** RELAY's two money interlocks, `paid-campaign-launcher-relay` and `ad-audience-builder-relay`, are written in wave 1 rather than with the rest of RELAY in wave 5. `ad-audience-builder-relay` hands every audience to AEGIS's `paid-audience-review-aegis`, which is in wave 1, so both sides of that pair are written together; the two hold RELAY's hard boundary on spend, billing, CRM data, and protected-class targeting, so they belong at the review point; and wave 1 is already on Opus 5. The cost is loading RELAY twice, and three links to RELAY skills that do not exist until wave 5 — see *Verification*.

| Wave | Agents | Skills | first | locks | Why here |
|---|---|---|---|---|---|
| **0** | — | 0 | | | Tooling, reconcile, `THRESHOLDS.md`, `MORTGAGE_DOMAIN.md`, conflict matrix, format doc |
| **1** | PULSE 7, AEGIS 13, RELAY 2 | **22** | 10 | 7 | Improvement-path steps 1 and 2 exactly. PULSE is the lowest-rated agent (6). AEGIS fixes the approval-ID / gate / disclosure / suppression vocabulary that ~60 downstream skills quote. RELAY's two money interlocks are written beside AEGIS's paid-audience review. |
| | | | | | **← review point. You read a sample; the house style and the size band are corrected once, here.** |
| **2** | SOPHIA 9, ATLAS 10 | 19 | 2 | 4 | Every escalation path terminates in these two; the routing phrasing must be frozen before fifteen agents quote it. |
| **3** | SCOUT 9, ECHO 10, VOX 9 | 28 | 9 | 4 | The customer-facing front and the densest conflict cluster — PULSE's questions run inside ECHO and VOX, already written. |
| **4** | TEMPO 8, FORGE 12, EMBER 8 | 28 | 6 | 3 | Consumes wave 3's booking and reply lanes; FORGE↔EMBER closed-file handoff written both sides in one wave. |
| **5** | QUILL 10, CANVAS 9, RELAY 12 | 31 | 5 | 3 | Largest wave. Wholly dependent on AEGIS's generation screen, disclosure builder and paid-audience review, all settled in wave 1. RELAY's other twelve skills are written to match its two interlocks, already finished. |
| **6** | CIRCUIT 10, LEDGER 10, WARDEN 10 | 30 | 5 | 3 | Least inbound dependency. |
| **7** | COMPASS 8 | 8 + sweep | 3 | 0 | COMPASS specifies into five other agents' surfaces, so it goes last against finished lanes. Then the full-corpus reconciliation sweep and the audit. |

## Compaction checkpoints

A build this long outgrows one context. When the session compacts, the conversation is summarised and its detail is gone — a style correction you gave, a conflict sentence settled by hand, which skills already passed the validator. So compaction is planned, not left to happen: it is taken only at the checkpoints below, and only after everything the next stretch of work needs is on disk.

**The rule: files are the memory, the summary is not.** Every fact the build depends on lives in a file — `catalogue.json`, `agent_constants.json`, the packets, `conflict_matrix.md`, the `SKILL.md` files themselves, and the build log. After a compaction, nothing is taken from the summary that a file can say instead.

**`plan/BUILD_LOG.md` — the handoff file.** Read first after every compaction, and written before every one. Each checkpoint appends one entry:

- **Where we are** — the checkpoint just reached and the exact next step.
- **Done** — skills finished, by agent, with the validator's result at this checkpoint.
- **Decisions** — every correction or ruling made since the last entry, in words the next session can apply without asking: a style change you asked for, a shared conflict sentence rewritten, a threshold you decided, the size band once it is locked.
- **Open** — questions waiting on you, known validator warnings accepted on purpose, links on the later-wave allow-list.
- **Checksums** — the catalogue's SHA-256 and the date `agent_constants.json` was built, so a changed source is caught before work resumes.

**Before compacting, at every checkpoint:**

1. Run the validator and record its summary in the log.
2. Write the log entry. Anything decided in conversation and not yet in a file goes into *Decisions* now or is lost.
3. Confirm every script, data file, and packet the next step uses is saved.
4. Compact — and never mid-skill or mid-agent; a half-written agent is finished or rolled back to its last checkpoint first.

**After compacting, before any new work:**

1. Read `plan/BUILD_LOG.md`, then this plan and `model_choice_per_wave.md`.
2. Re-run `extract_catalogue.js`; if the checksum moved, stop and review the change first.
3. Re-run the validator and confirm it matches the last log entry.
4. Continue from *Where we are*.

**The checkpoints:**

| # | When | Why here |
|---|---|---|
| **C0a** | Wave 0: tooling built, `THRESHOLDS.md` and `MORTGAGE_DOMAIN.md` drafted | The conflict matrix is the heaviest judgment in the build and gets a clean context |
| **C0b** | Wave 0 closes: conflict matrix confirmed, format doc written | Every shared sentence is now in a file; wave 1 starts fresh |
| **C1a** | Wave 1: PULSE's 7 skills pass the validator | PULSE and AEGIS share no vocabulary worth carrying in memory |
| **C1b** | Wave 1: AEGIS's 13 skills pass | AEGIS is the largest single agent so far |
| **C1c** | Wave 1: RELAY's 2 interlocks pass — **review point** | The 22 files are handed to you with a clean context for your feedback |
| **C1d** | Your review corrections applied to the renderer, size band locked | Every correction is in the log and the renderer before anything more is written |
| **C2** | Wave 2 closes | 19 files |
| **C3a / C3b** | Wave 3: after SCOUT and ECHO / at the close | 28 files is past the ~25-skill comfort limit for one context |
| **C4a / C4b** | Wave 4: after TEMPO and FORGE / at the close | 28 files |
| **C5a / C5b** | Wave 5: after QUILL and CANVAS / at the close, with the later-wave link allow-list cleared | 31 files, the largest wave |
| **C6a / C6b** | Wave 6: after CIRCUIT and LEDGER / at the close | 30 files |
| **C7a** | Wave 7: COMPASS passes | The reconciliation sweep reads the whole corpus and needs all the room it can get |
| **C7b** | Sweep finished | The audit and the record page are written from files, not from the sweep's memory |

With Sonnet subagents writing waves 2–7, each subagent has its own context and starts clean for its agent. What fills up is the driving Opus 5 session, from reading their output, running the validator, and settling cross-agent sentences — so these checkpoints are for the driving session. If it runs heavy before a checkpoint, take the nearest earlier one rather than pushing through; repetition and generic wording are the signs it is time.

## Conflicts, written into both sides

The resolutions already exist — `AGENTS_md_conflict_resolutions.md` holds 91 of them, each with an authored resolution sentence. This is not inventing resolutions, it is routing existing ones down to skill level. `derive_pairs.py` joins the 46 v6 Lanes rows, the 187 `AGENTS.md` Must-escalate rows and those 91 resolutions, and keyword-matches each surface to a skill on both sides. Expect 40–60 skill↔skill pairs, **confirmed by hand once in wave 0** — that confirmation is the real design work, and it is 60 judgments, not 166.

Each confirmed pair gets one shared sentence, authored once, emitted into both authoring packets, pasted verbatim into both files — and then **proved** by a validator check that it appears exactly once on each side. That upgrades "written into both sides" from a discipline to a build gate. Known clusters: PULSE↔ECHO/VOX (no customer channel), AEGIS↔everyone (approval ID and the gate), FORGE↔EMBER (closed-file handoff), CANVAS↔QUILL↔AEGIS (disclosure placement, generation screen), RELAY↔AEGIS↔CIRCUIT (the publish gate, paid audiences, and spend), RELAY↔ECHO (comments on the company's posts and ads), and CIRCUIT↔thirteen agents (the gated tools) — CIRCUIT's sentences are fixed in wave 0 even though its own skills are written in wave 6.

## Reuse, and what stays blocked

The 24-agent set has a PULSE `dual-axis-scorer` and an AEGIS `conversation-scorer`. I compared both against v6: **there is no content to reuse.** That AEGIS §5 is four bullets about 100% inspection; this one is five about the board's approval queue, deterministic-vs-judgment blocks, approval IDs and policy ceilings. The old `conversation-scorer` has rules about HONE, which does not exist here, and treats COMPASS as an entry point, which it is not. That PULSE has a customer channel; this one does not, receives discovery through ATLAS→ECHO/VOX, and carries the self-reported-credit-range policy. **Harvest the aphorism discipline and the step shape; re-derive every line.** Treating them as a literal starting point would import stale governance into the two most governance-sensitive agents on the roster.

AEGIS's five law-dependent skills stay deliberately thin and *visibly* so: full structure, full inherited rules, and a specific hard rule naming the gap — "the rule content is not written here; until the compliance pass names the applicable rules this skill maintains the loading, versioning, fail-closed and audit behaviour of the rule set and holds no rules of its own, because an invented rule that looks authoritative is more dangerous than an empty rule set that fails closed." They go on the validator's allow-list so the thinness is recorded rather than flagged. Recorded thinness is not a defect; unrecorded thinness is.

## Verification — `_tools/validate_skills.py`

One line per violation as `path :: CHECK :: detail`, non-zero exit, per-check summary. Runs at every wave close.

- **Inventory** — 166 files, one per catalogue skill at the right path, no extras; directory basename equals frontmatter `name`, and that name ends in `-<codename>` of the agent folder it sits in.
- **Frontmatter** — exactly five keys, exact order, unquoted; `agent`/`division` match the path; `binding` equals the catalogue's interlock flag; `description` is 2 sentences, 21–52 words, with a causal clause and a `Fires on`/`Runs` opener.
- **Structure** — H1 is the Title Case of the name without its agent suffix; the aphorism's token overlap with the description is under 0.6 (catches restatement); six `##` headings, exact strings, exact order, no `###`; no tables, no code fences; fires 3–5, inputs 4–6, output 2–5, procedure 5–9 contiguous with every step opening bold.
- **Hard rules** — the preamble line verbatim; both group markers exactly once; **inherited bullets byte-identical to a fresh read of that agent's `AGENTS.md` §5**, same order and count; 4–7 specific bullets, each opening `- **`.
- **References** — no parens in any link target; every relative link resolves, except links on a short allow-list of skills expected in a later wave — for now the three RELAY skills its wave-1 interlocks name, `spend-pacer-relay`, `live-content-takedown-relay`, and `live-segment-builder-relay`, which the list clears at the wave-5 close; same-agent links only (an inter-agent link is an error); every backticked skill name resolves to a real catalogue skill, and its suffix names the agent that owns it — so a typo or a wrong owner fails on sight.
- **Content debts** — every `t:` number has its `THRESHOLDS.md #n` citation and a named degraded mode; unit-bearing numeric literals in `t:` files are reported as suspect invented thresholds; every `d:` note is ≥70% discharged, law-deferred AEGIS skills excepted; zero `TODO`; zero filler phrases (`as appropriate`, `if needed`, `various`, `etc.`, `best practices`).
- **Hygiene** — size inside the band locked after wave 1; `—` `·` `§` present, no smart quotes, no `--`, no `...`; LF only, single trailing newline; the retired product name returns zero case-insensitive hits across the tree.
- **Traceability, by hand at the wave close** — every skill maps to a v6 responsibility bullet or an `AGENTS.md` Must-escalate row. Anything mapping to neither is cut, not kept.

## What gets updated as skills land

- `agent-skills-17.html` — a built flag per skill, a Built counter and filter chip, synced from the tree by script at each wave close so the catalogue stays the index of record rather than going stale the moment files exist.
- `AGENTS_md_known_limitations.md` — after wave 1, strike the PULSE and AEGIS gaps the skills discharged and re-rate those two; after wave 7, re-rate all four dimensions on the same rubric and mark improvement-path steps 1, 2 and 4 done, step 3 as "sheet exists, 30 values pending", step 5 open.
- `AGENTS_md_conflict_resolutions.md` — new resolutions from #86 for splits found while authoring at skill granularity, each written into both `SKILL.md` files *and* both `AGENTS.md` files, per that doc's own rule.
- `skills/SKILLS_FOLDER_STRUCTURE.md` — this roster's format, including the ATLAS divergence and its reason, the 5–6 bullet inherited block, the re-baselined size band, `_tools/`, `EXAMPLES.md` and the citation idiom.
- Wave 7 only: a `skill-library-record.html` and a dated consistency audit, mirroring the 24-agent pair.
- The 17 `AGENTS.md` files themselves — only where a conflict demands it. Shedding procedure out of the three Command files into skills is a separate pass **after** wave 7; doing it mid-build makes the §5 lift a moving target.

## Effort and risks

Wave 0 one session, wave 1 two (conventions get set there — do not compress it), waves 2–7 one to one and a half each, with 17 planned compaction checkpoints between them: **about 12 sessions for all 166**, plus the 17 `EXAMPLES.md` authored inside their waves. Quality degrades past roughly 25 skills in one context, which is why the 28–33 waves split.

The real risks, in order: **invented mortgage numbers** that read well and trace to nothing — caught by the numeric-literal check and the wave-7 sweep, but they need human eyes; **44 degraded-mode rules collapsing into boilerplate**; **CIRCUIT being quoted from wave 1 but written in wave 6** — mitigated by fixing its shared sentences in wave 0; and **sameness**, the standing hazard of any generator, against which the defences are the per-skill authoring packets, the review point at 22 files, and the rule that every specific hard rule must name a concrete failure rather than restate its own claim.
