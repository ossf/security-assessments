# Joint Assessment: Reviewer

**[< Back to Creating a Joint Assessment](../creating-document.md)**

A reviewer is the active outside party in a joint assessment. You are reading the project's self-assessment, asking questions of the maintainers, working through threat models, and contributing to a document that will be published as the joint output. This page describes what that involves, what level of expertise is needed, and how to do it well.

## Who is this for

Anyone with a working interest in security and a willingness to read carefully and ask honest questions. You do *not* need to be a domain expert in the project being assessed. Security acumen is the more important skill, and security acumen is something most engineers can develop with practice. A basic technical understanding of the project's domain — comparable to someone who has just started using the technology — is enough.

If you are new to security work entirely, the right starting point is usually the *observer* level (described below) on someone else's assessment. The next assessment, you take on a piece of analysis as a reviewer. By the assessment after that, you are often the most useful person in the room because you remember what it was like not to know.

## Levels of participation

Joint assessments typically run with people at a few different levels of involvement. Pick the one that matches your experience and bandwidth.

- **Observer.** Attends meetings, reads the document, lurks in the chat channel, has no formal responsibilities. The intent is not to silence you — if you have a question or notice something, voice it. The intent is to let you watch the process without pressure to drive it. This is the recommended starting level for someone new to security assessments.
- **Reviewer.** The core role described on this page. Active participant in feedback, analysis, and document refinement.
- **[Lead reviewer](./lead.md).** A senior reviewer who orchestrates the engagement. Almost always someone who has reviewed at least one prior assessment.
- **Facilitator.** A coordinator across multiple assessments, used when the reviewing organization runs many joint reviews and needs a queue manager and quality bar across them. In small contexts this role doesn't exist, or it folds into the lead.

## What reviewers actually do

Concretely, you will:

- **Read the self-assessment carefully** and produce a list of clarifying questions. Many of the highest-value items in a joint assessment come from this initial pass — the things that turn out to be unclear, ambiguous, or implicitly assumed.
- **Work through the threat-modeling techniques** ([actors](../../background/threat-modeling/actors.md), [actions](../../background/threat-modeling/actions.md), [attack graphs](../../background/threat-modeling/attack-graphs-technique.md), [attack matrices and comprehensive coverage](../../background/threat-modeling/comprehensive-coverage.md), [DREAD](../../background/threat-modeling/dread-technique.md)) for the parts of the system you've been asked to cover. The lead will divide work; you focus on your portion.
- **Capture findings in three buckets**: clarifying questions for the project, feedback for the project (recommendations, hardening, design observations), and feedback for the reviewing organization itself (process gaps, items to track, patterns worth noting).
- **Participate in discussion meetings** with the project maintainers, walking through findings and resolving disagreements where possible.
- **Contribute to the joint document.** The lead (or someone designated by the lead) writes the consolidating summary; reviewers contribute the analysis and findings their portion produced.

## Conflicts of interest

Declare them up front. The two most common cases:

- You work for an employer that competes with, depends heavily on, or is a major customer of the project.
- You contribute to the project itself, even occasionally.

Neither necessarily disqualifies you, but the lead should know. In some cases you'll be reassigned to a different portion of the assessment; in others you'll be moved to observer level for that engagement.

## How to be a good reviewer

**Ask the obvious question.** *"Why does service A trust service B?"* and *"What stops an attacker who controls X from doing Y?"* are the bread-and-butter questions of joint assessments. They feel basic, but they are exactly the questions whose answers turn out to be load-bearing.

**Frame findings as factual statements about the system.** *"If the build server is compromised, an attacker can sign arbitrary releases because no offline key check is performed at install time"* is a finding the project can act on. *"The release pipeline is concerning"* is not.

**Calibrate your impact estimates.** When you score with DREAD or any other framework, walk the number back to a sentence: *"if this is exploited, X happens, costing roughly Y, requiring Z to remediate."* If the sentence sounds wrong, the score is wrong.

**Respect editorial boundaries.** The self-assessment portion of the joint document is the project's. Even if you disagree with their framing, that's the project's section to write. Your section is the analysis, summary, and recommendations.

**Don't manufacture criticism.** A common mistake is to feel that the assessment must produce a long list of issues to be valuable. It mustn't. A good assessment of a well-built project may produce a short list of refinements and a clear articulation of the existing strengths. That is a useful artifact — it gives downstream consumers and adopters something concrete to rely on.

**Time-box your "I'll dig into this later."** Joint assessments stall when reviewers have a vague intention to read the source code more deeply and never quite get there. If a finding requires you to investigate something specific, give yourself a small fixed budget for it — an hour, two hours — and either come back with an answer or write the question down for the project to answer instead.

## What to expect

A reasonable reviewer commitment is **10–20 hours** spread over a few months for a typical joint assessment. The bulk of that is reading, analyzing, and writing — meetings are a relatively small fraction. Your effort will be very lumpy: a heavy reading week at the start, gaps while waiting on the project, more heavy weeks during analysis and discussion.

You should also expect to come away with a sharper sense of how to look at a system you don't already know. Each assessment makes the next one faster. After two or three reviews, you will likely be ready to lead one.
