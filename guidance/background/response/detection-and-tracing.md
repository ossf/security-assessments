# Detection & Tracing

**[< Previous: Comprehensive Coverage](./comprehensive-coverage.md)**

The core concept of defensive security is to take things that are damaging and either make them less likely or less impactful.

To better reason about this, we will look at several capabilities that a defender often retains even when attacked. Note that this is not an exhaustive list, but these are the most common properties that exist today, so deserve emphasis. The capabilities we will discuss in detail are detection, non-repudiation, recovery, and prevention.

## Detection

Another important aspect is what is done when an attack occurs. In the worst case, the attacker could try repeatedly and the defender would never realize an attack is occurring. This is very common if the attacker can download and run the defender’s software locally on their own infrastructure because then the attacker can experiment with a running copy of the system. This is basically the norm for open source software and is also common for proprietary software.

If a system is attacked, ideally you’d like to know it. This is where detection comes in. Detection is any means by which you can know you’ve been attacked. Common ways to know this involve logging API calls, examining network traffic, and looking for anomalous events by collecting measurements of anything deemed as deviation from standard system behavior.

It is common for many systems to be constantly under attack. What is more important is detecting successful attacks and determining their severity. A person who steals a pen from TrashPanda Bank is less of a concern than one who steals the vault keys from the manager!

## Non-repudiation / Forensic Traceability

Once an attack has succeeded, you may have an intruder in your systems. You may need to look through what has occurred to understand which actions an intruder performed and which were legitimate actions by the normal system.

If in TrashPanda Bank, Bob the teller says that Alice the manager asked him to give her the contents of his cash drawer, but Alice denies this, how do we know who to believe? Well, if Bob got a receipt or there exists a video recording then there may be a way to prove who is lying and who is honest.

In computer security, this is usually done by having something called non-repudiation. This is where a statement is made such that it later can be proven that a specific party actually made it. This is usually done by the party (Alice, let’s say) signing it with a private key that only she owns. Then any party with Alice’s public key can verify that Alice (or a party who compromised her private key) made that statement.

So, as you can see non-repudiation is essential for post-attack forensics and should be a goal for any systems with multiple actors.

Note, it is possible to have differing amounts of non-repudiation and detection in a system. If TrashPanda Bank counts money for the whole bank at the end of each day, the bank may be able to quickly detect if something does not add up. However, this does not mean that they will know who is responsible. Conversely, if TrashPanda Bank has video recordings for all time, but never checks them, then they will not detect problems well, but when they do can figure out exactly what occurred.

**[> Next Up: Applying Mitigations](./applying-mitigations.md)**
