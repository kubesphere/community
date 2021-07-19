# GitHub Identity Provider

KubeSphere provides you with an example of configuring GitHubIdentityProvider for OAuth2 authentication.

You need to create a [GitHub OAuth application](https://docs.github.com/en/developers/apps/authorizing-oauth-apps) first.

*Example Configuration*:

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
       - name: github
         type: GitHubIdentityProvider
         mappingMethod: auto
         provider:
           clientID: '************'
           clientSecret: '************'
           redirectURL: 'https://ks-console/oauth/redirect'
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