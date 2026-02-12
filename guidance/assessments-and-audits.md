# Security Assessements and Audits

When looking at security, there are different levels at which you can do this. Roughly speaking, a security assessment can be thought of as examining the security architecture and posture of a software project. While the tooling, implementation strategy, deployment, etc. are important to a security assessment, the assessment is often detached from a specific deployment and the implementation itself. It focuses more on whether a software project as a whole is doing the sorts of things that lead to security.

Let’s now consider an example security assessment using a real world example of a bank called TrashPanda Bank. TrashPanda Bank is a brick-and-mortar bank without any computers, which allows one to focus on non-technical attacks and defenses. A security assessment would look at a TrashPanda’s security by examining the blueprints, vault types, alarm systems, accounting practices, policies for vetting employees, etc.

In contrast a security audit looks for instances of specific flaws in a security project. So, for a computing project, the goal of an audit is to find specific attack cases / issues in the source code that could enable an attacker to do something malicious.

To return to TrashPanda Bank, a security audit of this would look quite different from an assessment. The auditor might try to pick locks, actually smash a
chisel into the mortar around a safe to see if it can be removed, understand if the gym using the floor above the bank could enable one to smash in through the vault’s ceiling, or figure out the timing of the security guard bathroom breaks to see if there is a moment they can sneak past undetected. In other words, these look for problems that result in specific, detailed flaws in implementation and quirks of the deployment that cause weaknesses an attacker can exploit.

One final note is that the terms “audit” and “assessment” are not universally used this way in all literature. So if you read them elsewhere, please consult the author’s definition.

## Pros and Cons

There are merits to both audits and assessments. As a result, the best security firms will do both sorts of analysis (to different levels of detail) on a software project.

Assessments tend to be better at identifying more systemic problems, like design problems or issues in the procedures used to make software. These problems are extremely important to fix because they are often cause multiple instances of a security issue. They can also increase the impact, turning a minor problem into a major one.

Assessments are often essential for an organization to tell if a software project is a good one to rely on. The way in which things are fixed and the “quality” of the software project are exhibited as part of the assessment.

Assessments can be valid for a long period of time (years) so long as the project does not make substantial changes to how they make software. As such an assessment better represents the project’s overall health. In contrast, a security audit will instead represent only a momentary snapshot of a project’s set of vulnerabilities (often only a single release) and only for the deployment scenarios considered.

Similarly, an assessment is general enough that some properties (like the actors, actions, goals, etc.) will directly translate over to multiple implementations of the system in different languages and also will likely translate to a wide array of deployment environments. With an audit, bugs found in an audit are often specific to an implementation (unless the implementers looked at each other’s code and copied them!).

Security audits are great for finding bugs in the project today. Hence a project can often fix problems found in an audit rather quickly. It is usually immediately apparent that these bugs were impactful because an auditor often provides an example exploit that causes a security failure due to the bug. This looks great to management as it is clear what value they have derived from the security audit and patching the bug.

To understand the difference between assessments and audits consider the following cases for TrashPanda Bank. The security assessment firm says that you should implement better personnel controls which the assessors claim will improve several different security aspects. In contrast, a security auditor may find out that Eve in accounting has been embezzling money, which then may lead the firm to fire and prosecute her.

On the surface, the audit sounds more pertinent at any particular moment because it has an actual example of a serious problem. The downside stems from the fact that an audit focuses on what someone found at that moment, it is even the case that different audits may lead to quite different results. For example, security firm A’s audit may have caught Eve’s embezzling, while security firm B’s audit finds out that Tom the teller has a gambling problem and has been skimming deposits (i.e., stealing cash when a deposit is made). The two firms who did different audits found different problems, which is expected. With audits, you really don’t know of any underlying deficiencies other than the bugs they found. In contrast, with a security assessment, you tend to focus on macro-level concerns and procedures at TrashPanda Bank. You may tighten up your personnel controls, which may lead to Eve silently stopping her behavior as she knows she would be caught and Tom the teller taking a job at another bank. So, although acting upon the results of an assessment may mitigate or prevent these issues from arising, you may never detect occurrences of a problem explicitly from an assessment.  The assessment flags potential problems, but it is difficult to count or measure avoided bugs and vulnerabilities. This makes the value of a security assessment require more effort to quantify, such as factoring reduction of structural risk and mitigation of losses by reducing the likelihood and severity of a negative outcome should problems occur.

In the end, we recommend projects initially perform a security self-assessment before engaging with any specific audit process.  Security assessments provide durable guidance which can continue to pay dividends over the lifetime of a project -- a better value for the maintainer time investment.
