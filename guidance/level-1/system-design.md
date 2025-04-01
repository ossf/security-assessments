# System Design

**[< Previous: Project Overview](./project-overview.md)**

This section provides an overview of the system and its distinct parts, helping reviewers understand how different components interact and where security boundaries exist.

## System Actors

[Actors](guidance/background/threat-modeling/actors.md) are the individual components or entities within your system that interact to provide its functionality.

In this situation, Actors are not equivalent to Threat Actors. Instead of looking at the human element (actors using different parts of the system), this is looking at functional elements that are able to act upon each other.

Actors should only be considered distinct if they are isolated in some way. For example, if a service has both a database and a front-end API but a compromise in either would affect the other, then they should be treated as a single actor rather than separate entities.

For each actor, describe:

- **Its role in the system** (e.g., a client application, an authentication service).
- **How it interacts with other components** (e.g., via API calls, message queues).
- **The isolation mechanisms in place** (e.g., separate authentication domains, network segmentation).
  
Capturing all of these mechanisms is crucial, as these can prevent an attacker from moving laterally after a compromise.

[+ Read More About Actors](../background/threat-modeling/actors.md)

## System Actions

Actions describe the processes and interactions that occur between actors in order to deliver functionality.

These are the steps that a project performs in order to provide some service
or functionality.  These steps are performed by different actors in the system.
Note, that an action need not be overly descriptive at the function call level.
It is sufficient to focus on the security checks performed, use of sensitive
data, and interactions between actors to perform an action.

For example, the access server receives the client request, checks the format,
validates that the request corresponds to a file the client is authorized to
access, and then returns a token to the client.  The client then transmits that
token to the file server, which, after confirming its validity, returns the file.

If you have a more complex system, you may want to create a chart using a free tool such as
[draw.io](draw.io) or using GitHub flavored markdown you can make a diagram using a
[mermaid chart](https://github.blog/developer-skills/github/include-diagrams-markdown-files-mermaid/).

[+ Read More About Actions](guidance/background/threat-modeling/actions.md)

## Security Functions and Features

### Critical Security Components

This is a listing critical security components of the project with a brief
description of their importance.  It is recommended these be used for threat modeling.
These are considered critical design elements that make the product itself secure and
are not configurable.  Projects are encouraged to track these as primary impact items
for changes to the project.

Each critical component should be listed with a brief description of its importance.

Examples:

- **Encryption module** – Encrypts stored and transmitted data.
- **Access control service** – Manages authentication and authorization.

### Security-Relevant Features

This is a listing of security relevant components of the project with
brief description.  These are considered important to enhance the overall security of
the project, such as deployment configurations, settings, etc.  These should also be
included in threat modeling.

Each security-relevant component should be documented with a description of its role in security.

Examples:

- **Configurable logging settings** – Helps detect and respond to incidents.
- **TLS enforcement** – Ensures secure communication.

**[> Next Up: Development & Support](./development-and-support.md)**
