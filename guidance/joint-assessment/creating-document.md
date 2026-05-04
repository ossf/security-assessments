# Creating Your Joint Assessment Document

A joint assessment is a Level 2 review: a collaborative security assessment performed *with* a project's maintainers, by reviewers who are not part of the day-to-day team. Where a self-assessment is the project speaking about itself, a joint assessment is the project and a small group of outside reviewers refining that picture together — surfacing missing cases, hidden assumptions, and structural risks that the maintainers were too close to see.

The process described here is adapted from the CNCF TAG-Security joint review process. The same structure applies to any open source project working with peer reviewers, an academic partner, or a third-party security firm — and to closed-source teams whose reviewers come from internal security, a sister team, or a contracted assessor. Where this guide says "reviewers," read it as whoever is filling that role in your context.

## Prerequisite: a completed self-assessment

A joint assessment builds on, and does not replace, the [self-assessment](../self-assessment/getting-started-self-assessment.md). Trying to start at Level 2 without the Level 1 artifact in hand almost always wastes reviewer time: the early conversations end up reconstructing information that the maintainers already had, and the deeper analysis that is the whole point of a joint review never gets reached.

Treat the self-assessment as the entry ticket. If the project does not yet have one, start there.

## Roles

A joint assessment has three named roles, plus an optional facilitator:

- **[Maintainer](./roles/maintainer.md)** — someone from the project being assessed, providing accurate information and context.
- **[Reviewer](./roles/reviewer.md)** — an outside party providing security-minded scrutiny, feedback, and an independent read of the system.
- **[Lead](./roles/lead.md)** — a senior reviewer who orchestrates the review, recruits other reviewers, divides up the work, and shepherds the document to completion.
- **Facilitator** (optional) — a neutral coordinator who helps prioritize work, manages the queue if the reviewing organization is doing many assessments at once, and is the point of escalation if the lead and project disagree. In small contexts (one project, one reviewing partner) the lead and facilitator can be the same person.

A typical joint assessment runs with the project's maintainers on one side and 2–5 reviewers on the other, with one of those reviewers acting as lead.

## The workflow

The phases below describe a typical engagement. Adjust the cadence to your situation; the sequence is what matters.

### 1. Kickoff

The project files a request for joint review through whatever channel the reviewing organization uses (an issue in the reviewers' repository, an intake form, an email). The request should link to the completed self-assessment and identify primary points of contact on the project side. The reviewing organization recruits a lead and reviewers, who declare any conflicts of interest.

### 2. Initial clarifying pass ("naive questions")

Before anyone scores attacks or proposes recommendations, the lead reviewer reads the self-assessment from the perspective of someone unfamiliar with the project and asks plainly: *what is this? what does this actor do? what does that interface guarantee?* This pass is deliberately not about finding flaws — it is about producing a shared mental model. The questions get answered by the maintainers and folded back into the document.

This phase often surfaces the most valuable findings even though it produces no "results" yet. Maintainers asked to explain their system to a careful outsider routinely realize that a constraint they thought was enforced is in fact only conventional, or that two diagrams in their head describe slightly different systems.

### 3. Reviewer analysis

Reviewers (the lead included) work through the system using the techniques from the [Threat Modeling](../background/threat-modeling-101.md) section: actors, actions, attack graphs, attack matrices, DREAD, comprehensive coverage. Each reviewer collects findings in three categories:

- **Clarifying questions** — items where the reviewer needs more from the project before reaching a conclusion.
- **Feedback for the project** — proposed changes, recommendations, hardening opportunities.
- **Feedback for governance / reviewers' own organization** — patterns worth noting for future assessments, gaps in the assessment process itself, or items the reviewing body should track.

The lead consolidates these into a draft summary document.

### 4. (Optional) Hands-on review

Some assessments include a lightweight hands-on phase: reviewers run the software in a representative configuration, exercise the documented security features, attempt obvious misuse, and note what they observe. This is *not* an audit — it is a sanity check that the documentation matches reality. It is bounded by reviewer availability and expertise; absence of findings is not absence of bugs.

### 5. Discussion and disagreement resolution

Reviewers and the project meet to walk through the draft. Most disagreements are resolved by clarifying language. For the rest, two principles help:

- **Stick to factual statements.** *"The system loses property Y when actor X is compromised"* is the kind of claim both sides can examine and either accept or refute. *"This is a huge problem"* or *"this is fine"* is much harder to land.
- **Different sections have different final writers.** The self-assessment portion of the joint document is the project's; even if reviewers disagree with framing there, the project keeps editorial control. The reviewers' summary and recommendations (often a top-level README or summary section) is the reviewers'; even if the project disagrees with phrasing there, they don't get to overwrite it. This is by design — it lets the joint document carry both perspectives honestly when consensus isn't reached.

If a disagreement still cannot be resolved, the facilitator (or whatever the equivalent escalation path is in your context) gets involved.

### 6. Publication

When both sides are satisfied — or have agreed to disagree per the rules above — the joint assessment is published. Where you publish depends on the reviewing organization's conventions and the project's preferences. Common landing spots:

- A dedicated assessments repository maintained by the reviewing organization.
- The project's own repository (often under `docs/security/` or similar), with a link to the reviewing organization's announcement.
- The project's website.

Whichever you pick, link the published assessment from the project's `SECURITY.md` so downstream consumers can find it. Include the date and version of the project that was assessed, and a clear statement of what *kind* of artifact this is (an assessment, not an audit; a snapshot, not a guarantee).

### 7. Reassessment over time

Joint assessments age more gracefully than audits, but they do age. Significant architectural changes — a new authentication model, a new external trust boundary, a major refactor, a merger with another codebase — should trigger a refresh. Even without those, plan to revisit every 12–24 months: a quick read-through often surfaces sections that are technically still accurate but that reviewers would now phrase differently.

A refresh is much lighter than the original. The structure exists, the actors are mostly stable, and most of the work is on the deltas. Open an issue with the reviewing organization, scope what changed, and run an abbreviated version of the workflow above.

## Format and structure

Use the [joint-assessment template](/templates/joint-assessment.md) as the starting point. The template captures the structure used in published joint assessments, but the structure is a guide, not a constraint — adapt it where the shape of your project demands it.

## What you can expect from the process

A few realistic expectations to set with the project before kickoff:

- **It takes longer than feels reasonable.** Plan in weeks-to-months, not days. 5 hours of project effort is the low end; 40+ hours is not unusual for complex systems. Reviewers are usually volunteering or splitting their time, and the back-and-forth that produces the value is inherently asynchronous.
- **The most useful conversations are informal.** Don't save up questions for big meetings. Async chat with reviewers during their analysis tends to produce far better results than batched feedback at milestones.
- **The output is not a list of bugs.** It is an articulation of the project's security posture, written in language that downstream consumers, auditors, and compliance partners can reference. Bug-finding is what an audit does.
