# Getting Started: Self Assessment (Level 1)

This guide is derived from the course [Security Self-Assments for Open Source Projects (LFEL 1005)](https://training.linuxfoundation.org/express-learning/security-self-assessments-for-open-source-projects-lfel1005/) distributed by the Linux Foundation Education.

By the end of this guide, you should have a good understanding of what a security self-assessment is and you’ll be prepared to dive in to create one of your own.

## What is a Security Self-Assessment?

There are as many different meanings behind the term security self-assessment as there are behind the word security. Whether you are securing a physical location, an event, software, or anything else, there is value in a self-assessment—but that assessment will be different based on the context.

The benefits will be the same whether we’re securing elections or websites. The process of a self-assessment accomplishes several things:

- Provides the responsible parties with a refined perspective to the security status quo
- Streamlines security improvements by highlighting areas of improvement
- Provides stakeholders with key information regarding security progress
- Accelerates future assessments by clearly documenting answers to common security questions

In this guide, we’re looking to secure an open source project repository. Similar principals will apply to private software repos, though some of the implementations may differ.

> [!WARNING]
>
> While this may help streamline a threat model, it is very different. Check out the [threat model](https://github.com/argoproj/argoproj/blob/main/docs/end_user_threat_model.pdf) created by ControlPlane for Argo CD to learn more.

## Self Assessment Format

This guide will walk you through the process of creating your own security self-assessment documentation.

We will be following the recommendations provided by the Cloud Native Computing Foundation to their myriad of open source software projects. The standard of self-assessment is required by the CNCF for incubating and graduating projects, and it is incentivized by the Cloud Native Security Slam for all CNCF projects to revisit their self-assessment annually.

Anyone familiar with your project can contribute to the creation of the self-assessment, but it is important that the effort contains a high level of engagement from the project’s leadership—a full review and endorsement at minimum—to ensure that nothing is missed and that any findings are incorporated into the project roadmap.

We will be also creating a self-assessment for our own little open source project—a text execution harness that has been on the back burner for too long, and is getting ready for new contributions. Now is a great time to evaluate the progress and gaps related to security!

Hopefully your project has better security considerations already in place… but if not, don’t feel bad! This process is designed to help us better understand our project and triage the necessary work.

Here are the items we’ll be creating:

- Metadata: security links
- Overview: actors, actions, background, goals, and non-goals
- Self-assessment use
- Security functions and features
- Project compliance
- Secure development practices
- Security issue resolution
- Appendix

## Let's Dive In

If you feel like you aren’t ready to begin with your self-assessment, consider why that might be the case. If you feel that your project isn’t ready, or you don’t have all the answers right now, don’t let that stop you from starting! Simply leave notes along the way so that you have a strong first iteration of the self-assessment.

**[> Next Up: Header Content](./header.md)**
