---
title: "An Introduction to OAuth"
date: 2021-12-12T11:14:57+11:00
draft: true
image: img/Post2.jpg
tags: ['Learning', 'Authentication']
---

Open Authorisation, or OAuth for short, is a way to grant third-party applications access to specific information or permissions from an account with another provider.

It allows people to use the login credentials they have from one service to login to another service. For example, OAuth is commonly used when logging in with Google or Facebook accounts onto other websites that may be used less frequently, such as Canva or Grammarly.

## What Is OAuth?

OAuth itself is an "open standard" authorisation protocol, meaning that is it publicly available for any individual or company to implement or update. The protocol is not owned by any company, which helps prevent users from becoming trapped within a business's 'ecosystem' of technology.

OAuth 2.0 is a very different version from OAuth 1.0 and 1.1. OAuth 2.0 issues ***access tokens*** to the third-party website with the approval of the user. The third-party will then use that access token to obtain the approved information it needs to provide its service to the user.

OAuth 2.0 in particular has a specific authorisation process depending on the device or application the user is attempting to access, such as a web page, a desktop application, smart device or a mobile phone.

## Benefits of using OAuth

One of the major benefits of using OAuth is that the websites or application that is being accessed is given limited access to the user's data without accessing the user's credentials. The OAuth protocol allows users to specify exactly what information, and what level of permissions, they would like to grant the third-party. At no point is the third-party given access to the user's password for the service they are logging in with, wether that be gmail or facebook.

An often overlooked advantage of using OAuth is the simplicity it brings to using multiple web-based and software applications. A good cyber security practice for any person is to keep unique passwords for every website or service they use, a practice which many people do not follow. OAuth simplifies the need for users to create multiple usernames and passwords for many different services, or more likely use the same username and password across these multiple services, which can be a security risk.

**Add more to this paragraph**
From the perspective of a business, implementing OAuth as the only method for users to login with alleviates the need for businesses to invest in securely storing and guarding over login credentials for those users. In the even of a cyber attack on the business, attackers will not be able to steal user's passwords as the OAuth token does not provide this when used to login. [Link](https://www.clowder.com/post/why-your-organization-should-be-using-oauth-2.0)

## Disadvantages of using OAuth

In May of 2017, approximately 1 million Gmail users were targeted with a phishing attack, where the attackers pretented to be either a collegue or employer of the victim and prompted them to click on a link in the email. This link would then redirect the victim to allow a malicious program disguised as a fake site called "Google Apps" to access their "email, contacts and online documents" through the OAuth protocol.

While this attack wasn't a fault with the protocol itself, the easy setup and access that using OAuth grants allowed attackers to manipulate many users into granting the attackers access to their personal information.

Another key issue with OAuth is a result of the flexible design and implemetation of the protocol itself, due to its open-source nature. When using the protocol, user's must trust that it has been properly implemented by their service provider, as there is plenty of opportunity for security vulnerabilites to arise. OAuth 2.0 has few build-in security features, and combined with the few mandatory components needed for basic functionality of the protocol, the security of the protocol relies on robust installation and care from developers.

## How does OAuth acutally work?

OAuth works by defining three parties that will communicate with eachother. These are the **Resource Owner**, meaning the user who owns the data, the **Client Application**, meaning the third-party who wants to access the data, and finally the **OAuth Service Provider**, meaning the website or service that controls the data, such as Gmail.

As mentioned previously, there are many ways that OAuth can be implemented, but the most common way is through the use of *authorisation codes* and *grant types*.

1. The user wants to access a third-party website and, if the third-party supports OAuth, will have give the user the option to log in with a choice of service providers.

2. 


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

Tags:
