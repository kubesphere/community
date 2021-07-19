# LDAP Identity Provider

Set LDAPIdentityProvider in the identityProviders section to validate username and password against an LDAPv3 server using simple bind authentication.

During authentication, the LDAP directory is searched for an entry that matches the provided username. If a single unique match is found, a simple bind is attempted using the DN of the entry plus the provided password.

*Example Configuration Using LDAPIdentityProvider*:

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
      jwtSecret: "************"
      oauthOptions:
        accessTokenMaxAge: 1h
        accessTokenInactivityTimeout: 30m
        identityProviders:
        - name: ldap
          type: LDAPIdentityProvider
          mappingMethod: auto
          provider:
            host: 192.168.0.253:389
            managerDN: uid=root,cn=users,dc=nas
            managerPassword: ********
            userSearchBase: cn=users,dc=nas
            loginAttribute: uid
            mailAttribute: mail
kind: ConfigMap
name: kubesphere-config
namespace: kubesphere-system
```

For the above example:

| Parameter | Description |
|-----------|-------------|
| host | The name and port of the LDAP server. |
| readTimeout| Timeout while receiving data from remote server. Defaults to 15s. |
| startTLS | If specified, connections will use the ldaps:// protocol. |
| insecureSkipVerify | Used to turn off TLS certificate verify. |
| rootCA | Path to a trusted root certificate file. Default: use the host's root CA. |
| rootCAData | A raw certificate file can also be provided inline. Base64 encoded PEM file. |
| managerDN | DN to use to bind during the search phase. |
| managerPassword | Password to use to bind during the search phase. |
| userSearchBase | The search base is the distinguished name (DN) of a level of the directory tree below which all users can be found. |
| userSearchFilter | LDAP filter used to identify objects of type user. e.g. (objectClass=person). |
| loginAttribute | User naming attributes identify user objects, will be mapped to KubeSphere account name. |
| mailAttribute | The mail attribute will be mapped to the KubeSphere account. |

After apply the configuration, you will be able to login to KubeSphere using the account in the remote LDAP server.