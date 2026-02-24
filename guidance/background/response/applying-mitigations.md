# Applying Mitigations

**[< Previous: Applying Mitigations](./applying-mitigations.md)**

Applying mitigations is usually not as simple as just choosing a set of mitigations and applying them to parts of your system. A common mistake that I see novice system designers make is to focus more on the quantity and type of security mechanisms added than focusing on where and why. You need to reason about the goals your system has and then figure out how to intelligently apply mechanisms and controls to meet those goals.

To understand why, let’s go back to TrashPanda Bank and think about their security. If they buy and deploy the latest alarm system, but apply it to the manager’s snack drawer instead of the bank vault, they will not get the desired security benefits!

This also helps to explain why it is so important to design security into a system from the start instead of trying to bolt it on afterwards. If you don’t design things well from the start, it is often impractical or even impossible to get the security properties you want later... at least without starting over.

> [!NOTE]
> **From Graphs to Guards**, Commentary by Marco De Benedictis
>
> Attack Graphs capture the defenders’ mindset and working process, and so are time-consuming and require significant effort to generate to ensure correctness and the completeness of the paths that an attacker could exploit to achieve a potential goal.
> We can understand if tactical security controls are addressing the most relevant threats by cross-referencing the attack graphs back to the proposed mitigations. This can be practically achieved by overlaying security countermeasures at each individual step, and visually inspecting the branches that aren't properly covered by remediations.
> This visualization allows us to evaluate the effectiveness of our security assessment, and to surface the residual risks by identifying the branches with insufficient security controls and suggesting remediations that satisfy the greatest number of branches at once, taking into account their ease of maintenance, business requirements, and budget implications.

It is important to have a system that degrades gracefully under attack. This means that an attacker must compromise many parts of the system that are well protected and compartmentalized from each other in order to do substantial harm. So, think of how to make a system that slowly loses security properties as compromises occur, rather than one that has only “secure” and “insecure” states.

Note that you need to consider lateral movement in a system very carefully when thinking about a system degrading gracefully. If the ability to do X gives one the ability to do Y, then security does not degrade gracefully with respect to these two. If you can only get Y by obtaining the capability for X and Z (which are compartmentalized), then you have actually made the attacker’s life harder than compromising X if their goal is Y.

Another really key thing to do is to protect all access to something sensitive. (This concept is called complete mediation.) If TrashPanda Bank has a well fortified vault entrance with guards, etc. but has an unlocked, unmonitored window in the vault, the attacker will likely just use that. Violations of complete mediation are extremely common in systems where security was not designed in from the start. The reason is that the defenders may be unaware of an inappropriately secured action or be unable to secure some set of actions due to design flaws.

**[> Next Up: Security Assessments](./assessments.md)**
