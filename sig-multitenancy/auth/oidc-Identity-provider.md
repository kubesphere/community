# OIDC Identity Provider

[OpenID Connect](https://openid.net/connect/) is an interoperable authentication protocol based on the OAuth 2.0 family of specifications. It uses straightforward REST/JSON message flows with a design goal of “making simple things simple and complicated things possible”. It’s uniquely easy for developers to integrate, compared to any preceding Identity protocol.

*Example of using [Google Identity Platform](https://developers.google.com/identity/protocols/oauth2/openid-connect)*:

```yaml
apiVersion: v1
data:
 kubesphere.yaml: |
   authentication:
     authenticateRateLimiterMaxTries: 10
     authenticateRateLimiterDuration: 10m0s
     loginHistoryRetentionPeriod: 7d
     maximumClockSkew: 10s
     multipleLogin: true
     jwtSecret: "********"
     oauthOptions:
       accessTokenMaxAge: 1h
       accessTokenInactivityTimeout: 30m
       identityProviders:
       - name: google
         type: OIDCIdentityProvider
         mappingMethod: auto
         provider:
           clientID: '********'
           clientSecret: '********'
           issuer: https://accounts.google.com
           redirectURL:  'http://ks-console/oauth/redirect/google'
kind: ConfigMap
name: kubesphere-config
namespace: kubesphere-system
```

For the above example:

| Parameter | Description |
| ----------| ----------- |
| clientID | The OAuth2 client ID. |
| clientSecret | The OAuth2 client secret. |
| redirectURL | The redirected URL to ks-console. |
| issuer | Defines how Clients dynamically discover information about OpenID Providers. |
| preferredUsernameKey | Configurable key which contains the preferred username claims. |
| emailKey | Configurable key which contains the email claims. |
| getUserInfo | GetUserInfo uses the userinfo endpoint to get additional claims for the token. This is especially useful where upstreams return "thin" id tokens. |
| insecureSkipVerify | Used to turn off TLS certificate verify. |
