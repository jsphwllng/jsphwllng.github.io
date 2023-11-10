---
layout: default
title: kubecon eu 2022
description: "I just returned from my first tech conference: Kubecon CloudNativeCon Europe 2022."
order: 4
---
I just returned from my first tech conference: [Kubecon CloudNativeCon Europe 2022](https://events.linuxfoundation.org/kubecon-cloudnativecon-europe/). There's a whole other blog post to be written about developer etiquette, food, hygiene, covid, the state of the bathrooms and the fact that every talk seemed to be unequipped to deal with the number of attendees but I will instead focus on the talks that I saw while I was there. I only arrived on the second day which I will count as day 0 and the main conference days will be labelled as days 1-3.

Overall Impressions
-------------------

As interesting as every talk may have been and as technically impressive as some of the booths were my main takeaway from this conference was simply the scale of the k8s community. When I started out doing work with k8s I was aware that it was a very complicated tool that was developed by google before being made open source. This conference really enlightened me to the fact that almost every aspect of devops (except docker...) was open source and maintained, largely for free, by an army of developers. The CNCF and Linux Foundation seem to be pioneering the open source vision. I came away from the conference inspired to learn more, develop more and think about ways I could contribute to the community.

Day 0
-----

After the team from Helm failed to arrive at the first talk of the day we moved on to listen to The New Stack Tapas Tuesday which was a panel/group therapy focused around k8s upgrades. In my current company we are a couple of versions behind and have been scrambling to keep up to date. It was very encouraging to hear that not only was this a common problem but also that some companies were two years of versions behind. A lot of discussion was focused around automating these upgrades, focusing on levels of complexity (thousands of clusters!) and generally discussing the lifecycle of a cluster. Secondly I moved onto the lightning talks which were a mix of insightful, daring and hilarious. Some great talks focused on shifting the blame of incidents away from engineers and into systems that allowed incidents to occur, visualising layers of containers and using products such as Linkerd and Telepresence to debug. Some of the more bizarre talks came from a junior engineer telling a room full of seasoned k8s engineers how to get started with devops and an Islamabad CNCF chapter host explaining his CV.

Day 1
-----

They keynotes of day 1 were okay. My personal highlight came from Mercedes Benz discussing their evolution from servers to cloud computing. Lowlights came from Huawei who managed to make the topic of k8s in space into a tedious series of talking through graphs. The first interesting talk of the day was Kubernetes is Your Platform: Design Patterns For Extensible Controllers. The main interest here is my company had been strictly following one design pattern and I was almost unaware that other patterns existed. A funny but informative talk came from Effective Disaster Recovery: The Day We Deleted Production which built on the talks of the previous day's blaming a system rather than blaming an engineer. An interesting takeaway from this talk in particular was the idea of having a 'big red button' to halt all deployments and rollouts in the case of a failure - something that my company could perhaps benefit from. A talk that I also found useful was Autoscaling Kubernetes Deployments: A (Mostly) Practical Guide which, although basic, gave a lot of insight into when to use horizontal against vertical scaling, how to effectively drain and scale and using external metrics to trigger these scales.

Day 2
-----

An overall better round of keynotes were outshone by a CERN engineer showing k8s powering the large hadron collider and the mammoth of data that is passed through it, how it is handled, visualised and scaled. Really inspiring stuff. The major talk of the day came from Spotify and their recently donated project Backstage: Restoring Order To Your Chaos which was effectively a showcase, an advert and a call to action for Backstage which immediately won the attention of my team. While we had been playing around with the idea with using backstage I think that we were either naive or underestimating Backstage's potential impact. My current company is divided up into multiple teams working on multiple applications each of which has their own instances of pipelines, aws account, datadog dashboards, etc. and having all of these harmoniously pointed to one location sounded like a dream. We will definitely be investing more time into developing this and, hopefully, contributing back to the source code.

Day 3
-----

The final day's keynotes were a victory lap from the CNCF team discussing the growth of the foundation and the new appointments. Understandably as many devops products all seem to be heavily influenced or managed by the CNCF team. My team, as exhausted as we were, made it to a talk about multi-cloud solutions called Kubernetes Everywhere: Lessons Learned From Going Multi-Cloud which again expanded my understanding of reliability, availability zones and what it means to be "on the cloud". This is something that my team will also take into consideration with our own offerings. Sadly, as the heat weighed down on us and the [number of corona cases](https://twitter.com/tiffanyfayj/status/1529104399016026114) began to increase, my flight approached and I had to depart early.

Booths, products
----------------

Here I will do a quick outline of the products I got to see, what they do, and how cool they were.

*   CockroachDB a decentralised, multi-zone, horizontally scaling database. Although we cannot think of much of a usecase in our environment it was still a very interesting and cool offering
*   Keptn a k8s cluster deployment automater (canary, blue/green) based on metrics. Again, very interesting but does not align with our current needs
*   Slim.ai using ai to reduce docker image sizes. I particularly enjoyed discussing this product as it is one of those ideas you hear and think "well yeah, of course this should be how it is done".
*   Karpenter a cluster autoscaler alternative with a focus on flexibility and scale based on instance types, zones and cost. Very, very cool.
*   ArgoCD I know we may be slightly late to the game in implementing ArgoCD; a central continuous deployment platform to streamline kubernetes cluster deployments however we are very excited to work on it
*   Spectrocloud a visualisation tools for clusters with a nice GUI to enable infrastructure management. Although not offering anything revolutionary new this is a very "nice to have" tool.
*   Flux - An alternative to ArgoCD that does, largely, the same thing
*   MicroK8s a mini-kube alternative developed by Ubuntu (❤️) that spins its own single-node cluster with a set of addons. Sadly, as this is a linux offering, it only runs on linux machines where _snap_ is installed. I will personally be playing around with this as I am a ubuntu fanboy
