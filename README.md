# Open Source Project Security Assessments

In response to a rising demand for standardized security review of open source projects, the Open Source Project Security (OSPS) Assessments project provides a tiered model for assessing the security state of open source software.

## What is an assessment and how does it relate to an audit

Both a security assessment and a security audit help to understand the security of a system and play different, but overlapping, roles.   A security audit focuses primarily at looking for security defects in a project's implementation or a deviation from established best practices.   In contrast, an assessment focuses on thinking about what a reasonable project of this type might be expected to provide in terms of security properties and potential gotchas for users.

To make this clearer, consider a non-technical example of a presentation tool, as people commonly use when giving a talk.   A security audit would point out defects in manufacturing.   Both an assessment and an audit would likely flag an issues like the use of a hardcoded security key that is shared for all instances of the clicker.   The assessment would catch that the wireless communication in the presentation tool can make it easy to track the owner and also give guidance on ways to mitigate this.   The assessment may also catch subtle issues like a laser pointer being considered a weapon in countries like Switzerland and thus the inclusion of this meaning the presenter tool is banned from air travel in that country.

So audits are more about a failure to build software correctly and follow best practices.   Assessments are looking at whether the security properties of the software make sense and give suggestions for improvement.

## Approach

OSPS Assessments may come in one of two types: self-assessment or joint-assessment. This tiered approach is intended to reduce complexity through a "shift left" approach that encourages participation from project maintainers while also reducing overall cost and complexity.   

### Getting Started

Visit [the Getting Sarted guide](./guidance/getting-started.md) to determine your first steps, including which of the assessments is right for your situation. In most cases, it is recommended to start at the lowest level, self-assessments, and work up from there.

Continue reading below for a rapid overview of each assessment type.

### Level 1: Self-Assessment

A self-assessment allows a software project to evaluate its own security posture using a standardized process. This helps identify strengths, areas for improvement, and potential risks without external influence. The results can serve as a foundation for internal discussions, decision-making, and future external reviews.

### Level 2: Joint Assessment

A joint-assessment is a collaborative security review conducted with external security experts or a designated working group. This approach provides an opportunity for project teams to receive constructive feedback, validate security practices, and gain insights from experienced reviewers. The process often includes structured discussions, evidence-based evaluations, and actionable recommendations for strengthening security practices.

## Antitrust Policy Notice

Linux Foundation meetings involve participation by industry competitors, and it is the intention of the Linux Foundation to conduct all of its activities in accordance with applicable antitrust and competition laws. It is therefore extremely important that attendees adhere to meeting agendas, and be aware of, and not participate in, any activities that are prohibited under applicable US state, federal or foreign antitrust and competition laws.

Examples of types of actions that are prohibited at Linux Foundation meetings and in connection with Linux Foundation activities are described in the Linux Foundation Antitrust Policy available at http://www.linuxfoundation.org/antitrust-policy. If you have questions about these matters, please contact your company counsel, or if you are a member of the Linux Foundation, feel free to contact Andrew Updegrove of the firm of Gesmer Updegrove LLP, which provides legal counsel to the Linux Foundation.

[how the project operates]: governance/GOVERNANCE.md
[how to report security-related issues]: governance/SECURITY.md
