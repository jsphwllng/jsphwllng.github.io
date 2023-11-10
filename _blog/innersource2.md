---
layout: default
title:  "INNERSOURCE: AN ANARCHIST APPROACH TO PROJECT MANAGEMENT"
description: 	"maintaining your innersource project so that everyone can get involved"

order: 13
---
So, you have an innersource project and someone has built a feature. What now? Who owns it? Did this 10x developer just increase my workload?

## QUALITY CONTROL
Previously we discussed agreements surrounding quality control which should be outlined in documentation as detailed as possible. The purpose of this is to reduce the workload, no only for you, the trusted committer, but also the future maintainer of the project. New functionality should, broadly, be accompanied with tests, documentation, and example usage. This means that future maintainers, bug fixes, usage will all be more easily handled by the community you are fostering.

This type of quality control can be easily facilitated by including a CONTRIBUTION.md checklist in github:

```md
# Description

Please provide a concise overview of the modification, indicating the resolved issue and offering relevant context and motivation. Include any necessary dependencies for this alteration.
Type of modification

Please remove any options that are not applicable.

[] Bug fix (a non-breaking modification that addresses an issue)
[] New feature (a non-breaking modification that introduces new functionality)
[] Breaking change (a modification, either a fix or a feature, that would cause existing functionality to behave unexpectedly)
  This modification requires an update to the documentation

# Testing Procedure

Kindly describe the tests conducted to verify the changes made. Provide clear instructions for reproducing the tests, and include any pertinent details about the test configuration.
Checklist:

[] My code adheres to the project's style guidelines.
[] I have conducted a self-review of my code.
[] I have added comments to my code, especially in complex sections.
[] I have made the necessary modifications to the documentation.
[] I have made appropriate changes to the CODEOWNERS file.
[] My changes do not generate any new warnings.
[] I have included tests that demonstrate the effectiveness of my fix or the functionality of my new feature.
[] Both new and existing unit tests pass locally with my modifications.
```

## THE SHARED RESPONSIBILITY MODEL
If a developer, or a team of developers, has built a new functionality to your innersource project they are now the owner of this feature. That means that, for this particular codebase, they join the trusted committers in making sure that the feature is functioning and usable. The benefit here is that who would be a better expert in a particular feature than the team who built it? The likelihood is that they will be the first adopters of the feature, resulting in "real world" bug testing also coming from their side.

While the documentation should be sufficient enough that any of the trusted committers would be able to field questions from other developers, it should be noted that the true expertise lies with the team who built the function and they should be willing to help out whenever possible.

If a developer, or team of developers, is regularly contributing to the project it might be worth offering the (maybe) coveted position of a trusted committer as they will be familiar with the process and development cycle.

## PROJECT DIRECTION
Unless a project is in maintenance mode there should be some plans for the future. The beauty of innersource is it pries away this responsibility from a few project managers and places it back into the hands of developers. As innersource benefits internal tooling then it will be the users, the developers, who will decide its future. There are a couple of different approaches to follow here.

Firstly there could be no direction, pure anarchy. Features will only get developed as they are needed by the teams who need them. This approach ensures a lack of feature creep and actually creates an incredibly streamlined product.

Secondly we can consider a more traditional approach to the product management. Goals for the project can be discussed between trusted committers and shared publicly in the project repository. Goals can be established and built by either the trusted committers or by anyone who wants to get involved with the project. This approach may seem slightly less intuitive but, for companies just adopting the innersource model, can provide a nice transition.

Transparency is crucial throughout the planning process as it contributes to conflict reduction. When discussions are public and intended for archiving, participants tend to consider the entire company's needs more effectively, leading to better prioritization. Additionally, this approach helps break down the silo mentality.

The level of transparency in planning has increased as a result of involving more individuals in the planning meetings. With more people present for trade-offs and negotiations, a broader perspective is gained. Equally important is the implementation of a minor procedural change: ensuring that all relevant conversations are documented passively. This allows for future review of discussions and prompts individuals to adjust their conversational strategies. Furthermore, the creation of passive documentation helps prevent information overload by enabling efficient searches and reducing unnecessary communication.
