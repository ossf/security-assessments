# Security Assessments

This guidance categorizes the assessments into three levels, which involve increasing levels of complexity. The purpose of an assessment is to create opportunities for the project to turn a critical eye to the system being built, to ensure the software is safe and stable for all future users.

## When should an assessment be done?

In an ideal world everyone would do a security assessment of their project while forming the design in order to ensure that the design will meet the security goals.

Most importantly, if you are designing a security focused system, you need to understand what you are trying to protect against. If you haven’t threat modeled the system ahead of time, your design is very unlikely to match your threat model well. This will lead to insecurity as well as bad user experience in many cases. So, at least some lightweight threat modeling in the design phase is standard practice for organizations that write security-focused code.

In general, the earlier an assessment is done, the more secure the software will be, and the easier it will be to adapt to any design or other changes that are uncovered by the assessment. So, do your best to start early!

> [!INFO]
> A Health Check and Path to Enhanced Security, Commentary by Ash Narkar
>
> The security assessment process really helped the OPA team understand the overall health of the project from a security perspective. The assessment identified areas of the project that could be improved for example better documentation around secure deployment practices, enhancing OPA's toolchain usability to reduce policy authoring related errors. The OPA project benefited from the recommendations and advice provided by the security experts at CNCF's TAG-Security and our on-going relationship with TAG-Security helps us gain insights into the latest security best practices thereby allowing us to continuously improve OPA's security posture.

## Which assessment is right for me?

It is typically advised to do a self assessment prior to a joint assessment, because the latter builds on the former.

1. A **self-assessment** is the least complex form, ideal for use during feature planning, or in preparation for a higher level assessment.
2. A **joint assessment** is more involved than a self-assessment, but is typically achievable for a small team of volunteers who are familiar with the project.

You can read more about the requirements, process, and outputs from each level:

- **[> Get Started: Self Assessment](../../self/quickstart.md)**
- **[> Get Started: Joint Assessment](../../joint/quickstart.md)**
