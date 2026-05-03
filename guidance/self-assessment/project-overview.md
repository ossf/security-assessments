# Project Overview

**[< Previous: Metadata Content](./metadata.md)**

This section introduces your project and its purpose, helping reviewers quickly understand its significance and context.

## Background

Provide essential context for reviewers who may not be familiar with your project's domain. Describe the problem your project addresses, the approach it takes to solve it, and the typical users who benefit from it.

## Security Goals

Clearly outline the security guarantees your project aims to provide. These should be specific assurances that define the security scope, such as access control measures, data protection strategies, or authentication mechanisms.

For example: "Flibble only allows parties with an authorization key to change data it stores."

## Security Non-goals

Define what your project explicitly does not aim to achieve. This helps set realistic expectations for users and reviewers while preventing misunderstandings about security responsibilities.

For example: "Flibble does not intend to stop a party with a key from storing an arbitrarily large amount of data, possibly incurring financial cost or overwhelming the servers."

## In-scope Threat Actors

State, in the same place, who you are defending against and who you are not. Frame this in terms of *capability,* not job title — capability is what determines whether a defense works, and it transfers cleanly across deployments.

Useful capability axes include:

- **Position** — outsider on the public network, authenticated user, fellow tenant in a shared deployment, insider with code-commit rights, supply-chain attacker who can compromise an upstream dependency.
- **Resources** — opportunistic attacker with commodity tooling vs. a well-resourced adversary willing to spend significant time and money.
- **Access to side channels** — physical access to the host, ability to observe network timing, ability to read logs.

Then state the explicit non-goals: e.g., *"We do not defend against an attacker who has root on the host running our software,"* or *"We do not defend against a malicious maintainer with merge rights."* Naming the threats you have decided not to address is just as important as naming the ones you have.

**[> Next Up: System Design](./system-design.md)**
