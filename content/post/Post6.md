---
title: "Understanding the log4j global security incident"
date: 2022-01-09T21:24:23+11:00
draft: true
image:
tags: ['Learning', 'Vulnerability']
---

## What is the log4j incident?

Apache log4j is an old logging framework used with the java programming language. A vulnerability was discovered on the 24th of November 2021, and released through a twitter post to the world on the 9th of December 2021. A function of log4j's formatting is the ability to trigger/execute code.
When the vulnerability message is logged by an attacker, Java will fetch the object that is referred to from the remove server, deserialise it and run the code.

## Background Information

Logging is keeping records of data input, output, changes and results of a program.
It is basically a reord of all events that occur in an operating system or software.

A loggin framework is usually a third-party application that is used to help ease and standardise the process of logging information.

## Links

[Link](https://nypost.com/2021/12/20/why-is-the-log4j-cybersecurity-flaw-the-most-serious-in-decades/)
[Link](https://en.wikipedia.org/wiki/Log4j)
[Link](https://stackify.com/compare-java-logging-frameworks/)
[Link](https://en.wikipedia.org/wiki/Zero-day_(computing))
[Link](https://www.lawfareblog.com/whats-deal-log4shell-security-nightmare)
[Link](https://www.cbsnews.com/news/log4j-vulnerability-breach-patch/)
