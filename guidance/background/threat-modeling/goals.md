# Threat Modeling: Goals

**[< Previous: Actions](./actions)**

<!-- TODO: This section is titled "goals," but I don't understand why. It's about bad assumptions -->

One of the most important things to do in threat modeling is to understand what an attacker can and cannot do based upon the access they have. In our concept of a “game” this is like the conditions by which the attacker gains points (by violating the goals you have for your system) and the legal moves that the attacker can make toward that end.

## System Goals

Assuming that you are being realistic in your attacker model, the stronger the set of moves the attacker can make, the more secure your system is. To understand why, let’s say that TrashPanda Bank made the assumption that all of its employees were trustworthy and did their job flawlessly. If it turns out that one of the employees is malicious or makes a mistake, then you are now outside the bounds of what you have considered in your assessment. It is as though a player of the game you set up made a move that you thought was not legal, when you did your analysis! This means you don’t have a way of understanding what the impact of an attack would be or whether your security will hold.

Note that this does not mean you should not implement controls in the following areas! It just means that long held assumptions on the efficacy of these measures should be restated and that they are better used as part of a layered approach to make things harder, instead of infallible controls. They should not be relied on alone to stop a skilled attacker.

> [!IMPORTANT]
> **Adapting to Modern System Boundaries**
>
> STRIDE has been used for a long period of time, but unfortunately has portions that don’t apply as well to modern distributed systems. So the notion of escalating privilege could be thought better as the ability to move laterally (break the boundaries between actors) in a system. In other words, once an attacker gains access to X, are they able to find a way to get access to Y? This involves a failure to sufficiently compartmentalize X and Y from each other.
> Also, the notions of spoofing and escalation should be thought of in an additional way that a reader may not initially consider. Distributed systems often use a concept called a token (also called a capability in some literature), where an API request contains information to authorize the transaction. In these cases, authentication is not needed. The API request token is sufficient to authorize access. This is much like a movie ticket being sufficient to grant access to a movie. There is no need to check the attendee’s identification, so long as they possess a valid ticket. So, for Eve to gain access to Bob’s data, it doesn’t necessarily mean that she must know Bob’s password. She may have just gained access to a token that some service uses to perform actions on behalf of Bob. She may even confuse the service into doing the actions she wants using Bob’s token. Of course, if tokens are not used and service X is just always trusted to do a set of actions, spoofing and escalation become trivial once you compromise a service!

## Common Assumptions

To make it simpler, there are a set of standard assumptions that most systems make in the current era (this was originally written early 2023). A note for any future reader, these assumptions tend to evolve over time and so may not be reasonable while you are reading this document.

### Leadership will not compel the organization to perform actions that violate the security goals of the system

This includes the government, company management, or a similar agency will not compel the organization to perform actions that violate the security goals of the system.

While it may seem a fanciful attack to some readers, this is a legitimate attack risk that many companies have faced and in fact do (often silently) face today. For a real world example, consider the pressure on Apple to create a malicious update and unlock the San Bernardino shooter’s phone [Wikipedia: Apple–FBI encryption dispute]. However, most security systems are designed so they will fail in such a case and allow the government, company leadership, or a sufficiently large set of malicious insiders to violate its security goals.

### Cryptographic algorithms that are widely thought to be secure, are secure

This includes public/private cryptography, symmetric key algorithms, cryptographically secure hash algorithms, etc.

In practice, contests like the ones that NIST holds to choose cryptographic algorithms tend to have produced excellent results. Even when algorithms fail, it tends to be a slow breaking of the algorithm. The breaking of the algorithm is often possible first by parties with a large quantity of computational resources instead of a sudden moment where anyone can trivially break the algorithm. Other standards bodies have a much more mixed record, in particular if their security systems are effectively designed by committee. Look carefully for broad peer review of cryptographic algorithms and security designs, as NIST performs, as an indicator of quality.

### Hardware memory protection mechanisms work as designed

After SPECTRE and MELTDOWN, people in the community realized that there are some ways to use rare cache / memory error behaviors to bypass security protections. For example, a program could read memory in the operating system kernel or in another program. A series of defensive code changes now makes these attacks infeasible on modern hardware (as we understand it). The assumption that memory protections work is common not because it is universally thought that memory protection will absolutely hold in all cases, but largely because not having this assumption makes it too challenging to design security systems. It essentially makes it infeasible to do compartmentalization on a single piece of computing hardware and may make it feasible to cause information disclosure from any component on the same physical hardware. As this is currently an area of active research by hardware security researchers and chip makers, the protections and our understanding of the risks in this domain are likely to evolve over time.

> **Future-proofing While Maintaining Compatibility**
>
> Note that today, these assumptions are being relaxed by some modern security systems like TUF. For example, TUF supports multiple cryptographic algorithms and has a built-in way to add and remove cryptographic algorithm support while maintaining security properties. This enables secure migration to new algorithms either proactively, or as the need arises.
>
> For example, while there is support in TUF for post-quantum cryptographic algorithms, many adopters may not have enabled it. A TUF repository can enable post-quantum crypto and re-sign its metadata using both algorithms, thus allowing current users to securely transition to the new algorithm and protecting all users versus post-quantum attackers.

### An attacker cannot hack a specific component or system

Modern systems tend to have so much code and tend to use so many libraries, that this just isn’t a reasonable expectation. Even a “proven to be secure” microkernel like SeL4 has had security bugs found in it [SeL4 issue #85, SeL4 issue #86, seL4 Version 9.0.0 Release Notes]. It is important to assume code could have bugs, especially large components, and to design your system to have different isolated compartments so that your system’s security will degrade gracefully when components are successfully breached. This assumption seems to be on the way out, but some systems being created today do still use this assumption. You should assume that such compromises are a matter of when, not if [TAG Security Catalog of Supply Chain Compromises].

### A key or other secret will never be leaked, compromised, misgenerated, etc

Incidents violating this assumption are common [TAG Security Catalog of Supply Chain Compromises]. Modern systems should design revocation mechanisms that retain trust even when an attacker knows a secret and is a man-in-the-middle. Ideally, one should also design the system to prevent substantial harm while you work to address a secret disclosure.

### Multifactor authentication (MFA) using SMS is a sufficient barrier

This assumption isn’t actually a bad one for MFA that does not use SMS. An organization using authenticator apps or hardware tokens seems to do quite well from a security standpoint (barring a few minor hiccups [Wired Magazine: The Full Story of the Stunning RSA Hack Can Finally Be Told], which do not seem to be indicative of a trend). However, the same is not true of SMS based MFA systems, which have been shown to be vulnerable to attack. So, do try to have your organization not only mandate MFA, but choose a means of performing it which provides a level of security appropriate for what you are protecting.

### The complexity of parsing code for a complex format is not particularly relevant

This is a common mistake that organizations make, where the code to parse data formats or keys becomes a major liability. The number of X.509 certificate parsing errors alone that have led to security vulnerabilities is astonishing [MatrixSSL: Security Vulnerabilities]. A related problem in this space is that even just getting a format serialized into a consistent format is a more difficult challenge than many developers initially realize. So the complexity of the data communication and storage format should be a major concern, especially for sensitive API calls and components.

### Operating system user access control protections like file permissions are an impassable barrier

It turns out that it is often not that difficult to escalate privilege when gaining access to an account on a system. The reason is that the operating system’s system call boundary is massive and hard to employ effective controls on. You should not willingly let attackers into a system and rely on user permission bits, file ACLs, etc. as your only means of protection. Rather think of these as a barrier that may slow or trip up an attacker, but are not reliable as a line of defense.

### The network cannot be tampered with

It turns out that becoming a man-in-the-middle is possible in many scenarios, including wireless attacks in a coffee shop, BGP route hijacking, DNS cache poisoning, etc. While it isn’t trivial for any person to become a man-in-the-middle for a network path between two randomly selected computers, it certainly isn’t unobtainable for a large and important class of attackers.

### Software provided by dependencies are secure so long as we take care when adding them

Attackers in some ecosystems have begun attacking software projects by taking over a dependency and adding malicious code. In other cases, a dependency is simply neglected for a long time and does not receive security patches. In yet other cases, an organization simply forgets or neglects to update dependencies to a later version so that a vulnerable version remains in use. Like the software your organization writes itself, dependencies need care, examination, and attention so that they do not become liabilities.

### Firewalls keep out bad guys

Firewalls are an important tool for helping to provide compartmentalization of networked components. However, experience shows that they are insufficient on their own. In practice, many attacks involve an attacker bypassing firewalls and network monitoring systems to access things that should have been restricted. This is not surprising given how difficult it is to write a policy that stops exactly all of the “bad things” and allows exactly all of the “good things”. So, it may be helpful to think about this as a way to increase the difficulty for an attacker rather than as a means for stopping them outright.

### Antivirus stops malware on end hosts

In much the same way, antivirus software on client machines largely just helps to make certain compromises less likely, but comes with its own risks and concerns. Today many experts recommend only using the antivirus software that comes with your operating system (if applicable). However, purchasing commercial antivirus software gives questionable benefits and does come with some added risk.

### Trained users will to choose and manage sufficiently secure passwords

This is patently false, which is one reason why multi-factor authentication is an option or even a requirement for many systems. Strong password guidelines for users are important. Users should also be incentivized to use tools like password managers.

> [!NOTE]
> A Methodology for Identifying Discrepancies with Respect to Privacy Regulations, Commentary by Ragashree Shekar
>
> In the current landscape, with more and more data generated from each of us through the surplus connected devices we use, it also gives an opportunity to gather more and more data about us and utilize it to enhance their business. It is about time privacy is engineered into each project we build that collects personal, health or protected user information not just to comply with the regulations, but also to protect user’s right to privacy. LINDDUN[1] is a privacy engineering framework that helps model the system, find and manage the threats associated with this system. LINDDUN categorizes the threats into 7 categories such as Linkability, Identifiability, Non-repudiation, Detectability, Disclosure of Information, Unawareness, and Non-compliance. Let’s look at each one of them:
>
> - Linkability: Whether an attacker is able to link two items of interest without knowing the data subject [2] corresponding to these items
> - Identifiability: Whether the attacker is able to identify a data subject from a set of data objects through items of interest
> - Non-repudiation: A data subject cannot deny an action
> - Detectability: An attacker is able to distinguish whether an item of interest about a data subject exists or not, regardless of being able to read the contents itself
> - Disclosure of Information: An attacker is able to learn the content of an item of interest about a data subject
> - Unawareness: The data subject is unaware of the collection, processing, storage or sharing activities (and the corresponding purposes) of the data subject’s personal data
> - Non-compliance: The processing, storage, or handling of personal data is not compliant with legislation, regulation, and/or policy
>
> A few notes to consider. First, Identifiability and Linkability are closely associated with each other as lack of anonymization affects results in identifying 2 data subjects or linking two different data objects.
>
> Second, Awareness is a big part of the privacy laws, regulations and policies and failing to inform the data subject of what data about them are being collected, how it would be processed/used, who else would it be shared/sold to, and to let the data subjects decide if they want to opt-in. Thus unawareness is a subset of non-compliance.
>
> However, it is difficult to assess the impact of a vulnerability by using these criteria. This method is intended more for compatibility analysis with respect to privacy regulations than for searching for technical vulnerabilities.

## System Non-goals

In addition to goals, another key aspect to consider are things that you consider to be non-goals of the system. These are “illegal moves” in the game. They tend to come in two types, the first being things that you simply do not care about if they occur.

For example, TrashPanda Bank is likely well aware that people off the street may wander into the bank. Some of those people may steal a pen or the deposit sheets that are left out on the desks. They may use the bathroom and enjoy the heat / air conditioning without being a customer. However, TrashPanda Bank may also just assume that those costs are minimal and any effort to deter such actions would have a negative impact on the experience of other customers. So, solving these types of issues may be a non-goal.

The second type of common non-goal is one that seems too fanciful for the attacker to carry out. For example, let’s say in order to break into TrashPanda Bank, the attacker will become president of the country and launch a nuclear strike on the vault. Whether or not the vault resists such an attack, any surviving members of the company are likely to be focused on things other than the vault. So, TrashPanda Bank could consider worrying about such an attack a non-goal.

## Attacker Goals

Another way to frame the system goals is to talk about what an attacker may want to accomplish. This is sometimes (mis-)used to say that these goals are the only things an attacker would want to do, and so the system's goals should just be to prevent those. Unfortunately this line of reasoning will often miss cases because it is assumed the attacker will simply not care to perform them. In the movie The Dark Knight, there is a famous (and long) story told by Alfred, which concludes with the statement “Some men just wanna watch the world burn”.

You should assume that someone will have the temptation to do a bad thing if it is possible to do so without a massive amount of skill and resources.

Additionally, you should assume that a compromise may be the result of a negligence rather than intent. If the new guy deletes a production database, many other layers of security have been neglected prior to that mistake.

## Using STRIDE To Enumerate Attacks and Goals

Fortunately, security researchers have long understood that it is too easy to miss computer security concerns when threat modeling.

To aid in going through different cases, there is a model called STRIDE. STRIDE stands for the following properties:

- Spoofing: The act of using another’s credentials. This can be for many purposes, such as gaining access to a resource they should not have access to, or masking the source of an attack. Commonly, this is done by authenticating as a different user when performing an activity.
- Tampering: The act of modifying information in a malicious way. This depends a lot on the project, but can involve things like replacing a user’s data with something else, manipulating account balances, or changing log information.
- Repudiation: The act of performing an action but asserting you did not in situations where others cannot prove otherwise. This involves situations where the attacker makes tracing the cause of a problem infeasible.
- Information Disclosure: This is when you make private information public. Situations where this occurs typically involve data leaks of user account data, private messages, financial details, etc.
- Denial of Service: This is where an attack prevents legitimate users from accessing information or services they are supposed to have access to. This can be very localized, such as locking a user out of their account, or very broad, such as bringing down an entire website. Attacks of this type are sometimes done using a set of computers that work together to attack a system. An attack of this type by a distributed set of computers is called a DDoS attack (Distributed Denial of Service attack), which you likely have heard mentioned before.
- Escalation of Privilege: This is the act of gaining more authorization to perform actions in a system that should not be granted. Note that while Spoofing focuses on appearing to be someone else, Escalation of Privilege focuses on using an identity you have to do things which should not be authorized. For example, consider the administrative assistant for TrashPanda’s CFO. For withdrawals over a certain amount, the CFO may be required to place her signature on the transaction confirmation. However, if the administrative assistant for the CFO states that the CFO authorized it, the teller may (incorrectly) still complete the transaction. This is a case where the administrative assistant has escalated his privilege to do an action he was not authorized to perform.

| Attack                  | Property Violated        | Impact                         |
|-------------------------|--------------------------|--------------------------------|
| Spoofing                | Authentication           | Misdirected identity           |
| Tampering               | Integrity                | Unreliable data                |
| Repudiation             | Non-repudiation          | Lack of ownership for actions  |
| Information disclosure  | Confidentiality, Privacy | Lack of confidentiality        |
| Denial of service       | Availability             | Unreliable service             |
| Escalation of privilege | Authorization            | Grants Unauthorized access     |

> ![NOTE]
> Tracking Trash Pandas with Data Flow Diagrams Commentary by Ann Wallace
>
> In my experience, a Data Flow Diagram (DFD) is invaluable for threat modeling, providing a detailed view of data management within a system to identify and mitigate security risks. DFDs give a thorough and detailed view of how data is managed within a system, which is critical for identifying, examining, and mitigating potential security risks.
>
> These diagrams portray data movement within a system, shedding light on vital areas where data is entered, exits, and is processed. This level of detail is key in spotting vulnerabilities. DFDs are especially adept at uncovering potential points where an attacker could access or extract data. They cover the full spectrum of the system we're analyzing for threats, embracing all the internal and external components, like various entities, actors, data storage, and data flows.
>
> DFDs also enhance communication, clarifying system data handling and risks to stakeholders, aiding in prioritizing security measures. Clear, understandable DFDs are vital for all involved to identify key components and understand control paths.
>
> For instance, a DFD for TrashPanda Bank would map money flow, highlighting entry/exit points, customer involvement, asset storage, trust boundaries, and processes like bank teller and ledger operations. This facilitates comprehensive threat analysis, examining potential data interception/manipulation points, and assessing security measure effectiveness, ensuring robust protection against security threats.

**[> Next Up: Attack Graphs](./attack-graphs-technique.md)**
