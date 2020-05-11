# KubeSphere Jenkins Plugin

As we all know, KubeSphere uses Jenkins as the CI / CD engine by default.
Using Jenkins is like building Lego bricks. It is a combination of Jenkins plugins.
KubeSphere also has its own Jenkins Plugin to extend the capabilities of the CI / CD engine.
At present, we use a Jenkins Plugin to complete multiple extension functions (the traditional method may build multiple Plugins).
This is because each version of KubeSphere is bundled with a specific version of Plugin, 
so there will be no conflict between plugins. Using this method also makes it easier to install and maintain plugins.
The plugin is currently maintained in [Jenkins github org](https://github.com/jenkinsci/kubesphere-extension-plugin).

## Main Functions

Next we will explain the several functions that the plugin currently provides.

### Custom ContainerFilter

[ContainerFilter](https://jenkins.io/doc/developer/extensions/blueocean-rest-impl/) is an ExtensionPoint of Jenkins BlueOcean Plugin.

KubeSphere extends this extension point to implement a specific filter in Jenkins to filter the BlueOcean API's response.

### KubeSphere ApiToken Authenticator

[BasicHeaderAuthenticator](https://jenkins.io/doc/developer/extensions/jenkins-core/#basicheaderauthenticator) is an ExtensionPoint of Jenkins Core.

This extension point allows us to implement our own authentication logic, not just using user systems such as LDAP.

When a user accesses the DevOps part of the KubeSphere interface, the user calls Jenkins' API (for example, triggering a build).
At this point, KubeSphere needs a way to access Jenkins as a user.  

This extension implements such functionality. When accessing the Jenkins API, users can use KubeSphere's API token for authentication.

### KubeSphere Notification

KubeSphereNotification implements multiple extension points within the Jenkins Core for event notification.

Both notification methods and event types are extensible.
Currently we have implemented a Webhook notification method with the following event types:

```markdown
- jenkins.job.started (Events are triggered when the pipeline started)
- jenkins.job.completed (Events are triggered when the pipeline completed)
- jenkins.job.finalized (Events are triggered when the pipeline finalized)
- jenkins.job.input.started (Events are triggered when the pipeline input step started)
- jenkins.job.input.proceeded (Events are triggered when the pipeline input step proceeded)
- jenkins.job.input.aborted (Events are triggered when the pipeline input step aborted)
```

For more detailed information we recommend you read the documentation of the plugin.

## Configure the Plugin

Currently, the two most popular Jenkins plugin configuration methods are [Groovy Script](https://wiki.jenkins.io/display/JENKINS/Post-initialization+script) and
[CasC Plugin](https://github.com/jenkinsci/configuration-as-code-plugin).
We recommend to use CasC to configure plugins. Therefore, the configuration method of CasC is implemented in our plugins.
Detailed information can refer to the documentation of the plugin.

## Plugin Release

The way plugins are published is no different from regular Jenkins plugins.
You can read the official Jenkins plugin [release documentation](https://jenkins.io/doc/developer/publishing/releasing/) to publish KubeSphere Jenkins plugin.
