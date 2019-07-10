---
layout: post
title: "An introduction to OAuth 2.0"
categories: security
---

OAuth 2.0 is an open standard for authorization, published as [RFC 6749](https://tools.ietf.org/html/rfc6749) and [RFC 6750](https://tools.ietf.org/html/rfc6750) in October 2012.

OAuth 2.0 enables a third-party application (**client**) to obtain limited access (via an **access token**) to an HTTP service (**resource**), either on behalf of an end-user (**resource owner**) or by allowing the application to obtain access on its own behalf. This specification replaces and obsoletes the OAuth 1.0 protocol.

# Roles

OAuth defines four *roles*:
- **resource owner** (eg. the end-user)
- **resource server** (the server hosting the protected resources, capable of accepting and responding to protected resource requests using access tokens)
- **client** (the application making protected resource requests on behalf of the resource owner)
- **authorization server** (the server issuing access tokens to the client after successfully authenticating the resource owner and obtaining authorization)

# Obtaining Authorization

To request an **access token**, the **client** obtains authorization from the **resource owner**. The authorization is expressed in the form of an **authorization grant**, which the **client** uses to request the **access token**.

OAuth defines four *grant types* (plus and extension mechanism for defining additional grant types):
- **authorization code**
- **resource owner password credentials**
- **client credentials**
- **implicit**

The **authorization code grant** is the most used type, for apps running on a web server, browser-based and mobile apps. For other use cases, see [here](https://auth0.com/docs/api-auth/which-oauth-flow-to-use) a decision tree about which flow to use.

The **authorization code grant** type is used to obtain both **access tokens** and **refresh tokens** and is optimized for confidential clients. Since this is a redirection-based flow, the client must be capable of interacting with the **resource owner**'s **user-agent** (typically a web browser) and capable of receiving incoming requests (via redirection) from the **authorization server**.

![Authorization Code Grant Flow](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=dGl0bGUgQXV0aG9yaXphdGlvbiBDb2RlIEdyYW50IEZsb3cKCnBhcnRpY2lwYW50ICJSZXNvdXJjZSBPd25lciIgYXMgUk8AFQ5DbGllbnQAFgVDAC8OAFsOU2VydgA8B0FTAE8XABkLUlMKCkMtPitBUzoAgR4UUmVxdWVzdApSTy0-QVM6IExvZ2luICYgQ29uc2VudApBUy0tPj4tQwAmF3Nwb25zZQBYCUV4Y2hhbmdlAIIIBmZvciBBY2Nlc3MgVG9rZW4AQQwADAsgWysgUmVmcmVzaAAiBl0KbG9vcACBMQVSUzogAIIzCQCBJQcgd2l0aABLDlIAgR0JACILAIEWBgAoBkRhdGEKZW5kCg&s=modern-blue)

# OpenID Connect

OAuth 2.0 describes patterns for granting authorization but does not define how to actually perform authentication. One interesting and useful extension of OAuth 2.0 is the **OpenID Connect** protocol.

[OpenID Connect](http://openid.net/connect/) 1.0 is a simple identity layer on top of the OAuth 2.0 protocol. It allows **clients** to verify the identity of the **end-user** based on the authentication performed by an **authorization server**, as well as to obtain basic profile information about the **end-user** in an interoperable and REST-like manner.

# Reference

- [OAuth 2.0 \| oauth.net](https://oauth.net/2/)
- [RFC 6749 - The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)
- [RFC 6750 - The OAuth 2.0 Authorization Framework: Bearer Token Usage](https://tools.ietf.org/html/rfc6750)
- [OAuth 2.0 Simplified \| Aaron Parecki](https://aaronparecki.com/oauth-2-simplified/)
- [OAuth 2.0 Authorization Framework \| Auth0 Docs](https://auth0.com/docs/protocols/oauth2)
