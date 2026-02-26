# DREAD Technique

**[< Previous: Attack Graphs Technique](./attack-graphs-technique.md)**

The properties of an attack will vary based on the avenue of the attack. Some actions an attacker can only perform once before detection, while others an attacker can do repeatedly. Some require specialized skills, while others can be done by anyone.

> [!NOTE]
> **From Improbable to Inevitable**, Commentary by Justin Cappos
>
> It is helpful when thinking about attacks to really think outside the box. One exercise I like to do is to “prove” why an attack couldn’t happen. As I’m reasoning through it, I usually come up with the way in which the attack could occur.
>
> For example, consider TrashPanda Bank. If I’m thinking of how to get into the vault, I might think “It’s not possible because there is a guard during the day and an alarm system (which automatically triggers a lockdown) at night. Even if you get past those, you need to have the manager key and a teller key to open the vault.” I would turn thought into “In order to break into the vault, you need to somehow bypass a guard during the day or the alarm system at night. The attacker needs a manager key and teller key...” and then proceed from there to devise under what circumstances this would be possible.

It is also important to question your assumptions a bit when doing this process. So, you should also consider that this all assumes that the alarm system functions properly, the locking mechanism in the vault operates as designed, the vault was correctly installed and so drilling in, etc. are impractical.

## Different attacks can have different impact

Not every compromise is the same in a system. In some cases an attacker gains only limited access to a system. In others, they may have total control. We talk about these differences by talking about the “impact” of an attack.

You can think of impact as the monetary cost, reputational cost, etc. to an action having occurred. However, it is hard to know an exact value for this. What is the cost of having leaked a large amount of private customer data? Unfortunately, this seems to happen fairly regularly for some large companies and very little actually occurs. In other cases, a company may face lawsuits from investors and customers or fines from regulators after a security breach. This makes the impact easier to quantify.
Using DREAD to estimate the expected impact of a threat.

**DREAD** outlines the impact categories of **D**amage, **R**eproducibility, **E**xploitability, **A**ffected users, **D**iscoverability. This mental model provides a measurable means to quantify the impact of an attack by rating the attack between 0-10 in the impact categories, 0 being no impact and 10 being the highest impact. The final impact is the average of the impact across these categories.

```text
"Impact score" = (Damage + Reproducibility + Exploitability + Affected users + Discoverability)/5
```

Let’s dive into what each impact category means:

- **Damage:** The potential destruction the attack is capable of causing for the assets in the scope. In this context of information security, information disclosure is the damage. 0 stands for no damage, 10 stands for destruction of the information or information system serving this data causing denial of service.
- **Reproducibility:** Reproducibility stands for how easy is it to reproduce this attack? Is it just very juvenile, or does it need experience to find the vulnerability and cause this attack? A rating of 0 is difficult or impossible and 10 refers to very easy to reproduce.
- **Exploitability:** Complimentary to Reproducibility, exploitability refers to what is needed to ensure the attack is successful? Does it take advanced scripting or tools to exploit the vulnerability or is it as simple as adding the string “ OR 1=1? 0 refers to practically infeasible computational power or sophisticated tools & techniques, whereas 10 refers to just an availability of interface to interact with the target application such as browser or command line etc.
- **Affected users:** Affected users refers to how many users are impacted by this attack, ranging from no users (0) to all non-administrator users to all-users and administrators alike (10).
- **Discoverability:** Discoverability refers to how easy it is to find the attack in the first place. Is it evident in the plain sight (for example use of components with publicly disclosed vulnerabilities, authentication in the URL, or directory traversal) or is it hard to disclose? The scores range from 0 (very hard to discover) to 10 (very easy to discover).

| Impact Category  | Description | Ratings Range |
| --- | --- | --- |
| **Damage** | How bad is the damage? | No Damage = 0<br>Complete destruction = 10 |
| **Reproducibility** | How easy is it to reproduce this attack? | Difficult to reproduce = 0<br>Easy to reproduce = 10 |
| **Exploitability**  | How easy is it to cause this attack? | Difficult or practically infeasible = 0<br>Easy to exploit = 10 |
| **Affected Users** | Which users does this attack impact? | No users = 0<br>All users across privilege levels = 10 |
| **Discoverability** | How easy is it to discover? | Difficult to discover = 0<br>Easy to discover = 10 |

DREAD framework eases the threat treatment by putting a number value to the threats in a criteria that novice professionals are also familiar with and could articulate, thus limiting the barrier to entry. While the framework looks seamingly simple, the accurate analysis in complex ecosystems needs extensive information security expertise with up to date knowledge in the domain.

In practice, many security experts argue that discoverability is both hard to quantify and so often gotten wrong.  As a result, it is suggested to use DREAD without trying to estimate D (Discoverability).  To do this, you would always mark Discoverability as a 10.

For more information on the DREAD model, refer to DREAD (risk assessment model) - Wikipedia.

**[> Up Next: Understanding Risk](./understanding-risk.md)**
