# Threat Modeling: Actors

**[< Previous: Threat Modeling 101](../threat-modelling-101.md)**

We need a term to describe the parties in the system that perform all of the actions in the system and might be erroneous, compromised, or just plain malicious.  We call these actors and the things they do actions.  It is important to enumerate these up front as they are effectively the “players” in the threat modeling game.

Back in earlier days of computing, many computer systems were fairly isolated from each other and programs needed to be secure in this environment.  Hence the number of actors was small, often just a server, a client, and an attacker.  In modern systems that consist of many distributed and isolated components, the number of actors can be very large.

To see how large modern systems can get, consider an assessment for the [Sigstore project](./#TODO) and the way it might get integrated into an open, community software repository like [PyPI](./#TODO), a community repository of software for the Python programming language.  The actors include the PyPI server, the administrators of PyPI, the CA(s) trusted to issue PyPI’s public key, parties that control BGP and/or routers, parties that control DNS, the developers who use PyPI for their software, the CDN that distributes PyPI software, the users downloading that software, and outsiders.  If you think it seems overwhelming, consider also that at this point we haven’t even listed the parties for Sigstore, which would be another 10 or so actors!

However, in coming sections, we will describe techniques that will enable one to quickly categorize groups of actors as equivalent, which helps us to keep this manageable in practice.  For example, for many systems a party that can control the network has similar capabilities in many cases independent of whether they control routers, BGP, or DNS.  So, for threat models that focus on higher level communication properties between actors over higher level network protocols, the distinction of exactly how an actor controls the network may not matter.

## Is It Good Or Bad To Have Many Actors?

You may think that having more actors automatically makes a system have better or worse security properties. There are two factors that lead to having many actors and they impact the security of a system in opposing ways.

The first factor is the security principle that complexity tends to lead to insecurity.  Simply put, if an attacker can bypass your system by finding a flaw, the more places the attacker can look, the easier it tends to be.  Of course, this doesn’t mean you should remove encryption code or security checks because they make the code longer!  It just means that all other things being equal, more complexity (i.e. actors) tends to lead to more bugs.

The second factor includes the principle of least privilege, that a party should have as little privilege as possible, which is the main argument for compartmentalization. Compartmentalization means that when one portion of a system fails or is compromised, it is separated, much like a ship might have protections so if one part of the hull is breached and the internal part is flooded, it doesn’t automatically spread to the entire ship.   Compartmentalization helps to contain the attackers capabilities from a single compromise.  Consider instead a system with a single point of failure; this has fewer actors, but is clearly weaker from a security standpoint.

So, you really cannot read too much into the security of a system by the number of actors alone.  You need to understand other key aspects of the system.

## Compartmentalization of Actors

A key aspect to consider is the mechanism by which actors are compartmentalized (i.e., isolated) from each other in a system.  After all, if the private keys for Alice and Bob are stored on a file system that both have access to, then if either Alice or Bob is malicious, they steal the other one’s key and then can do anything the other’s private key is trusted to do as well.   So, it is worth discussing why, how, and when actors are separated from each other.

Note that this also may depend on the deployment environment.  Perhaps some deployments share storage for Alice and Bob for cost reasons.  This is important to highlight, as it will become relevant later when we think about the impact of attacks.

One more note is that having different levels of compartmentalization between actors is common in a system.  Most systems have a trusted actor who is responsible for indicating who the other actors are in the system.  (This is often a party like a CA, root of trust, root key, or similar.)  As a result, this trusted actor can effectively issue false credentials and pretend to be any other party.  In contrast, the other actors in the system may have strong isolation between them, making the act of compromising them effectively independent attacks that must be carried out.  This degree to which the isolation between parties contains a compromise can be a critical aspect of the system’s security.

**[> Next Up: Actions](./actions.md)**
