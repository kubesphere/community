# 项目

KubeSphere SAML 2.0 认证集成

## 项目目标

集成 [SAML 2.0](https://www.oasis-open.org/committees/download.php/56776/sstc-saml-core-errata-2.0-wd-07.pdf) 认证方式。

## 技术要求

* Golang
* REST API
* OpenAPI
* SAML

## 项目背景

安全断言标记语言 2.0 (SAML 2.0)， 用来在安全域中交换身份验证（Authentication）数据和授权（Authorization）数据。SAML 2.0基于XML协议，使用包含断言（Assertions）的安全令牌在SAML授权方（即身份提供者，Identity_provider，缩写为IdP）和SAML消费方（即服务提供者，Service Provider，缩写为SP）之间传递委托人（通常是一个终端用户）的信息。SAML 2.0 可以实现基于网络跨域的单点登录(SSO)。

KubeSphere 支持诸多第三方认证登录协议, 用于 KubeSphere 登录认证请求，目前已经支持如：Oauth2, CAS, OIDC, LDAP 等协议。通过集成 SAML 2.0 认证协议，KubeSphere 进一步的提升了用户账户系统集成能力，支持更多的第三方用户认证系统。

## 项目详情

单点登录(SSO)是 SAML 的主要应用场景。当用户访问受 SAML Service Provider(即 KubeSphere Console) 保护的资源时，Service Provider 会要求用户发送身份认证请求至 SAML Identity Provider。认证流程如下图所示:

![](https://upload.wikimedia.org/wikipedia/en/0/04/Saml2-browser-sso-redirect-post.png)

在 KubeSphere 中，需要实现以下功能：
* SAML 断言解析
* SAML 断言签名验证
* SAML 用户信息获取
* JWT token 交换(用户KubeSphere Resources API 验证)

## 项目产出

实现一个基于 saml 协议的 [identityprovider](https://github.com/kubesphere/kubesphere/tree/master/pkg/apiserver/authentication/identityprovider) 接口实例, 用于接入 Idp 服务。

## 链接

* https://www.oasis-open.org/committees/download.php/56776/sstc-saml-core-errata-2.0-wd-07.pdf
* https://developer.okta.com/docs/concepts/saml/#understanding-the-role-of-a-service-provider
* https://github.com/kubesphere/kubesphere/tree/master/pkg/apiserver/authentication/identityprovider
* https://github.com/dexidp/dex/blob/master/connector/saml/saml.go

## 快速入门

安装一个[最小化的 KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/)。

配置 [Oauth2 认证]( https://kubesphere.com.cn/docs/access-control-and-account-management/configuring-authentication/)

配置一个 Idp 服务，如: [Okta](https://help.okta.com/en/prod/Content/Topics/Apps/Apps_App_Integration_Wizard_SAML.htm)。

## 入门 Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)

## 导师/联系方式

* [Hongming](https://github.com/wansir/)
* [Roland](https://github.com/rolandma1986/)

