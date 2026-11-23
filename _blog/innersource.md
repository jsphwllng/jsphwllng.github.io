---
layout: default
title: not closed source, not open source, but a secret third thing
description: "An overview of how to establish an innersource project"
order: 6
---
Writing internal tools for a company is tough. Individual users and teams may have different requirements and therefore be requesting changes to the tools. This creates a large workload for the team maintaining the tool. If only there was a way that everyone could contribute to a toolset cross-functionally, cross-team and reducing silos?

**Innersource** allows teams to contribute to one central project but also places the onus on them to maintain this feature. The innersource model fosters a strong contribution culture across teams as well as sharing knowledge, struggles and ideas. Rather than listing the benefits of this approach, let's instead look at how we would set up such a project, and then the benefits will reveal themselves!

## Trusted Committers

*"The rewards to the enterprise are great: better integrated code, better code reviews, faster pull request (PR) turnaround time, clearer knowledge for refactoring, more documentation with less pain, and bottleneck reduction."*

<small>-Understanding the InnerSource Checklist</small>

Trusted committers are comprised of individuals who have a greater understanding of the direction of the project, its struggles, and its overall roadmap. They are there to enforce the quality of the code submitted to the codebase. The role of Trusted Committers is not to develop features or resolve bugs on behalf of others. While these tasks may arise during the project's maintenance, requesting a feature or reporting an issue does not automatically make it the responsibility of Trusted Committers. Rather, their primary purpose is to promote teamwork and uphold the high standards of the innersource project, without being directly responsible for its development.

The trusted committers act as both project managers and product managers. Where contributions need to be prioritised, releases overseen, or incidents handled then it is the role of these experts to steer the ship.

When individual contributors have worked within the bounds of the project for long enough, they could be invited to join the trusted committers team. It is not a thankless task, however, where engineers who do not normally take on responsibilities surrounding triage and effort planning might benefit substantially from this.

## Documentation and guidelines

In order for contributors to understand how contribution works there needs to be extensive documentation surrounding contribution guidelines, culture, etc. A fantastic example of this is [Zalando's skipper](https://github.com/zalando/skipper/blob/master/CONTRIBUTING.md) contribution guidelines. It outlines how to contribute bug reports, feature requests as well as code contribution. This should be done on a project by project basis, however, some minimums to include would be testing conventions, documentation conventions, versioning and dependency management, styling conventions, community standards.

Trusted committers create and possess their own contributing agreements. These agreements outline the regulations that contributors must adhere to in order for the TC to approve their code contributions. Contributing agreements are publicly available to all members involved in development, and must include the trust committers' names, contact information, and availability schedule.

## What's in it for me?

The trusted committer role highlights a developer's expertise in mentoring, extensive understanding of architecture, and proficiency in code-review techniques. The domains of Expected Collaboration and Mentorship are closely related to the duties of a Trusted Committer. In addition, the Trusted Committer will interact with teams beyond their usual work sphere, reducing the presence of silos.

A remarkable aspect of InnerSource is that it does not necessarily require a top-down mandate from corporate headquarters to commence - and in fact, it's probably better if it doesn't. Even a single team in a department can initiate a few minor adjustments in the appropriate areas to observe outcomes. This may inspire other teams to follow suit.

InnerSource is facilitated by both tools and procedures, but it also necessitates a cultural shift. The most significant transformation is embracing the idea of making mistakes, discussing them, and learning from them.

## Where to start?

Below are a list of wonderful resources that I used when writing my own innersource agreements and documentation:

* [Understanding the InnerSource Checklist](https://innersourcecommons.org/documents/books/InnerSourceChecklist.pdf)
* [An introduction to innersource](https://resources.github.com/innersource/fundamentals/)
* [Zalando's skipper Contribution Guidelines](https://github.com/zalando/skipper/blob/master/CONTRIBUTING.md)
* [What is innersource?](https://about.gitlab.com/topics/version-control/what-is-innersource/)
