# Threat Modeling: Actions

**[< Previous: Actors](./actors.md)**

In addition to understanding the actors, it is important to know what actions they perform. This should include the actions that are desirable (at a high level) and how they are carried out, including any checks and balances.

For example, in TrashPanda Bank, customers may have a list of actions they perform such as opening an account, withdrawing money, checking a balance, renting a safety deposit box, visiting their safety deposit box, and making a deposit. For each of these actions, there needs to be a detailed description of how the process works and how the various steps are verified by different parties.

An example action may look something like the following.

```text
Renting a safety deposit box:

Requires a customer with a current account to make an in-person request at TrashPanda Bank to a teller.

The teller processing the request first verifies the customer’s account exists, is linked to the customer (by checking their identification) and has a balance of at least $100.

The teller then gives the terms and conditions form to the customer, who signs the request. After this is confirmed by the teller, the customer pays the deposit fee to the teller. The teller logs this transaction into their log book and inserts the payment as per the steps in “making a deposit”, except that the remittance goes to TrashPanda’s safety deposit box fund (listed in the teller’s handbook) instead of the user’s account

The manager is then called by the teller, who re-checks the client’s identification and verifies the remittance to TrashPanda’s safety deposit box was processed by checking the logbook of the teller. The manager now accesses the safety deposit usage map to find an unused safety deposit box, considering customer requests for a specific lucky number or an accessible box. The manager then provides the customer a copy of the key for the box. The teller and the manager use their keys to provide the customer access to the vault, where the safety deposit boxes are kept. The manager and teller leave the vault to provide the customer privacy. Once the customer is finished, they exit the vault and the manager locks the vault again.
```

Note that increased complexity of actions does tend to correlate with insecurity, at least if you ignore the complexity added by security steps. A system which does a few simple things is easier to secure in most cases.

Please don’t mistake this for saying that fewer API calls or system calls means better security. If that were true, we could just have one API call that takes an argument telling it what action to actually perform! This would be a case where the complexity of the API isn’t well reflected by the number of API calls.

**[> Next Up: Goals](./goals)**
