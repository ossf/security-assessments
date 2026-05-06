# Threat Modeling: Actors

**[< Previous: Threat Modeling 101](../threat-modeling-101.md)**

We need a term to describe the parties in the system that perform all of the actions in the system and might be erroneous, compromised, or just plain malicious. We call these actors and the things they do actions. It is important to enumerate these up front as they are effectively the “players” in the threat modeling game.

Back in earlier days of computing, many computer systems were fairly isolated from each other and programs needed to be secure in this environment. Hence the number of actors was small, often just a server, a client, and an attacker. In modern systems that consist of many distributed and isolated components, the number of actors can be very large.

To see how large modern systems can get, consider a few examples:

- A **package signing system** (such as Sigstore) integrated with a public software registry (such as PyPI). Actors include the registry server, the registry administrators, the certificate authorities trusted to issue keys, parties that control BGP and/or DNS, the developers who publish packages, the CDN that distributes them, the end users downloading them, and outsiders. And this is all without considering Sigstore.  Sigstore itself adds another half dozen or so actors of its own!
- A **mobile application**. Actors include the user, the app store reviewing and distributing the app, the device operating system and its sandbox, the app's backend services, any third-party SDKs (analytics, ads, crash reporting, payments), the user's network, and any other apps on the device that the operating system permits to interact with yours.
- A **command-line tool** distributed through a package manager. Actors include the maintainer, the build system that produces releases, the package manager (and whoever can upload to it), the GitHub or GitLab account that hosts the source, mirrors and CDNs, the user invoking the tool, the shell environment it runs in, and any subprocesses it spawns.
- A **library** consumed as a dependency. Actors include the maintainer, the package registry, downstream applications, transitive dependencies of the library, the CI systems that build downstream apps, and — crucially — the future versions of the library that will be pulled in automatically by version-range resolution.
- A **commercial SaaS product**. Actors include the customer's end users, the customer's administrators, the SaaS provider's operators, cloud infrastructure providers, third-party integrations and webhooks, billing/identity providers, and the broader internet.
- An **internal enterprise application**. Actors include employees with various role levels, contractors, the IT team, the SSO provider, the corporate network, audit and compliance teams, backup systems, and any vendors with privileged access.

In every case the actor list looks daunting at first. The next sections describe techniques for grouping actors with equivalent capabilities so the model stays manageable.

For example, for many systems a party that can control the network has similar capabilities in many cases independent of whether they control routers, BGP, or DNS. So, for threat models that focus on higher level communication properties between actors over higher level network protocols, the distinction of exactly how an actor controls the network may not matter.

## Is It Good Or Bad To Have Many Actors?

You may think that having more actors automatically makes a system have better or worse security properties. There are two factors that lead to having many actors and they impact the security of a system in opposing ways.

The first factor is the security principle that complexity tends to lead to insecurity. Simply put, if an attacker can bypass your system by finding a flaw, the more places the attacker can look, the easier it tends to be. Of course, this doesn’t mean you should remove encryption code or security checks because they make the code longer!  It just means that all other things being equal, more complexity (i.e. actors) tends to lead to more bugs.

The second factor includes the principle of least privilege, that a party should have as little privilege as possible, which is the main argument for compartmentalization. Compartmentalization means that when one portion of a system fails or is compromised, it is separated, much like a ship might have protections so if one part of the hull is breached and the internal part is flooded, it doesn’t automatically spread to the entire ship.  Compartmentalization helps to contain the attackers capabilities from a single compromise. Consider instead a system with a single point of failure; this has fewer actors, but is clearly weaker from a security standpoint.

So, you really cannot read too much into the security of a system by the number of actors alone. You need to understand other key aspects of the system.

## Compartmentalization of Actors

A key aspect to consider is the mechanism by which actors are compartmentalized (i.e., isolated) from each other in a system. After all, if the private keys for Alice and Bob are stored on a file system that both have access to, then if either Alice or Bob is malicious, they steal the other one’s key and then can do anything the other’s private key is trusted to do as well.  So, it is worth discussing why, how, and when actors are separated from each other.

Note that this also may depend on the deployment environment. Perhaps some deployments share storage for Alice and Bob for cost reasons. This is important to highlight, as it will become relevant later when we think about the impact of attacks.

One more note is that having different levels of compartmentalization between actors is common in a system. Most systems have a trusted actor who is responsible for indicating who the other actors are in the system. (This is often a party like a CA, root of trust, root key, or similar.)  As a result, this trusted actor can effectively issue false credentials and pretend to be any other party. In contrast, the other actors in the system may have strong isolation between them, making the act of compromising them effectively independent attacks that must be carried out. This degree to which the isolation between parties contains a compromise can be a critical aspect of the system’s security.

**[> Next Up: Actions](./actions.md)**
