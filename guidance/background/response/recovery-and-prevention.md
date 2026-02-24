# Recovery & Prevention

**[< Previous: Recovery & Prevention](./recovery-and-prevention.md)**

Downstream from detection and tracing is recovery, and then that concept naturally leads us back around to the thought of preventing a breach in the first place.

## Recovery

Once you know an attack has occurred, a major goal is to get the attacker out of your system. In some cases, this is very difficult. If an attacker gained the ability to install software as root on your devices, for example, then they could have installed basically any software (rootkits, firmware, etc.) and so you may need to start over.

Fortunately well designed systems usually have the ability to securely recover from a compromise. Note that it is common to assume that an attacker could act as a man-in-the-middle for your users. So, if you have a compromise of a system, you can’t securely revoke or restore trust using the same key that was compromised. So you will need users to leverage a different key, perhaps using the root of trust, which is compartmentalized and more privileged to securely recover the system to a secure state.

Recovery is a very important property to have. However, in general, it isn’t possible to recover in every case. After all, if every actor in a system is compromised, it doesn’t seem possible to ever move back to a state with a trustworthy root of trust without starting anew.

## Prevention

Another means to deal with an attack is simply to prevent it from being effective. The previous sentence, using the word “simply” is a bit misleading because this is often one of the most difficult things to do. Well designed systems have this property for most types of attacks.

Note that you need to carefully be able to argue why you protect against a set of attacks. This includes in what scenarios an attacker is prevented from doing an action. Once again, being rigorous and clear about limitations are absolutely key.

> [!IMPORTANT]
> **Aiming for Full Prevention**
>
> Some modern systems provide prevention of only certain attacker actions, in only certain scenarios. They may prevent information from being valuable after a certain point of time or from a key from being exfiltrated after a successful attack. (See HSMs, the concept of perfect forward secrecy, and ephemeral keys, as examples.) These properties are certainly nice to have, but ideally you want full prevention as a goal.

## Recovery vs. Prevention

A natural next thing to consider once you understand the different means by which you can handle a compromise, is whether there is an implicit order so that prevention is always better than detection, for example. It turns out that this is not always the case. For example, suppose that TrashPanda Bank could detect Eve embezzling a small amount of money. Alternatively, they could have a means to prevent Eve from doing so, but not detect her attempt. In this case, TrashPanda Bank’s management may feel it is worth the small financial loss to know Eve is unreliable and fire / prosecute her.

To consider another example, let’s say that TrashPanda Bank has a super alarm system that can detect when the view of any sensor is blocked momentarily. Unfortunately, TrashPanda Bank is set near a set of cherry blossom trees and when the blossoms fall, they block the sensors, leading to a ton of false alarms. Suppose that TrashPanda set the alarm to automatically ring the police when it was triggered. After being summoned several times, the police are unlikely to respond to alarms for TrashPanda in the future, leading to the police ignoring an alarm on the vault. So, in this case, the security system’s drawbacks may actually degrade security.

> [!IMPORTANT]
> **Overprotection Sometimes Considered Harmful**
>
> While the example above is a bit silly, adding a security mechanism does sometimes degrade security in practice. It used to be thought that changing passwords frequently was an important security practice. It was later shown that this made users choose weaker passwords, reuse passwords more often, and led to companies providing more vulnerable means to recover lost passwords.
>
> However, this all being said, there is actually a practical hierarchy of what defender’s capabilities are usually preferable. Usually prevention is the best because it actually stops the negative outcome from occurring at all. Recovery is really, really important for all but the most unlikely of events. Note that manual effort for recovery is common which is often reasonable. However, this implies that this also should be a rare act to avoid overburdening the poor person who does the recovery. Detection is important, but can be overwhelming if it is overly broad. If you can detect problems, but cannot forensically trace the cause, it can lead to a lot of extra work.

So, while it is not always true, in general:

```text
Prevention > Recovery > Detection w/ Forensic Traceability > Detection > Forensic Traceability
```
