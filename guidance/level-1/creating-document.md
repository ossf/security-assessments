# Creating Your Self Assessment Document

Before we dive in to the contents of the assessment, let's consider how and where it will be published. This is not a critical or essential consideration, but it will make things easier if you can lock this in sooner rather than later.

## Scope

Determining what should be covered in your self-assessment may be straightforward, or it may feel daunting at first.

Most projects will only need a single assessment document that is maintained over time as the design changes or new information is gathered. For example, the [Flux project](https://github.com/fluxcd) has multiple repositories that are compiled into a single deliverable, needing only a single assessment.

It is possible that your project will be best served by multiple self-assessments if it contains multiple disconnected parts. We can look at two projects as examples of this: [Argo](https://github.com/argoproj) and [Privateer](https://github.com/privateerproj).

Argoproj is made up of multiple independent but complementary elements: Argo CD, Argo Workflows, Argo Rollouts, Argo Events (and more smaller pieces). Because each of these can be used independently of the others, it is best (and easiest) to assess them one at a time.

On the other hand, Privateer is composed of multiple independent elements that rely on each other to work properly: the core, plugins, and an SDK that enables their development. Privateer and the Privateer SDK are tightly coupled, so we will want to include them both in our assessment. But because plugins each contain their own custom logic that is not always maintained by the Privateer project, and no plugin interacts with another, it is best to assess Privateer and each plugin _one at a time_ — in spite of the fact that the two concepts are part of the same ecosystem.

If any elements interact with each other by design (such as in the second example), there will be space within the assessment to discuss that relationship without going into a detailed assessment of the items it relates to.

Once you’ve determined the scope of your assessment, you’ll be ready to get started documenting it!

## Format

We will be creating our example self-assessment in Markdown because of its compatibility with open source repositories. This easy-to-learn format will be automatically parsed and beautified when loaded to repo hosts such as GitHub.

You may simplify the self-assessment process by starting (and potentially staying) in another format, such as a Drive/Word document. Use whatever format is best for you to craft and distribute your self-assessment to your project’s stakeholders.

## Publishing

Where you publish is up to you to determine, as your project may have different processes for distributing information to stakeholders, such as contributors, maintainers, owners, and users. If your assessment is part of a larger organization, all assessment documentation should be maintained in a centralized location for quick reference by the community, its technical advisors, and its leadership.

**[> Next Up: Header & Metadata](./header-metadata.md)**
