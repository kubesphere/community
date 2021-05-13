# Project

KubeSphere SAML 2.0 Authentication Integration

## Project Goal

Integrate [SAML 2.0](https://www.oasis-open.org/committees/download.php/56776/sstc-saml-core-errata-2.0-wd-07.pdf) authentication。

## Skills to Learn/Improve

* Golang
* REST API
* OpenAPI
* SAML


## Background

Security Assertion Markup Language 2.0 (SAML 2.0) is a version of the SAML standard for exchanging authentication and authorization identities between security domains. SAML 2.0 is an XML-based protocol that uses security tokens containing assertions to pass information about a principal (usually an end-user) between a SAML authority, named an Identity Provider, and a SAML consumer named a Service Provider. SAML 2.0 enables web-based, cross-domain single sign-on (SSO), which helps reduce the administrative overhead of distributing multiple authentication tokens to the user.

KubeSphere supports third-party authorization protocols, such as Oauth2, CAS, OIDC, LDAP. By integrating with SAML 2.0, KubeSphere further enhances user account system integration and supports more third-party user authentication systems.

## Project details

Single Sign-On (SSO) is the primary application scenario for SAML. When a user accesses a resource protected by the SAML Service Provider (i.e., KubeSphere Console), the Service Provider requires the user to send an authentication request to the SAML Identity Provider, as shown in the following diagram:

![](https://upload.wikimedia.org/wikipedia/en/0/04/Saml2-browser-sso-redirect-post.png)

In KubeSphere, the following functions need to be implemented:
* SAML assertion parsing
* SAML assertion signature verification
* SAML user information acquisition
* JWT token exchange (user KubeSphere Resources API validation)

## Outcomes

Implement an instance of [identityprovider](https://github.com/kubesphere/kubesphere/tree/master/pkg/apiserver/authentication/identityprovider) base on SAML protocol, which will be used to integrate with Idp.

## Links

* https://www.oasis-open.org/committees/download.php/56776/sstc-saml-core-errata-2.0-wd-07.pdf
* https://developer.okta.com/docs/concepts/saml/#understanding-the-role-of-a-service-provider
* https://github.com/kubesphere/kubesphere/tree/master/pkg/apiserver/authentication/identityprovider
* https://github.com/dexidp/dex/blob/master/connector/saml/saml.go

## Quickstart

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). 

Configuring [Oauth2 Authentication]( https://kubesphere.com.cn/docs/access-control-and-account-management/configuring-authentication/) for KubeSphere to learn 3rd-party authentication works.

Configuring a SAML Identity Provider, for example, [Okta](https://help.okta.com/en/prod/Content/Topics/Apps/Apps_App_Integration_Wizard_SAML.htm)

## Newbie-Friendly Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)

## Potential Mentors

* [Hongming](https://github.com/wansir/)
* [Roland](https://github.com/rolandma1986/)
