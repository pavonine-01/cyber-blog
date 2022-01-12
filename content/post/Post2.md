---
title: "An Introduction to OAuth"
date: 2021-12-12T11:14:57+11:00
draft: false
image: img/Post2.jpg
tags: ['Learning', 'Authentication']
---

Open Authorisation, or OAuth for short, is a way to grant third-party applications access to specific information or permissions from an account with another provider.

It allows people to use the login credentials they have from one service to login to another service. Most commonly, OAuth is used with Google, Facebook or GitHub accounts.

## What Is OAuth?

OAuth itself is an "open standard" authorisation protocol, meaning that is it publicly available for any person or company to implement or update. It is not owned by any particular company, which helps prevent users from becoming "locked-in" to any companies 'ecosystem' of technology.

OAuth 1.0 was initially developed in 2007, but didn't become widely used until it was released as an open standard in 2010.

OAuth 2.0 is a very different version from OAuth 1.0 and 1.1. OAuth 2.0 issues ***access tokens*** to the third-party client with the approval of the user. The third-party will then use that access token to obtain only the approved information it needs to provide its service.

OAuth 2.0 in particular has a specific authorisation process depending on if the user is trying to access a web page, a desktop application, smart device or a mobile phone.

## Benefits of using OAuth

One of the major benefits of using OAuth is that the websites or application that is being accessed is given limited access to the user's data without accessing the user's credentials. The OAuth protocol allows users to specify exactly what information, and what level of permissions, they would like to grant.

An often overlooked advantage of using OAuth is the simplicity it brings to using multiple web-based and software applications. OAuth negates the need for users to create multiple usernames and passwords for many different services, or more likely use the same username and password across these multiple services as many people do, which can be a security risk.

**Add more to this paragraph**
From the perspective of a business, implementing OAuth as an option for users to login with alleviates the need for businesses to invest in securely storing and guarding over login credentials for those users. In the even of a cyber attack on the business, attackers will not be able to steal user's passwords as the OAuth token does not provide this when used to login. [Link](https://www.clowder.com/post/why-your-organization-should-be-using-oauth-2.0)

## Disadvantages of using OAuth

There have been some security vulnerabilities with using OAuth 2.0.

In May of 2017, approximately 1 million Gmail users were targeted with a phishing attack, where the attackers pretented to be either a collegue or employer of the victim and prompted them to click on a link in the email. This link would then redirect the victim to allow a malicious program called "Google Apps" to access their "email, contacts and online documents" through the OAuth protocol.

While this attack wasn't a fault with the protocol itself, the easy setup and access that using OAuth grants allowed attackers to manipulate many users into granting the attackers access to their personal information.

**NEED TO ADD AN ACTUAL SECURITY RISK**.

## How does OAuth acutally work?

*All of this needs to be re-written, it is from this [link](https://auth0.com/intro-to-iam/what-is-oauth-2/)*

1. The Client requests authorization (authorization request) from the Authorization server, supplying the client id and secret to as identification; it also provides the scopes and an endpoint URI (redirect URI) to send the Access Token or the Authorization Code to.
2. The Authorization server authenticates the Client and verifies that the requested scopes are permitted. 
3. The Resource owner interacts with the Authorization server to grant access.
4. The Authorization server redirects back to the Client with either an Authorization Code or Access Token, depending on the grant type, as it will be explained in the next section. A Refresh Token may also be returned.
5. With the Access Token, the Client requests access to the resource from the Resource server.

## Links

[Link](https://en.wikipedia.org/wiki/OAuth)
[Link](https://developer.okta.com/blog/2017/06/21/what-the-heck-is-oauth)
[Link](https://aaronparecki.com/oauth-2-simplified/)
[Link](https://www.scienceabc.com/innovation/oauth-how-does-login-with-facebook-google-work.html)
[Link](https://stackoverflow.com/questions/7561631/oauth-2-0-benefits-and-use-cases-why)

.
