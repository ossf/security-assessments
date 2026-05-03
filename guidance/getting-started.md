# Getting Started

<!-- Devnotes:
  [!NOTE] is used for any first-person quotes that should be attributed.
  [!IMPORTANT] or [!WARNING] is used for any text blocks that are supplemental to the content and do not need to be attributed.
  ``` code block is used for formulas or other content that should be clearly demarcated
-->

This guidance describes security assessments, including what a security assessment is, how it differs from a security audit, how to perform a security assessment, and how to use a completed assessment.

These contents are heavily informed by the Security Assessment process developed by the CNCF Security and Compliance Technical Advisory Group and authored by Justin Cappos (TAG-SC Technical Lead). That process was refined through years of assessing real projects across many domains, and the techniques generalize well beyond their origin. This guide is intended to be useful to any open source maintainer — and to closed-source teams who want a durable, defensible record of their security posture.

It is recommended to follow the guide one step at a time, rather than seeking to read and understand the process in completeness. You will internalize more by attempting the exercises yourself.

## Why bother with an assessment?

Security is unusual among engineering concerns because it has an *intelligent adversary*. To see why that matters, imagine learning chess. If your opponent is a program that picks legal moves at random, you can devise a strategy that wins almost every time, and you can quantify your win rate the way you'd quantify the failure rate of a hard drive. Now replace the random opponent with a human — or with hundreds of humans who have studied your strategy and are trying to defeat it. Your win rate is no longer a stable number. The opponent will deliberately steer the game into the situations that hurt you most.

Reliability engineering reasons about the random-opponent case. Security has to reason about the second one. A security assessment is a structured way to reason about it: to make explicit what you're trying to defend, who you're defending against, and what you've decided is out of scope. It is less about producing a list of bugs (that's an audit) and more about building a model of your system that you and others can argue with.

The work is not a chore. Done well, it is one of the more intellectually rewarding parts of building software — you come away with sharper intuitions about your own system, and with artifacts that make every future security conversation (with auditors, with downstream consumers, with compliance teams, with your own future self) shorter and clearer.

## Self-assessment first, third-party review later

A common question is whether to start with a self-assessment or bring in outside reviewers. Almost always, start with a self-assessment. It costs you only your own time, surfaces the easy gaps before any expensive eyes look at the system, and produces an artifact that makes any subsequent third-party review dramatically more efficient. The Joint-Assessment guidance is designed to build on a completed self-assessment, not replace it.

## Identifying Your Use Case

How you engage with this guidance will depend on your use case:

### You are preparing to have your software assessed by peers or a third-party

Please do a quick read of the knowledge base before working with reviewers. If you haven't done a self-assessment yet, consider setting that as your interim goal — prior to bringing in reviewers from outside the project.

### You want to learn about threat modeling and software security

Many sections are helpful to learn about threat modeling and how to assess the security of general projects. Perhaps the least relevant part are the portions of this book that relate to the specifics of Security Assessments. However, those sections can serve as an example of how to implement some of the ideas in the rest of the book.

### You want to lead or participate in an assessment

You should read as much of the content as possible. This includes the self-assessment content if the project you're assessing is supplying a completed self-assessment to kickstart your review.

The sections describing how to use an assessment and how to have your project assessed effectively may be less applicable to you, but will help you understand the process and expectations from those perspectives.

### You are evaluating the security posture of a project with a published security assessment

You, the consumer of this hard work, need to understand how best to benefit from a security assessment. The section on consuming assessments is exactly what you need. It may also be useful to read the following section on Security Assessments and Audits, to understand the difference and why you should expect to see relatively few CVEs raised after a security assessment versus a security audit.

This applies whether the project you're evaluating is an open source dependency, a commercial vendor's product, or an internal piece of software your own organization is reviewing — the same questions you ask of an external project apply to your own.

### If you're still not ready to get started

As with many things in security there is often not one “correct answer”, despite there being infinite wrong answers. If you would like to ask questions or help improve this guidance, please don't hesitate to engage through the designated [community channels](../CONTRIBUTING.md).

**[> Next up: Security Assessments and Audits](./background/assessments-and-audits.md)**
