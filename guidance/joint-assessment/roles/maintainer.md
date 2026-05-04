# Joint Assessment: Maintainer

**[< Back to Creating a Joint Assessment](../creating-document.md)**

If you are reading this, you are someone the project being assessed is relying on for accurate information about how the system actually works. That makes you the most important person in the room.

This page is for project maintainers participating in a joint assessment of their own software. It assumes you have already completed a [self-assessment](../../self-assessment/getting-started-self-assessment.md) — without that, the joint review will spend its budget reconstructing context instead of producing insight.

## What you are doing

Three things, in roughly equal measure:

1. **Providing accurate information.** Reviewers ask questions; you answer them as precisely as you can, ideally with links back to source code, design docs, or commit history. *"I think it works that way"* is fine as long as you mark it as such — it tells the reviewers where to push deeper, which is what they're there for.
2. **Iterating on the document.** Your self-assessment is the starting draft. As reviewers ask "naive" questions and dig into actors and attack paths, the document gets sharper. You are co-editor on the project-owned portions and a careful reader on the reviewer-owned portions.
3. **Making decisions about your own roadmap.** Reviewers will surface findings. Some will be straightforward fixes; others will be design observations that take a release cycle to address; others will be issues you choose to acknowledge but not fix in this scope. All three responses are legitimate. The point of the assessment is to make these decisions visible, not to force a particular outcome.

## What it actually costs

Realistic effort, drawn from past joint assessments:

- **Small project, well-prepared self-assessment:** ~5 hours of maintainer time, spread over a few weeks of elapsed time.
- **Mid-size project:** 15–25 hours, often over a couple of months.
- **Complex multi-component project:** 40+ hours and several months of elapsed time.

Time is unpredictable because the depth of investigation depends on what reviewers find. Plan for a marathon, not a sprint. Block calendar time for it the way you would for a release — not "I'll get to it when I can."

## Practical tips

**Do a thorough self-assessment first.** Cutting corners at Level 1 directly produces rework at Level 2. A vague *"We sign releases"* in the self-assessment becomes a 30-minute reviewer back-and-forth in the joint phase asking which key, where it lives, who controls it, and how it's rotated. Five minutes of clarity now saves hours later.

**Chat informally.** Reviewers are usually happy to answer focused questions and look at intermediate work products. Don't save everything for scheduled meetings — quick async exchanges as questions come up tend to be the highest-value interactions.

**Be patient with "dumb questions."** A reviewer asking *"why does this service trust that one?"* is doing exactly what you brought them in to do. The questions that feel obvious are often the ones whose answers turn out to be load-bearing for the assessment. Treat them as opportunities to write down a working assumption, not as a test.

**Stick to factual statements when you disagree.** When something a reviewer wrote feels wrong, the productive form is *"the document says X, but in fact Y because Z (link)."* The unproductive form is *"this characterization is unfair."* The first invites correction; the second invites stalemate.

**Know which sections you control.** The self-assessment portion of the joint document remains under your editorial control. The reviewers' summary and recommendations remain under theirs. If a disagreement cannot be resolved by discussion, this split lets the joint document publish honestly with both perspectives, rather than blocking on consensus.

**Use placeholders.** Sections that need clarification can carry a `(How? — to confirm with X)` marker. This is preferable to either guessing or leaving the section blank, and it gives reviewers a place to focus.

**Plan for publication and re-use.** Decide early where the assessment will live (your repo, the reviewers' repo, your website) and link to it from your `SECURITY.md`. The artifact has more value if it's findable. Note the version of the project that was assessed; future readers will want to know.

## What you should expect from reviewers

In return for your time, you should expect:

- **A serious, security-minded read** of your system, not a checklist exercise.
- **Specific, actionable findings**, framed as factual statements about your system, not as judgments about whether the system is "secure."
- **Respect for your editorial control** over the project-owned portions of the document.
- **Clear communication** about timeline, expected next steps, and who's responsible for what at each phase.
- **A finished artifact** you can publish, point auditors and downstream consumers at, and refresh later without redoing it from scratch.

## When the work is done

The joint assessment is "done" when both sides are satisfied with the document and any unresolved disagreements have been honestly captured. Publish it, link it from `SECURITY.md`, record the date in your assessment metadata, and put a calendar reminder 12–18 months out for a refresh.

Many maintainers find that the most valuable thing the assessment leaves them with isn't the document itself — it's the sharper internal model of their own system. The document is the artifact you can share; the model is what helps you make better security decisions for the next several years of the project's life.

If you have time afterward, consider serving as a reviewer for someone else's joint assessment. Maintainers who have been through the process tend to be among the most effective reviewers for the next project in line — and helping out is the simplest way to keep the practice scaling.
