# Joint Assessment: Lead

**[< Back to Creating a Joint Assessment](../creating-document.md)**

The lead reviewer is the senior reviewer who runs the engagement. The lead recruits the rest of the review team, divides up the work, manages the document through to publication, and is responsible for the overall quality and timeliness of the assessment. The lead is also an active reviewer — leading does not mean delegating the analysis.

Almost always, the lead is someone who has reviewed one or more prior joint assessments. If you are leading your first one, the right configuration is to pair with an experienced facilitator or co-lead from the reviewing organization.

## Prerequisites

Before saying yes to leading an assessment:

- **Prior reviewer experience.** At least one previous joint assessment in any role beyond observer. Two or more is better.
- **Bandwidth.** Realistically 20–40 hours over the course of the engagement, spread across several months. The lead's time is lumpier than a regular reviewer's: heavier at the kickoff and discussion phases, lighter in the middle.
- **Comfort writing.** The lead consolidates findings into a summary document. You can designate someone to draft, but you own the final output.
- **No disqualifying conflict of interest.** The lead role is the most exposed; if you are heavily entangled with the project (as employer, major customer, or significant contributor), the lead role should go to someone else.

## What the lead does

### Before kickoff

- **Read the self-assessment** carefully. If it is sparse or incomplete, raise that with the project before recruiting reviewers — leading a joint assessment of a half-finished self-assessment wastes everyone's time, and the maintainers usually appreciate the early signal that they should circle back to Level 1.
- **Recruit reviewers.** A typical team is 2–5 reviewers including the lead. Mix experience levels deliberately: at least one experienced reviewer (yourself, ideally one more), at least one observer or first-time reviewer to grow the bench. Confirm conflict-of-interest declarations.
- **Set expectations with the project.** Walk the maintainers through the workflow, the rough timeline, the roles, and the ground rules around editorial control and disagreement resolution. Surprises later are usually traceable to skipped expectations now.

### Initial clarifying pass

You personally do the first read of the self-assessment as if you knew nothing about the project. List the questions that come up — questions whose answers should be in the document but are not, places where the language is ambiguous, actors that are mentioned but not defined. Send these to the project before bringing in the rest of the reviewer team.

This phase routinely produces some of the most valuable findings of the entire engagement. Don't skip it, and don't outsource it.

### Analysis phase

- **Divide the work.** Different reviewers take different parts of the system. Match assignments to expertise and to growth opportunities — the assessment is also a teaching engagement.
- **Stay close to the work.** Read what your reviewers produce as they produce it. If a reviewer is heading down a path that won't be productive, redirect early; if they're onto something significant, make sure it gets the time it needs.
- **Be the project's main contact.** Maintainers shouldn't have to figure out which reviewer to ask which question. You route, or you answer directly.

### Discussion and resolution

- **Run the discussion meeting.** Walk through findings systematically. For each, the goal is one of three outcomes: agreed and going into the document, agreed but reframed (often a language fix), or honestly disagreeing — in which case the rules of editorial control take over (the project keeps editorial say over the self-assessment portion; the reviewers keep say over the summary and recommendations).
- **Escalate stuck disagreements** to the facilitator (or whatever the equivalent is in your context) rather than letting them block the document. The split-editorial-control mechanism exists precisely so consensus is not a publication prerequisite.

### Document and publish

- **Own the summary.** You write it, or you designate a co-author and review what they write. The summary is the section downstream readers will read first; it should be precise, factual, and free of "this project is secure" language.
- **Sanity-check the integrated document.** The self-assessment portion (project-controlled) and the summary (reviewer-controlled) should read coherently together — the same vocabulary for actors, the same level of specificity, no contradictions of fact.
- **Coordinate publication.** Where it lives, when it goes live, who announces it. Make sure the project links it from `SECURITY.md` and that the published document records the date and version assessed.

### After

- **Capture process feedback.** Anything that should be different next time — for the reviewing organization, for the joint-assessment guidance itself, for future leads — gets written down. This is how the practice scales.
- **Plan the refresh.** Open a placeholder issue 12–18 months out for the next look at this project. Even if the project drives the refresh themselves, the placeholder is a useful nudge.

## Common pitfalls

**Letting the assessment drift.** Joint assessments without active leadership stretch out indefinitely. Set rough timeboxes for each phase at kickoff and check progress against them. The right cadence varies; absence of cadence is a problem.

**Doing all the work yourself.** Tempting, especially for first-time leads, but it defeats the point. The reviewing organization needs the bench growth, the project benefits from multiple perspectives, and you'll burn out. Delegate, then review what your delegates produce.

**Pushing for consensus past where it's productive.** Some disagreements are real and shouldn't be papered over. The split-editorial-control rule lets the document publish honestly; use it rather than spending another four meetings trying to align on a sentence.

**Treating the process as a TAG-Security ritual.** The CNCF process is the heritage, not the requirement. If you are leading an assessment outside that context — for a non-CNCF open source project, for a closed-source team's internal review, for an academic-partner engagement — the role's job description is the same, but adapt the specifics (intake mechanism, publication venue, escalation path) to your context.

## Variations by context

The lead role plays out slightly differently in different settings:

- **Within a foundation or umbrella organization** with a standing review group: you mostly inherit infrastructure (intake, publication, reviewer pool) and focus on running this one engagement. The facilitator role exists separately.
- **Peer review between two projects or communities** with no shared organizing body: you also do the work of the facilitator — managing intake, publication, and scope. Plan more time accordingly.
- **A contracted or paid third-party assessment**: the lead is often a senior member of the assessing firm. The structural points (editorial control, factual statements, refresh cadence) all still apply; the budget is just less of a constraint.
- **A closed-source internal assessment**: the project being assessed is one team; the reviewers are another (often internal security). The lead is usually a senior member of the reviewing team. Publication is internal but the same artifact discipline applies — date, version, scope, who reviewed what.

The job is recognizable across all of these. The mechanics adapt.
