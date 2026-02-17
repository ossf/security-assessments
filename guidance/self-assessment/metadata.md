# Metadata Content

**[< Previous: Header Content](./header.md)**

The first full entry in your self-assessment will be the metadata values—key quick-view information about your project. These metadata fields provide essential context for stakeholders reviewing your security posture and project status.

## Fields

As seen in the template, the following fields are recommended.

### Assessment Stage

Indicate the current status of your self-assessment. This helps stakeholders understand how up-to-date the information is.

- **Incomplete:** The assessment is still in progress.
- **Complete:** The assessment is finalized and reflects the project's current state.
- **Obsolete:** The assessment is outdated and no longer maintained.

### Software Repository

Provide a direct link to the project's repository. This should point to the primary source code repository (e.g., GitHub, GitLab, or another hosting platform).

### Security Provider

Specify whether the project’s primary function is security-related.

- **Yes:** The project is designed to enhance security in an integrating system.
- **No:** The project is not primarily focused on security but may include security-related components.

### Programming Languages

List the programming languages used in the project. This information helps security reviewers assess potential language-specific risks and dependencies.

### Software Bill of Materials (SBOM)

Include a link to the project's SBOM, which details the versions and relationships of components used in the software, including libraries, packages, and dependencies used. This improves supply chain security and helps identify vulnerabilities in third-party components.

This link may be templatized, such as `your/releases/{version}.sbom`.

### Compliance Certifications

List any security standards or compliance frameworks the project adheres to (e.g., PCI-DSS, COBIT, ISO, GDPR). If applicable, provide links to compliance documentation or attestations.

### Security Documentation

Provide links to the project's security-related documentation. At a minimum, include a link to security-insights.yml or any other security policies, threat models, or vulnerability management resources.

As usual, formatting is less important than clear communication with your stakeholders. If this is better broken into a table or sub-sections, feel free to make that decision for your use case.

**[> Next Up: Project Overview](./project-overview.md)**
