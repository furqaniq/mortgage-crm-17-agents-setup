# Model choice per wave

Companion to `SKILLS_BUILD_PLAN.md`. Decided 18 September 2026.

## The short version

Opus 5 for wave 0 and wave 1, which now includes RELAY's two money interlocks. Sonnet 5 for waves 2–7, fanned out as one subagent per agent, with Opus 5 reviewing at each wave close.

## Why the split is safe at all

Two devices in the build plan make the authoring pass model-agnostic, and both have to exist before the split is taken:

- **The per-skill authoring packet.** Each of the 166 skills is written against a different bundle of concrete source material — its own catalogue description, its domain note, the full text of the thresholds it cites, its escalation rows, its lane rows, its hard boundary. Generic prose is hard to produce from a non-generic packet. The generator never writes prose, so it never supplies a template to fall into.
- **The validator.** Twenty-five mechanical checks turn "is this any good" into pass or fail — filler phrases, undischarged domain notes, missing threshold citations, inherited blocks that no longer match `AGENTS.md`, links that cross an agent directory.

Neither depends on who is holding the pen. That is the point.

## Keep on the stronger model

**Wave 0 — the conflict matrix.** The script proposes 40–60 skill↔skill pairs by keyword match; each is confirmed by hand and gets one shared sentence that must land verbatim on both sides. A wrong pair writes a contradiction into two files and the validator certifies it, because the check proves the sentence *matches*, not that it is *right*. This is 60 judgments and it is the real design work in the whole build.

**Wave 1 — PULSE, AEGIS, and RELAY's two interlocks, 22 files.** Every convention downstream inherits from these: the aphorism discipline, the shape of a specific hard rule, the degraded-mode phrasing, the size band that gets measured here and locked. They are also the two governance-sensitive agents — the L2 cap, the board approval queue, approval IDs, the disposition boundary. A weak rule here is copied in spirit 140 times.

**RELAY's two money interlocks, moved into wave 1 — `paid-campaign-launcher-relay` and `ad-audience-builder-relay`.** Together they hold RELAY's hard boundary: never spend more than a board user approved, never touch an ad account's billing, payment method, or spend limit, never upload contact data from the CRM to an ad platform, and never target by a protected class or a proxy for one. Each is the only place its line is held, so a soft rule costs real money or creates fair-lending exposure, and nothing downstream catches it — the validator proves a rule is present, not that it closes every indirect path around it. They are written in wave 1, beside AEGIS's `paid-audience-review-aegis`, the skill on the other side of every paid audience, so the two agree from the start and both reach you at the review point. RELAY's other twelve skills follow in wave 5 and are written to match them.

**The `EXAMPLES.md` near-misses.** The near-miss — the plausible call that would have been wrong, and why — is the entire value of a worked example and the hardest thing in the set to write. Examples whose right answer is obvious teach nothing, and they are easy to generate by accident.

## Hand to Sonnet 5

**Waves 2–7 — 144 files.** By then the conventions are fixed, the format is frozen, every skill has a packet, and the validator fails the build on the known failure modes. This is most of the roughly 113,000 words and the part that benefits most from volume and parallelism.

## How to run it

Preferred: keep the driving session on Opus and spawn **one Sonnet subagent per agent**, each given the format contract and that agent's packets, writing that agent's skills. The driving session stays the reviewer — it runs the validator, owns the cross-agent shared sentences, and closes the wave. Judgment stays in one place; volume parallelises. Because each subagent starts with a clean context, the compaction checkpoints in `SKILLS_BUILD_PLAN.md` apply to the driving session, which is the one that fills up. In wave 5, RELAY's subagent writes its remaining twelve skills and is given the two finished interlocks to match.

Alternative: `/model sonnet` for a whole authoring session, then switch back for the wave-close sweep. Simpler, slower, and the cross-agent sentences are easier to get wrong because no single context holds both sides.

## At every wave close, regardless of model

Run the validator. Read a sample by hand for the two things it cannot catch: **invented mortgage numbers** that read well and trace to nothing, and **degraded-mode rules that have collapsed into 44 copies of one sentence**. Both are quality failures that pass every structural check.
