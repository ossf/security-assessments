# Comprehensive Coverage

**[< Previous: Understanding Risk](./understanding-risk.md)**

One common problem is that it is easy to miss one or more cases when doing threat modeling. With distributed systems that have many components, this problem becomes much more common. The reason is that there are many different combinations of components that could be compromised by an attacker and used collectively to do nefarious things.

For example, suppose that in TrashPanda Bank suppose that the vault is locked and may only be unlocked by the manager’s key and a key from any one of the tellers. People going into the vault are also checked by a security guard to ensure they are escorted in by the manager. All vault entry and exit times are logged by the security guard. The security guard notifies the manager when the customer leaves so that the manager and teller may retrieve their keys and re-lock the vault, which the guard confirms to the manager.

If you threat model this situation, you also need to consider cases where a malicious security guard can work with a malicious customer to do something bad, by not logging their entry. Suppose the customer enters the vault and starts a fire or does some similar action. If the customer isn’t logged, it will not be possible to know who to blame. Even worse, the guard could potentially add a log entry to indicate that a different customer entered, blaming them for the incident. The system has lost forensic traceability (the ability to know what happened) of these events due to having insufficient protections over the security guard being malicious and working in coordination with a malicious customer.

Similarly, if a teller and guard work together, they could simply fail to re-lock the vault after a customer leaves. The teller could fail to perform the action and the guard could simply say to the manager that the vault was re-locked.

## Attack Matrices

As the simple example above shows, there can be a number of fairly complex interactions between actors when they could be malicious and act in unison. We could just write one big massive block of text to describe all of the interactions in the system and how different malicious actors can cause harm. This would be really unwieldy to read and to ensure we didn’t miss any cases, so instead we recommend you write it in a way that a reader can more easily reference.

To do so we use a representation called an attack matrix. An attack matrix is typically written so that the rows of the matrix correspond to a set of actors that are under the control of the attacker. The columns often represent different security designs that you may want to evaluate or things like different capabilities the attacker may have. What you are effectively doing is putting the text for what an attacker can do in the part of the matrix that corresponds to that set of capabilities.

Let’s look at a few example attack matrix entries for the previous section’s example vault at TrashPanda Bank.

| Malicious Actors | Impact |
| --- | --- |
| Customer + guard | Loss of forensic traceability from customer malicious actions. Able to falsely blame other customers for malicious actions |
| Teller + guard | Vault may remain unlocked after a customer visits the vault, when this teller and guard are working |

## Reducing the number of actors

Note that if we continue to fill out the matrix above, there will be quite a few rows due to the fact that there are `2 x number of actors` different combinations of malicious actors.

When the number of actors is even moderately large (like 5 or 6), this can be overly burdensome. Fortunately for us, in most cases the number of interesting sets of actors is actually quite small. For example, if the teller, guard, and manager work together, they can really do as they please and so a customer also being malicious really doesn’t add any further impact to the attacks that can be performed.

A few useful rules to consider:

1. A superset of a set of malicious actors can do at least the union of all subsets of those actors. In other words, if a teller+manager can have impact X, a manager+customer can have impact Y, and a teller+customer can have impact Z. The manager+customer+teller can have any impact from X, Y, and Z. In fact, the impact may be greater than this because X, Y, and Z may be limited by checks the non-malicious party performs.
1. It is common for many rows to subsume other rows. This is for two reasons. First, once a certain level of compromise is reached, usually the attacker effectively has full control of the system. In this case, additional compromises do not change the security impact of the attack. Second, some parties are so limited that their ability to harm a system has minimal added impact. So, whether they are malicious or not is inconsequential.
1. Many capabilities are quite easy to get in practice. So, if this is the case, it may be better to assume that an attacker already has those capabilities in all cases in the matrix. For example, it is common to assume a man-in-the-middle attacker who can intercept and modify network traffic. Breaking the table down into attackers that can and cannot do this may make the table unnecessarily long.

A question arises, if you have different ways to get the same impact, how do you label the row? In an attack matrix, what you do is to take the minimal set of actors that will cause a certain impact and label the row with it. This indicates that any attacker with at least these parties compromised, can perform this action.

Notice also that in some cases the impact of a compromise on different, disjointed, parties could be the same.

For example, suppose that teller+guard and manager+guard have the same impact. In this case, it is sensible to write the row as `teller+guard` OR `manager+guard` to save space instead of having two duplicate rows.

These space saving tips do not fully solve the problem though. Consider that the matrix we wrote before has the customer+guard row (such as above) as well as the potential for us to add a teller+manager+guard row. How do you know which row of the matrix to use? To make this clear to the reader you should sort the attack matrix so that the most impactful attacks are lower in the matrix. When reading an attack matrix and reasoning about a scenario, move down the matrix to find the lowest row that you match and then use this cell to determine the impact.

For more information about threat matrices, here are some references for further reading:

- G. Almashaqbeh, A. Bishop and J. Cappos, "ABC: A Cryptocurrency-Focused Threat Modeling Framework," IEEE INFOCOM 2019 - IEEE Conference on Computer Communications Workshops (INFOCOM WKSHPS), 2019, pp. 859-864, doi: 10.1109/INFCOMW.2019.8845101. [(Link)](https://arxiv.org/abs/1903.03422)
- Matt Tatam, Bharanidharan Shanmugam, Sami Azam, Krishnan Kannoorpatti, "A review of threat modelling approaches for APT-style attacks", Heliyon, Volume 7, Issue 1, 2021, ISSN 2405-8440,
[(Link)](https://www.sciencedirect.com/science/article/pii/S2405844021000748)
- Rajesh Gupta, Sudeep Tanwar, Sudhanshu Tyagi, Neeraj Kumar, "Machine Learning Models for Secure Data Analytics: A taxonomy and threat model", Computer Communications,
Volume 153, 2020, Pages 406-440, ISSN 0140-3664,
[(Link)](https://www.sciencedirect.com/science/article/pii/S0140366419318493)
- Zhang, L., Taal, A., Cushing, R. et al. "A risk-level assessment system based on the STRIDE/DREAD model for digital data marketplaces." Int. J. Inf. Secur. 21, 509–525 (2022). [(Link)](https://doi.org/10.1007/s10207-021-00566-3)

**[> Next Up: Detection & Tracing](../response/detection-and-tracing.md)**
