# Security Basics

**[< Previous: Security Assessements and Audits](../assessments-and-audits.md)**

There are so many foundational concepts and technologies you need to understand to reason about security of a cloud native application, that describing them well would require another entire book’s worth of material. Rather than replicate that material here, the reader is directed to resources that contain this information. If you encounter an unfamiliar term in the text, kindly take the time to look it up and understand it.

Most fundamentally, you should understand key concepts like integrity, non-repudiation, privacy, authentication, authorization, and trust. The Cloud Native Security Lexicon (available at tag-security/security-lexicon at main · cncf/tag-security (github.com)) has a quick overview of basic terms and concepts in computer security which covers these items.

For encryption, there are a lot of concepts you need to understand and cryptographic systems are very complex. Fortunately, you really just need to understand how to use them correctly and their strengths and weaknesses, instead of why they were designed in the way that they were. You will need to understand (at a minimum) public key cryptography, secret key cryptography, secure hash functions, key length, key distribution, root of trust, certificate formats (i.e., X.509), and certificate authorities. Depending on what you are assessing, understanding trust delegation, HMAC, post quantum cryptography, transparency logs, forward secrecy, and similar concepts may be useful.

>[!IMPORTANT]
> **Critical Perspective on Broad Promises**
>
> Beware of systems making broad promises due to the use of blockchain, Web 3.0, or decentralization. To date, the proponents of these systems have claimed far greater benefits than what the core technology has been able to deliver.

As an example, a proof-of-work blockchain is fundamentally a way to keep a distributed, append-only log amongst a set of distributed computers that don’t want to have a trusted centralized party. It is extremely slow and computationally wasteful compared to a centralized trusted server, but there is no longer a single point of compromise. That is, if you assume that the computational nodes have a protocol that provides this property, that the protocol is implemented correctly, and that some threshold (commonly 1/3 or 1/2) of the computational power isn’t held by evil people, etc. It also, by itself, doesn’t ensure that the information in the blockchain is actually valid or useful.

Interestingly enough, a transparency log uses a lot of the same mechanisms as a blockchain and thus has some similar weaknesses. However, transparency logs currently don’t have the same stigma in the security community in part because the deployment environment and stakes are different. There are large deployments of transparency logs today but they are early enough in their lifecycle that as a community, we really don’t fully understand how and when these systems fail to provide adequate security in the same way we do the other technologies in this section.

For computational security on a system, you need a basic understanding of access control. This means understanding compartmentalization / isolation as it relates to the operating system or container environment you are using. Access Control Lists (ACL) systems, file / device permissions, su (superuser) ability, system call filtering (seccomp), and capability / tokens are all very important to understand conceptually. Depending on your environment, knowledge of HSMs (Hardware Security Modules) and TPMs (Trusted Platform Modules) may also be relevant.

There is an additional set of things to understand around user identity, authentication, and authorization. This involves concepts like multi-factor authentication (also called two-factor authentication), hardware tokens (e.g., Yubikeys), and OIDC (a way to log in to a system via authentication through a third party like Google or Facebook). It is key to understand how users are identified and how this is tied to logging events for auditing purposes.

The last important concept to understand is the fundamental ways in which people design secure systems. Usually, you can find security design flaws by looking for situations that violate these principles and then reasoning about what problem occurs as a result. So understanding concepts like the principle of simplicity, least privilege, fail-safe defaults, least common mechanism, minimizing secrets, open design, complete mediation, and least astonishment [Saltzer and Schroeder, The Protection of Information in Computer Systems] are really fundamental and things every person thinking about security should internalize.

> [!IMPORTANT]
> **When 'Simpler' Does Not Mean ‘More Secure’**
>
> These principles are not fundamental “laws” of computer security which should never be violated. They are guidelines that often lead to security problems when the are violated.

For example, the principle of simplicity indicates that the simpler the component, the easier it is to reason about it and thus secure it. Suppose that TrashPanda bank’s system designer learns of this and decides to remove the need to verify client ID cards to simplify the system. Now anyone can withdraw money from anyone else’s account, trivially! This “simplification” has clearly made the system’s security worse.

So, instead think about the principles when looking at a design and reason if the security would be better or worse if they were followed. Usually, following the design principles will guide you toward security.

**[> Next Up: Threat Modeling 101](./threat-modeling-101.md)**
