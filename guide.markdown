## Intro [TL;DR]
Here is a cloudformation template providing everything you need before you start building instances in AWS and a guide to explain each part while hopefully enlightening you towards the benefits of cloudformation. As a piece of infrastructure it's opinionated and arguably overkill, but it's also as close to free as possible ($1.50/month beyond AWS free tier). The opinions will be explored in depth throughout but the overkill has a concise purpose.

### Purpose
There are plenty of cloudformation guides to help build a 3-tier web app infrastructure but, I've always felt this use case neglects much of cloudformation's power and much of AWS's features and security options. This template will configure a network layer following the [principles of least privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege) and take advantage of some less discussed, but powerful, services on offer from AWS; services which are otherwise very laborious to configure.

EC2/RDS instances are a well known quantity and you've probably already got a process for configuring these, a habit which little will convince you to change. Hopefully this guide will explain some of the real world use cases of AWS services you'd not thought of and make it first nature for you to reach for cloudformation for anything.

### Overkill, undercost
The template will create a lot of resources, just no actual useable instances. The end result will give you an endpoint to create a VPN tunnel into your new network, but little else you can actually use yet. Its aim is to give you a base from which to build and to support almost anything you'd want to build o top of it; Linux EC2, Windows EC2, RDS, ElastiCache, DNS, etc.

It also costs as close to nothing as possible. The only cost above free tier is for some domain name hosting, so you should be able to follow this guide for pennies and since it's a cloudformation template, you can spin it up and turn it off to avoid paying for a whole month.

### Guide infra
It starts with a quick overview of the cloudformation template document structure and how to deploy and remove the services described. Then, it'll go through blocks of the template one by one and describe the decisions made, what you might make differently and what you might need to expand on as you grow your infrastructure on top. It's around 1500 lines of JSON, so the guide is here to make it digestible, hopefully it does...


## .cform structure