---
title: "An Introduction to OAuth"
date: 2022-01-11T21:24:23+11:00
draft: false
image: img/Post2.jpg
tags: ['Learning', 'Authentication']
---

Open Authorisation, or OAuth for short, is a way to grant third-party applications access to specific information or permissions from an account with another provider.

It allows people to use the login credentials they have from one service to login to another service. For example, OAuth is commonly used when logging in with Google or Facebook accounts onto other websites that may be used less frequently, such as Canva or Grammarly.

## What Is OAuth?

OAuth itself is an "open standard" authorisation protocol, meaning that is it publicly available for any individual or company to implement or update. The protocol is not owned by any company, which helps prevent users from becoming trapped within a business's 'ecosystem' of technology, and also allows the technology to become widely adopted by many different service providers.

{{< figure src="/img/Post1Image1.JPG" title="An example of OAuth login options" height="350" width="350" >}}

OAuth 2.0 issues an **access token** to the third-party website with the approval of the user. The third-party will then use that access token to obtain the approved information it needs to provide its service to the user. With an access token, the user is able to continue using OAuth to access the services of the third-party, without the need to repeatedly issue new access tokens.

## Benefits of using OAuth

One of the major benefits of using OAuth is that the websites or application that is being accessed is given limited access to the user's data without accessing the user's credentials. The OAuth protocol allows users to specify exactly what information, and what level of permissions, they would like to grant the third-party. At no point is the third-party given access to the user's password for the service they are logging in with, whether that be gmail, facebook or another provider.

An often overlooked advantage of using OAuth is the simplicity it brings to using multiple web-based and software applications. A good cyber security practice for any person is to keep unique passwords for every website or service they use, a practice which many people do not follow. OAuth simplifies the need for users to create multiple usernames and passwords for many different services, or more likely use the same username and password across these multiple services, which can be a security risk.

From the perspective of a business, implementing OAuth as the only method for users to login with alleviates the need for businesses to invest in securely storing and guarding over login credentials for those users. In the even of a cyber attack on the business, attackers will not be able to steal user's passwords as the OAuth token does not provide this when used to login. However, businesses still need to protect the access tokens they hold to their user's accounts, as attackers can still use the access tokens to access sensitive information.

## Disadvantages of using OAuth

In May of 2017, approximately 1 million Gmail users were targeted with a phishing attack, where the attackers pretented to be either a collegue or employer of the victim and prompted them to click on a link in the email. This link would then redirect the victim to allow a malicious program disguised as a fake site called "Google Apps" to access their "email, contacts and online documents" through the OAuth protocol.

While this attack wasn't a fault with the protocol itself, the easy setup and access that using OAuth provides allowed attackers to manipulate many users into granting the attackers access to their personal information.

Another key issue with OAuth is a result of the flexible design and implemetation of the protocol itself, due to its open-source nature. When using the protocol, user's must trust that it has been properly implemented by their service provider, as there is plenty of opportunity for security vulnerabilites to arise. OAuth 2.0 has very little build-in security features, and combined with the few mandatory components needed for basic functionality of the protocol, the security of the protocol relies on robust installation and care from developers.

## How does OAuth actually work?

OAuth works by first defining three parties that will communicate with eachother. These are:

1. The **Resource Owner**, meaning the user who owns the data,

2. The **Client Application**, meaning the third-party who wants to access the data,

3. and finally the **OAuth Service Provider**, meaning the website or service that controls the data.

There are two main ways that OAuth can be implemented, either through "Implicit" grant types or "Authorisation Code" grant types. The most common way is through the use of Authorisation codes.
The grant type determines the steps that the three parties will take to establish communication, and it also determines how the access token is sent to the **Client Application**.

Since the "Authorisation Code" grant type is the most common, I will be exploring how it works instead of the "Implicit" grant type.

The following diagram appears complicated, but is simpler to understand once examples of the three parties are put in place, with "Jane" as the resource owner, Canva as the client application and Jane's Gmail account as the OAuth service provider. The link to the figure can be found at the PortSwigger website [here](https://portswigger.net/web-security/oauth/grant-types).

{{< figure src="/img/Post1BackupImage.jpg" title="OAuth 2.0 Authorisation Code Grant Type. Figure Source: PortSwigger" height="700" width="700" >}}

1. Jane wants to create an account with Canva using her Gmail account. Canva, being the client application, will send a request to Gmail, the OAuth Service Provider, requesting access to some of Jane's user data. Canva will also specifiy which grant type it would like to use, in this case the "Authorisation Code" grant type.

2. Jane will then be prompted to login to her gmail account, to verify she is the owner of the account and to give her consent for Canva to access her data.

3. Gmail will then send Canva a unique authorisation code.

4. Once Canva receives the code, it will exchange the authorisation code and request for an access token from Gmail's /token API.

5. If the authorisation code that Gmail initially sent matches the code that Canva sent back, then Gmail will issue the access token. If it doesn't match, it is considered a security issue and Gmail will not issue the access token.

6. Canva now needs to retrieve Jane's data from her Gmail account. It will send the access token it has been given to Gmail's /userinfo API in order to access Jane's data, like a personalised key opening a lock.

7. Once Gmail verifies that the access token is valid, it will send Canva the requested resources.

The meaning of Step 6 in the figure above being named "API Call" may be a bit unclear. An API is an "Application Programming Interface". The **OAuth Service Providers** obviously need to support the use of OAuth, and the communication that will take place between all parties. In order to do this, they provide an API's that can interact with potential **Client Applications**.

An API is simply a tool that lets two programs interact with each other. In Step 6, Canva uses the access token to interact with the resource server named /userinfo, in order to retrieve Jane's user data. Using an API allows Gmail to provide a service that is dedicated to fulfilling a certain type of job, such as the /authorisation API seen in Steps 1, 2 and 3, or issuing a token through a /token API, seen in Steps 4 and 5.

## Security Vulnerabilities

Mentioned previously as a disadvantage, the Client Application side of the OAuth communication is often left vulnerable due to the high likelihood of improper implementation of the protocol by developers themselves.

### CSRF Tokens

One example of this is the `state` parameter, which contains a unique and hard-to-guess value that will be sent back and forth between the Client Application and the OAuth Service Provider. This is called a **CSRF** token, and is used to prevent **C**ross-**S**ite **R**equest **F**orgery attacks. These attacks occur in cases when the server is unable to distinguish between requests sent from the victim or the attacker.

If the OAuth protocol is not implemented with this `state` paramater, attackers could potentially initiate an OAuth communication flow between themselves and the Client Application, and then trick the victim's browser into completing it, as the Client Application has no way to verify that the requests for authorisation codes or an access token is coming from the victim themselves, or an attacker.

### The "Implicit" Grant Type

The "Implicit" grant type is even simpler than the "Authorisation Code" grant type, as it does not involve the authorisation code being exchanged for the access token. Instead, when the user give his or her consent, the access token is given straight away. This makes it far less secure, as the access tokens are sent through the browser rather than through a secure back-channel.

If the user gives his or her consent, the authorisation server simply redirects the browser and adds the `token` and `state` information to the redirected URL. In order to store this information for later use, the client application sends this data to the server to store in what is called a `POST` request. The server has no way to verify the integrity of this data, and instead trusts it completely, meaning that the attacker is able to simply alter any of the paramaters in this `POST` request.

### Other Vulnerabilities and Prevention Methods

There are other vulnerabilities with OAuth 2.0 that mainly involve stealing authorisation codes and access tokens, either through a flaw in validating the `redirect_uri` paramater, or even stealing the codes through an open redirect proxy page. While these vulnerabilities are relatively simple to exploit, the prevention methods are also relatively simple to implement.

For example, the vulnerability with CSRF tokens can be prevented by ensuring that the `state` paramater is implemented and no left out of the OAuth 2.0 infrastructure in your business. Keeping a whitelist of verified URI's that can be used in the `redirect_uri` paramater will also help prevent malicious attacks.

Tags:
