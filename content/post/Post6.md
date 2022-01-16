---
title: "Understanding the log4j global security incident"
date: 2022-01-09T21:24:23+11:00
draft: true
image:
tags: ['Learning', 'Vulnerability']
---

## What is the log4j incident?

Apache log4j is an old open-source logging framework used with the java programming language. It is a popular framework widely used across various industries, from video games such as Minecraft to hospital equipment and other programs. Researchers from Alibaba Cloud Security Team discovered a vulnerability and reported it to Apache on the 24th of November 2021. The vulnerability was released through a Twitter post to the world on the 9th of December 2021.

The vulnerability with log4j, tracked within the National Vulnerability Database as [**CVE-2021-44228**](https://nvd.nist.gov/vuln/detail/CVE-2021-44228), or more colloquially known as **log4shell**, comes with its ability to remotely execute code.

**Attackers can exploit this vulnerability to perform a variety of cyber-attacks, such as force the server that is running log4j to install any software the attacker wants, including software that can completely take over the server.** *need to reword this*.

## Background Information

In Java programming, **logging** is a term to describe keeping records of all data input and output and any changes made in an application. Logging is simply keeping a record of all the events in an application and is mainly used for debugging and tracking the history of changes.

A logging framework is usually a third-party application used to help ease and standardise the process of logging information. Apache log4j is one popular and widely-used example of these third-party applications.

The log4j framework can look up information, such as Event lookups, Date lookups or JNDI (Java Naming and Directory Interface) lookups, to name a few examples. It uses the JDNI API to correlate these lookups against different record providers, such as DNS (Domain Name Service), RMI (Remote Method Invocation) or the others seen in the image below. An overview of JDNI can be found at [this link](https://docs.oracle.com/javase/jndi/tutorial/getStarted/overview/index.html).

{{< figure src="https://docs.oracle.com/javase/jndi/tutorial/figures/jndi/getStarted/jndiarch.jpg" title="JDNI API" height="500" width="500" >}}

The log4shell vulnerability takes advantage of log4j not performing input validation and not sanitising any URL's passed through input messages. Log4j does not verify the JNDI and LDAP (Lightweight Directory Access Protocol) requests. Therefore, attackers can execute malicious Java code on any server, as log4j blindly trusts all input.

## How log4j works



## What known cyberattacks resulted from log4j?

Within 72 hours of the log4j vulnerability being reported, more than 840,000 attacks were reported.

## Links

[Link](https://nypost.com/2021/12/20/why-is-the-log4j-cybersecurity-flaw-the-most-serious-in-decades/)
[Link](https://en.wikipedia.org/wiki/Log4j)
[Link](https://stackify.com/compare-java-logging-frameworks/)
[Link](https://medium.com/avmconsulting-blog/log4j-vulnerability-for-dummies-13af42ce4266)
[Link](https://www.lawfareblog.com/whats-deal-log4shell-security-nightmare)
[Link](https://www.cbsnews.com/news/log4j-vulnerability-breach-patch/)
