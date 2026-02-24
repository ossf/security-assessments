# Understanding Risk

**[< Previous: DREAD Technique](./dread-technique.md)**

A very useful concept when thinking about security assessments is the concept of risk. Rather than simply categorize things as possible and impossible, risk lets us try to understand how likely they are. If you have two equally negative outcomes which could be addressed with the same amount of effort, the more likely one is the one to focus on first.

Unfortunately, there really isn’t a solid way to know how likely certain events are in computer systems. These are uncommon events and advances that attackers make lead to huge advances in attack capabilities. However, in general, most people underestimate unlikely events. To be blunt, the state of the field is commonly that one tries to list existing anecdotal examples and once that occurs in a sufficiently public way, everyone seems to agree that this is now something to be concerned about.

Realistically, you get the most value out of understanding roughly how likely things are 1-in-100 vs 1-in-a-million vs 1-in-a-trillion, etc. versus trying to put an exact number.

> [!NOTE]
> **The Thousandfold Misconception**, Commentary by Justin Cappos
> I worked with Evan Gilman, Matt Moyer, and Enrico Schiattarella from the SPIFFE / SPIRE team on a threat assessment and as part of it we tried to quantify risk. We each did this independently for aspects of the system; our answers often varied by more than 10. In fact, in one case it varied by more than a factor of 1000! After discussing these differences, we began to better understand ways in which our mental models differed about how the system could be deployed. This was a really useful exercise for us even though I don’t think any of us put a lot of faith that the values we ended up with are close to the real value.

## Expected Damage

So if one understands the likelihood of things happening, how does that help if the impact of those things differs?  Well, fortunately, there is a simple formula to compute the expected damage from an attack:

```text
Expected damage ~= likelihood * impact
```

For example, if something has a 1-in-100 chance of occurring on a specific day, and costs you $1000 when it occurs, you expect that the amount you’ll have to pay over a long period is about $10 per day.

When addressing risks, you can look at how much your protection would cost (in terms of effort, money, etc.) and how this changes the expected damage.  This would be an ideal way to prioritize how to work on things.  So why don’t we do this?  Because the actual values for likelihood and impact aren’t really known in practice. So understanding “that things that are likely and high impact are really bad and need to be addressed” is going to be more useful in practice than the actual formula will be.

> [!NOTE]
> **The Value of Precedence**, Commentary by Andrew Martin
>
> We have found it helpful to list the remediations and controls from a threat model in precedence order. The recipient of a threat model is likely to be a risk owner such as a CISO or equivalent holder of funds, and the model should inspire them to remediate immediate existential threats, or threats with unacceptable impacts on business functionality, and consider which of the other scoped threats are worth investing in.
>
> Expected damage is a useful metric for risk management at the executive level, and it can be modulated with the secondary data point of likelihood — existential risks should be addressed in some manner, but it’s also acceptable to mitigate them in other ways (such as transferral with disclaimers or insurance policies, or acceptance of low likelihood). Each mitigation is a complex tree of possibly catastrophic permutations and so should be explicitly addressed by the risk owner.

**[> Up Next: Comprehensive Coverage](./comprehensive-coverage.md)**
