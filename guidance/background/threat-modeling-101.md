# Threat Modeling

**[< Previous: Security Basics](./security-basics.md)**

Security is one of the most critical properties to have in computing today. Unfortunately, it is also one of the most misunderstood. A common mistake people make it to tout something as “secure” or “insecure”. This doesn’t make a lot of sense because it is missing an important context: the scenario.

The scenario in many non-security real world situations is something that is implicitly defined. For example, if I say “my car is reliable'', you can assume that it almost certainly will not break down on the way to work. However, you should not expect that a “reliable” car would make a good submarine or perform well on Mars. Performing well on Mars is just not what is implied by a general statement of a car’s reliability.

While usually, one could just look at likely scenarios and determine the rarity of events, there is another aspect of security which makes this not work well: the intelligent adversary. In security, one assumes that an adversary has some ability of control over the system or environment and crucially, that an intelligent adversary will choose to set things up in a way that favors them. So, you may have set up the communication properties on your network to detect or correct 99.9999% of errors in random noise. But unless some secret prevents the attacker from knowing how your error correction works, the attacker can generate network traffic that makes your error correction useless.

> [!IMPORTANT]
> **Defining Scenarios**
>
> A fundamental aspect of threat modeling is the ability to frame and understand the various scenarios in which a system will operate. A key question that often guides this understanding is, "What are the intended use cases of a system, and where should it not be used?" This line of inquiry doesn't just establish the parameters within which a system is expected to perform but also helps to define the boundaries of its reliable operation.

Challenging yourself and your team to identify these “out of scope” scenarios or non-uses can be revealing. It prompts a closer examination of implicit assumptions and potential weaknesses. For instance, you could consider a system you're familiar with and ask, "What would be the 'submarine or outer space’' equivalent for your system?" Is syscall inspection suited for inspection of ingress traffic? Is a mutating admission webhook served at enforcing kernel security? This kind of hypothetical questioning can uncover overlooked vulnerabilities and lead to a more robust design.

This exercise not only broadens the scope of traditional threat modeling but also encourages a proactive approach to security. By contemplating extreme 'out-of-scenario' uses, we can better understand the full range of risks a system may face and fortify it against more than just the probable threats.

One way that we reason about security in a rigorous way is a process called threat modeling. Threat modeling is sort of like setting up a game between the defender and the attacker. The threat model describes the properties you are trying to provide and the capabilities of the attacker. If the attacker is able to find a way to defeat the defender’s desired security properties, this is a viable avenue of attack. We call such a successful attack, a compromise, and the weakness that lets an attack occur, a vulnerability.

Note that the term bug and vulnerability are not the same thing. While many bugs do enable an attacker to launch a successful attack, many bugs are just anomalous, benign behavior.  Similarly, a design flaw can cause a correctly implemented system to have a vulnerability. So, there need not be a bug in order to have a vulnerability.

**[> Next Up: Threat Modeling Actors](./threat-modelling/actors.md)**
