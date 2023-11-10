---
layout: default
title: "scoutCDK: how we solved best practice adoption"
description: "Defining best practices is only half the story"
order: 5
---


The Problem
-----------

Defining best practices is only half the story. When best practices relating to infrastructure decisions are ignored it can not only be expensive but also lead to vulnerabilities in our codebase. Furthermore, once best practices are defined they can be easily ignored, forgotten, or misunderstood especially when using multiple tools, codebases and platforms it can be hard to align. Scout24’s codebase has over 3000 Cloudformation YAML files which represents a lot of duplicated code, a lot of difficult to wrangle yaml, and even more difficult code to troubleshoot when things go wrong.

Infrastructure design itself is prone to many errors both human and organisational. Large, complex YAML files lead to typing errors, code can be written per individual use case which is therefore non-replicable, duplication, and a lack of version control. The goal of Scout24’s Application Platform team is to enable product developers to not have to worry about granular infrastructure details, like tagging or naming patterns, but instead focus on building applications and services that solve business needs.

The Idea
--------

In order to demonstrate the decision-making process and how ideas were iterated upon we can have a look at an example of one of our level 2 constructs and its design process.

While AWS’ CDK is becoming an industry standard and offers a more palatable way of creating cloudformation templates, it does not fully solve the problems we were facing in the Application Platform. By leveraging the AWS CDK and building upon it we are able to inject Scout24’s best practices into CDK constructs (code representing AWS resources) without the user even being aware of it. By offering this layer of abstraction we are able to not only comply with best practices relating to costs, service naming, etc. but also we are able to update our own library when the best practices change so users will also, seamlessly and effortlessly, benefit from these changes.

When designing the ScoutCDK one of the challenges that we faced was deciding how far we should abstract. When new engineers join Scout24 we don’t want them to be bogged down in reading best practices for infrastructure. Instead, they should be concerned with which application they are deploying and what they need to get it to run. Should users have to care about the number of clusters that a Redis cache should have? Should they even be able to define something like this?

In order to demonstrate this, we can look at AWS’ ElastiCache, which is their implementation of Redis.

The Implementation
------------------

When we were designing our extension of AWS CDK’s elasticache.CfnReplicationGroup Redis construct we had to decide what users should have to decide on and what we, as the Application Platform, should abstract.

### What must the users decide?

Ultimately, we decided upon the engine version of Redis and the EC2 Instance Type that it was built on could not be abstracted. When there is an update to a CDK deployment stack, such as changing the Redis engine version, it can lead to the entire deployment being rebuilt in AWS resulting in potential downtime. Therefore, if the “standard” that the Application Platform decides upon for Redis Engine changes then there would be potential downtime across all services that use the CfnReplicationGroup construct. The EC2 Instance Type and Redis Engine has to be decided individually by the teams who will use it and they would be responsible for handling upgrades.

### What can the users decide?

Deciding what the users can have a say in depends on the individual construct that you are designing. For example, when designing an application that reads/writes to multiple caches then it would be ineffective to have the port number of the cache be uneditable by the engineer. While these minute decisions are obviously down to the individual application, for wider infrastructure decisions how do we allow users to have an input?

A good example of this is deciding the number of cache clusters that a Redis replication group will have. The complexity here is understanding or knowing what a replication group is, what cache clusters are and what a ‘high availability’ of cache clusters would look like. In order to allow this customisation, we decided to abstract the numCacheCluster property away to a variable called highAvailability. This highAvailability will be enabled by default, providing users with multiple cache clusters. If a user were to decide they do not want this highAvailability then it would be set to a singular cluster. This represents the benefits of abstracting an infrastructure decision like this - users can decide what they want without needing to worry about how that is defined.

### What can’t the users decide?

What the users cannot modify is essentially where the enforcement of best practices comes into play. In the example of ElastiCache, when looking at our internal best practices, we decided configurations such as encryption, version upgrading, failovers, and security groups were all issues that should be “locked away” from the users. These are decisions handled by best practice definition. When defining a new ElastiCache cluster, users should ultimately be unopinionated or unaware of these design decisions. Therefore in our implementation, these values are hardcoded and unmodifiable to users.

Looking forward
---------------

The difference in readability from cloudformation, AWS’ CDK, and the ScoutCDK is also remarkable:

### AWS CDK:

<script src="https://gist.github.com/jsphwllng/b384e51fe0447fa3bf52c7ce4b1bb024.js"></script>

### ScoutCDK

<script src="https://gist.github.com/jsphwllng/b474557a8e80ba6a0d549330b1b96686.js"></script>


### Cloudformation

<script src="https://gist.github.com/jsphwllng/27bcbf973fd0d81aa9d7451d2300e4aa.js"></script>


While the product is now in place and thoroughly tested on our end we now require feedback from users. Within Scout24 there is obvious excitement for the ScoutCDK with several teams eager to get involved and now we must iterate through a cycle of collecting feedback, implementing changes, and understanding builder’s needs. If this is something that you are interested in either using or building you can check out Scout24’s career page [https://www.scout24.com/en/career](https://www.scout24.com/en/career).
