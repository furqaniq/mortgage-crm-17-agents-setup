# AGENTS.md known limitations — 17-agent roster

What still holds the 17 `AGENTS.md` files back from doing their jobs well, recorded for a later improvement pass. None of these is a conflict between files — those are settled in `AGENTS_md_conflict_resolutions.md`. These are gaps in *how* each agent does its work.

**Last rating: 7.4 / 10 for function** (average of the per-agent scores below) and **7 / 10 for conflicts** (0 high, about 13 medium, about 15 low after merging two audits), compliance law excluded — an independent re-audit of v6 and all seventeen files by seven reviewers who had not seen the earlier fixes. The fourth consistency pass (`AGENTS_md_conflict_resolutions.md` #66–85) then fixed every conflict found and the items marked *fixed* below. Not re-rated since.

| Dimension | Score | Meaning |
|---|---|---|
| Fidelity to job description | 5.0 / 5 | The file matches the v6 job description |
| Lanes | 3.8 / 5 | Ownership, handoffs, and enforcement are unambiguous across the set |
| Operability | 3.0 / 5 | An agent could do the job from the file alone |
| Domain depth | 2.5 / 5 | Mortgage-industry knowledge other than law |

The previous rating (7.9 and 8) came from a review that checked wording across files; this one traced each handoff and each rule to its mechanism, which found older gaps rather than new ones. Compare the two with that in mind.

The files are strong rulebooks — what each agent owns and must never do — and weaker operating manuals. Nearly every limitation below is a missing definition, threshold, procedure, example, or piece of mortgage operating knowledge.

---

## 1. Per-agent limitations

| Agent | Score | Limitations |
|---|---|---|
| PULSE | 6 | No scoring scale, intent or fit signals, or disposition thresholds; no complexity-signal list (self-employed history, recent bankruptcy or foreclosure, non-warrantable condo, gift funds, non-occupant co-borrower); no scenario math (which cost components, default assumptions); no re-score trigger; "outcome" undefined for the LEDGER feed; no rule for which dispositions need a human's confirmation under the L2 cap. *Fixed:* rate source for scenarios, scenarios never reach a customer |
| COMPASS | 7 | No shadow-mode definition or exit criteria; no 30-day milestones; "stopped using" undefined; the interview has no mortgage content (channel, licensed states, product mix, LOS, point-of-sale and pricing engine, lead vendors, roles); voice-platform phone setup has no owner. *Fixed:* LEDGER feed, readiness to the board, full migration routes, SMS registration, hire-request limits |
| ECHO | 7 | Ten intents listed but not defined; no opt-out phrase list; "distress" undefined; no per-intent actions for hot, reschedule, auto-reply, unclear; no language fallback when the library lacks the customer's language; no mortgage objection categories. *Fixed:* complaint flags, quiet hours, exit holds, human takeover, replies from every sender, rate questions, new senders |
| VOX | 7 | No disposition taxonomy; no transfer target order or ring timeout; no content spec for the spoken brief; no outbound attempt cadence or caller-ID rules; recording consent refused has no procedure; no call types for partners, vendors, servicing questions, solicitors. *Fixed:* voice campaigns, transfer timing, outbound context, script gaps, AEGIS paused, budget halt, new callers |
| FORGE | 7 | No dwell times; no extraction confidence threshold; no chase cadence or attempt limit; deadline edge cases (found inside 24 hours, passed, weekends); no condition classes or typical document expiry ages; EMBER's review ask waits for post-close completion. *Fixed:* file endings, envelopes, disposal, mailbox split with ECHO, migrated files |
| EMBER | 7 | "Dormant" undefined; no benefit bar for "math genuinely benefits them"; no "peak emotion" timing; no mortgage trigger playbook (mortgage insurance removal, ARM resets, FHA to conventional, cash-out equity); channels beyond email unstated. *Fixed:* reply ownership, trigger figures, no-closed-file contacts, unsubscribes, closed-lost from FORGE |
| RELAY | 7 | No test significance values; no internal early-warning level below the provider's complaint limit; no hard- and soft-bounce rules; no warmup schedule; no restart owner after a reputation pause; deliverability and carrier-registration detail absent. *Social scope, added after the last rating and not yet re-rated:* no posting cadence per company page; no list of ad platforms with their credit or housing category and Composio toolkit confirmed; no public-reply templates for ECHO yet; spam and abuse in comments are flagged to the page's owner but nobody moderates them; no retention rule for the record of a post taken down. *Fixed:* budget halt, gate refusals, copy requests, closed and in-process borrowers excluded |
| SCOUT | 7.5 | No duplicate-matching keys or confidence threshold; no junk and bot-fill criteria; "specialty" undefined (VA, FHA, jumbo, reverse, non-QM); no latency budget for its own segment. *Fixed:* unassigned leads, existing owners, new callers and writers, consent capture, departures |
| TEMPO | 7.5 | No reminder schedule; no no-show recovery window or attempt count; no buffer or travel defaults; no mortgage appointment types or lengths; no owner for scheduling the closing with the settlement agent; no procedure for getting availability from outside parties. *Fixed:* same-minute money escalation, deep-work conflicts, email account, cancellations, replies, departures, LEDGER feed |
| ATLAS | 7.5 | No first-touch rule; "confidence drops" undefined; no stall or loop definition; no budget amounts; no board-approval-stage default; the per-contact brief has no field list. *Fixed:* complete routing list, live calls on a budget halt, paused AEGIS or SOPHIA, authority returns, gate refusals, brief contents |
| QUILL | 7.5 | No channel limits (SMS segments, subject lines, ad characters); no reading level; no variants-per-test rule; no versioning scheme; no mortgage content knowledge (products, audiences, seasonality). *Fixed:* disclosure trigger, VOX script gaps, content people publish, retirement, changes requested |
| CANVAS | 7.5 | No brand-consistency criteria, tag taxonomy, format-spec values, or licence-warning window; no fast expiry for assets showing a rate; no co-branding lockup rules for routine partner brand clashes; no mortgage visual genres. *Fixed:* ad visuals' route, brand conflicts to the requester, stock imagery, alternatives, changes requested, shared-asset recall |
| WARDEN | 7.5 | No key-rotation interval or project-key replacement sequence; no anomaly thresholds or suspend authority during an incident; no check on who may request access; no mortgage role templates or license-state routing. *Fixed:* activity-log access, board queue, paused-manager route, owner naming, departures handoff |
| SOPHIA | 8 | "Ambiguous" undefined; no top-three ranking rule; no brief delivery time or prep lead time; no rule for "the right human" when the owner is away; no rules for what per-user memory may hold or who may see it. *Fixed:* override row, paused ATLAS, document questions, full From ATLAS list |
| AEGIS | 8 | No judgment-pass criteria, score scale, promotion and demotion thresholds, or red-team categories (awaiting compliance rules); no approval-ID lifecycle (expiry, what forces re-review); no fix-up step when after-the-fact scoring finds a live-channel violation. *Fixed:* board routes for recommendations and red-team results, budget warning, screen failure row, exit holds, gate reviews, WARDEN reconciliation |
| CIRCUIT | 8 | No backtest pass criteria or named approver for activation; no retry, replay, or time limit when repair fails; no change control when a field rename breaks readers; no mortgage milestone automations or LOS field mapping. *Fixed:* tool ban, other agents' surfaces, gate change review, send-step user ID |
| LEDGER | 8 | No named sources or tools for outside market data; no freshness thresholds; no attribution model or forecast method; no named scorecard recipient; thin mortgage analytics (lock pipeline, fallout, purchase versus refinance). *Fixed:* market-report approval path, TEMPO and usage feeds, COMPASS feed |

---

## 2. Thresholds and definitions to decide

These are **business decisions for the Account Owner**, not values to invent. Once decided, they belong in one shared sheet (for example `THRESHOLDS.md`) that each `AGENTS.md` references by name, so a value changes in one place.

| # | Threshold or definition | Used by | Where it appears |
|---|---|---|---|
| 1 | Intent and fit scales, disposition cut-offs, minimum coverage | PULSE | §2, §3, §4 |
| 2 | Judgment-pass criteria; conversation-score scale; promotion and demotion thresholds | AEGIS | §2, §4 |
| 3 | No-show recovery window | TEMPO | §2, §3 |
| 4 | Reminder schedule | TEMPO | §2 |
| 5 | Market-data age before it counts as stale, per data type (rates, inventory and pricing, competitor activity) | LEDGER, EMBER | §3 failure rows |
| 6 | Reactivation benefit bar (rate drop, monthly savings, break-even) | EMBER | §2 |
| 7 | Test significance: confidence level, minimum sample, minimum duration | RELAY | §2, §3 |
| 8 | Paced resume rate after a provider error | RELAY | §3 failure row |
| 9 | Expected dwell time per pipeline stage | FORGE | §2, §3 |
| 10 | Extraction confidence threshold | FORGE | §2, §3 |
| 11 | Shadow-mode exit criteria | COMPASS | §2, §3 |
| 12 | Key-rotation interval; access-review schedule; anomaly thresholds | WARDEN | §2 |
| 13 | First-touch channel rule | ATLAS | §4 |
| 14 | "Confidence drops" | ATLAS | §2, §3 |
| 15 | Budget amounts per contact, campaign, and user | ATLAS | §2, §3 |
| 16 | "Hot" and the other nine intents; opt-out phrase list; "distress" | ECHO | §2, §3 |
| 17 | Duplicate-matching and junk criteria | SCOUT | §2 |
| 18 | "Ambiguous enough to confirm"; the top-three ranking rule | SOPHIA | §2 |
| 19 | Channel length limits; reading level; variants per test | QUILL | §2 |
| 20 | Workflow rollback procedure | CIRCUIT | §3 |
| 21 | Licence-expiry warning window | CANVAS | §3 |
| 22 | Which kinds of task get a board user as an approval stage | ATLAS | §4 |
| 23 | Brand-consistency criteria; library tag taxonomy; per-channel format-spec values | CANVAS | §2, §3 |
| 24 | "Dormant" — how long without activity, and at which stages | EMBER, AEGIS, RELAY | §2, §4 |
| 25 | Chase cadences and attempt limits — FORGE's document chasing, TEMPO's overdue tasks, VOX's outbound attempts | FORGE, TEMPO, VOX | §2, §3 |
| 26 | Transfer target order and ring timeout | VOX | §3 |
| 27 | Stall and loop definition between agents | ATLAS | §3 |
| 28 | How early AEGIS files a budget override request | AEGIS | §3 |
| 29 | Backtest pass criteria and who confirms activation | CIRCUIT | §3 |
| 30 | Which PULSE dispositions need a human's confirmation under the L2 cap | PULSE | §3 |

Items 5 and 8 were introduced by the dependency-failure rows added in the last pass (`AGENTS_md_conflict_resolutions.md` #41) and need values before those rows are fully operational.

---

## 3. Cross-cutting limitations

1. **No worked examples anywhere.** No file shows what a right call looks like on its hardest judgments — an indirect opt-out, a borderline qualification, a good versus a bad transfer brief, a draft that needs changes rather than a rejection. Two or three short examples per agent would steady behavior more than further rules.
2. **Domain Context is crowded by coordination.** About half of each §4 describes other agents' lanes. That is what made the conflict pass hold, but it leaves little room for how the job is done.
3. **The Command files are long.** SOPHIA, ATLAS, and AEGIS each run 1,570–1,800 words, which risks diluting their core instructions. Moving procedure into skills (section 4) is the way to shorten them without losing rules.
4. **KPIs name metrics without defining them.** "Handoff precision," "escalation precision," "brand consistency," "decisions traceable to an insight," and others have no formula or target. They are carried verbatim from the handbook, so the fix belongs in the handbook or in the skills' *Measured on* sections, not in §6.
5. **Compliance law is not named in any file** — deferred by decision, to be added later. There are no compliance rules for AEGIS yet, so its judgment-pass criteria, score anchors, promotion and demotion thresholds, and red-team categories stay open until they exist. When the law is added, it should bind the agents that apply each rule (AEGIS first, then QUILL, CANVAS, VOX, ECHO, EMBER, RELAY, FORGE, PULSE, SCOUT, WARDEN), and every rule in the files should be traced to its source.
6. **Policy calls to confirm once law is added.** Made in the third consistency pass to remove conflicts, not from law: a borrower's self-described credit range may be recorded by PULSE, labeled self-reported (#59); a partner's own headshot may be used with the partner's written consent (#61); a calendar's attendee notice to staff is not a message (#52). Added in the fourth pass: a stock photo of an identifiable person falls under the likeness rule (#84); a trigger figure filled from a disclosure-builder placeholder AEGIS approved keeps the template's approval ID (#83); withdrawn and denied files go to EMBER as closed-lost for recycling (#83); a hostility or wrong-number hold is released only on the owning loan officer's request (#76). Added with RELAY's social scope: no contact data from the CRM is uploaded to an ad platform, which rules out customer-list and lookalike audiences (#88), and no agent hides or deletes a comment (#90).
7. **Mortgage operating knowledge is the weakest dimension (2.5 / 5).** Section 4 of most files describes the runtime, not the work: no complexity signals, refinance triggers, appointment types, condition classes, document expiry ages, market-data sources, or onboarding interview content. This belongs in skills and a domain reference, not in more rules.

---

## 4. Recommended improvement path

In order of return:

| Step | Work | Expected lift |
|---|---|---|
| 1 | `pulse` scoring skill: rubric, discovery question set, disposition rules, coverage rule, complexity signals | PULSE 6 → about 8 |
| 2 | `aegis` review and scoring skill: judgment-pass criteria, score anchors, promotion and demotion thresholds, red-team categories | AEGIS 8 → about 9 |
| 3 | Thresholds sheet (section 2), decided by the Account Owner and referenced from each `AGENTS.md` | +0.5 each for EMBER, RELAY, TEMPO, FORGE, COMPASS, LEDGER, WARDEN |
| 4 | Two or three worked examples per agent, inside that agent's skills | Operability across all 17 |
| 5 | Compliance law pass | Domain depth across the regulated agents |

Taken together, steps 1–4 bring the set to about 9 / 10 before law is added.

**Skill format to follow.** The earlier 24-agent company already has a settled skill format at `PaperClip-company/Company design/ImportantAgentFiles/SKILLS/SKILLS_FOLDER_STRUCTURE.md`:
- Division → `CODENAME (Title)` → skill folder → `SKILL.md`.
- Frontmatter: `name`, `description`, `agent`, `division`, `binding` (`interlock`, `mandate`, or `standard`).
- Six body sections: When this fires, Inputs, Procedure, Output, Hard rules, Measured on.
- Hard rules in two groups: the agent's `AGENTS.md` §5 inherited in full, then rules specific to the skill.

Its PULSE `dual-axis-scorer` and AEGIS `conversation-scorer` are useful starting points, but they predate this roster (no SOPHIA, no Composio, a different set of agents) and must be checked against v5 and the resolutions before reuse. Skills for this roster go in `17 agents setup/skills/`.

---

## Keeping this list current

- When a limitation is fixed, remove its row and note the change in `AGENTS_md_conflict_resolutions.md` if the fix touched more than one file.
- When a threshold is decided, record the value in the thresholds sheet, not in the individual `AGENTS.md`.
- Re-rate after each pass on the same four dimensions so scores stay comparable.
