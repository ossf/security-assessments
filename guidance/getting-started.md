# Getting Started

<!-- Devnotes:
  [!NOTE] is used for any first-person quotes that should be attributed.
  [!IMPORTANT] or [!WARNING] is used for any text blocks that are supplemental to the content and do not need to be attributed.
  ``` code block is used for formulas or other content that should be clearly demarcated
-->

This guidance describes security assessments, including what a security assessment is, how it differs from a security audit, how to perform a security assessment, and how to use a completed assessment.

These contents are heavily informed by the Security Assessment process developed by the CNCF Security Technical Advisory Group and authored by Justin Cappos (STAG Technical Lead). This draws on years of compound experience analyzing and evaluating security products across a wide array of domains. The examples in this text draw from both non-technical anecdotes and a variety of detailed technical examples from Linux Foundation projects in the cloud native space.

It is recommended to follow the guide one step at a time, rather than seeking to read and understand the process in completeness. You will internalize more by attempting the exercises yourself.

## Identifying Your Use Case

How you engage with this guidance will depend on your use case:

### You are preparing to have your software assessed by peers or a third-party

Please do a quick read of the knowledge base before working with reviewers. If you haven't done a self-assessment yet, consider setting that as your interim goal — prior to bringing in reviewers from outside the project.

### You want to learn about threat modeling and software security

Many are helpful to learn about threat modeling and how to assess the security of general projects. Perhaps the least relevant part are the portions of this book that relate to the specifics of Security Assessments. However, those sections can serve as an example of how to implement some of the ideas in the rest of the book in the cloud native space.

### You want to lead or participate in an assessment

You should read as much of the content as possible. This includes the self-assessment content if the project you're assessing is supplying a completed self-assessment to kickstart your review.

The sections describing how to use an assessment and how to have your project assessed effectively may be less applicable to you, but will help you understand the process and expectations from those perspectives.

### You are evaluating the security posture of a project with a published security assessment

You, the consumer of this hard work, need to understand how best to benefit from a security assessment. The section on consuming assessments is exactly what you need. It may also be useful to read the following section on Security Assessments and Audits, to understand the difference and why you should expect to see relatively few CVEs raised after a security assessment versus a security audit.

### If you're still not ready to get started

As with many things in security there is often not one “correct answer”, despite there being infinite wrong answers. If you would like to ask questions or help improve this guidance, please don't hesitate to engage through the designated [community channels](./CONTRIBUTING.md).

**[> Next up: Security Assessements and Audits](./assessments-and-audits.md)**
