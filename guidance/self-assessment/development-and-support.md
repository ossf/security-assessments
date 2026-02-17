# Development & Support

**[< Previous: System Design](./system-design.md)**

This section describes the development practices, communication channels, and security processes that support the project’s lifecycle. Providing this information helps reviewers understand how security is managed throughout development and maintenance.

## Development Pipeline

Describe the testing and assessment processes that the software undergoes as it is developed and built.

Here are some things you might consider including:

- What security practices do you automate or enforce in your SDLC?
- Do you have branch protection or repo security features in place?
- Are committers required to sign their commits, or a contributor license agreement?
- Do you have automated testing or fuzzing on every pull request?
- Do you have software composition analysis or dependency management tooling?
- How many reviewers are required for a pull request to be approved?
- Do you have any measures around code owners?
- Is your release process automated?
- Does every release include an automatically generated Software Bill of Materials?
- Do you sign releases?
- Are container images immutable and signed?

## Communication Channels

Define how different audiences can reach your team and how communication is structured.

- **Internal** – How do team members communicate with each other? (e.g., private Slack, internal mailing lists)
- **Inbound** – How do users or prospective users communicate with the team? (e.g., public mailing list, GitHub issues)
- **Outbound** – How do you communicate with your users? (e.g., security advisories, release announcements)

## Ecosystem

Describe how your software fits into the cloud-native ecosystem.

For example:
> *Flibber integrates with both Flocker and Noodles, covering virtualization for 80% of cloud users. While Flibber has a small direct user base, every virtual instance uses Flibber encryption by default.*

Understanding your project's ecosystem impact helps assess its security significance.

## Responsible Disclosure Process

Your project should have a process through which a responsible user or researcher can disclose findings related to vulnerabilities or weaknesses in your project, and the process a project will take in the event that a report is received or another security incident occurs.

If you’re using GitHub, there is a built-in feature for this within the Security tab at the top of your repository page. If you’re using another strategy, detail your approach here.

Include a reference to where your project has documentation letting readers know how to make responsible disclosures for your project.

- **Reporting** – How should suspected vulnerabilities be reported? (e.g., security email, private GitHub advisory)
- **Response Team** – Who is responsible for triaging reports?
- **Coordination** – Do you follow an embargo period before public disclosure?
- **Patch Process** – How are fixes developed, tested, and released?

## Incident Response

A major part of secure software development is simply a matter of planning ahead for when things go wrong. Vulnerabilities and weaknesses will eventually be found, and proper planning will enable your project to quickly and effectively respond.

Use this section to document your project’s process for triage, confirmation, notification of vulnerability or security incident, and patching/update availability.

If your project lacks a comprehensive plan for incident response, then include as much detail as you can—and be sure to include this gap on your project’s roadmap!

- **Triage & Confirmation** – How do you validate and assess security reports?
- **Notification** – How do you inform users about vulnerabilities?
- **Remediation** – How do you develop and distribute patches or updates?

A clear incident response process ensures vulnerabilities are addressed efficiently while minimizing disruption.

**[> Next Up: Security Considerations](./security-considerations.md)**
