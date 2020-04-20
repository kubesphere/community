## How to create S2IRun automatically by trigger

​	In the version of 2.1.X or other previous, if users want to rebuild program by S2I-Operator when the source code is updated, must create a new CR S2IRun by manually or click button `rebuild` in the console. This is very troublesome and non-automated, To be automatized, we need something to help us trigger s2i build automated.

​	The module of trigger in S2I-Operator allowed the user to create S2I resources automatically when be triggered by certain events. For example, if user sets a webhook in GitHub or other SCM, When the specified events happen, such as create a commit or other action,  S2I-Operator will receive a POST request, and create s2iRun resource related with the URL defined. 

![](images/s2i-trigger-flow.svg)



​	Currently, only GitHub-webhook and General-webhook are supported. GitHub-webhook handler can handle push events from the GitHub webhook server, and extract the commitId, author and other information from the webhook payload, so the operation will be more accurate. General-webhook handler can receive any SCM webhook or other customize server theoretically, Whether the method is Get or Post, but there may be some meaningless auto-runs because the webhook payload cannot be parsed. General-webhook handler use `secretCode` that in URL query paramters for authentication, `secretCode` must match the data with field secretCode from CR s2iBuilder. After receiving the request and authentication success, it will create s2iRun CR resource automatically, and then S2I-Operator will create a job to clone and build the program. Therefore, the user should select the correct webhook type when configuring the webhook.

**Below is the URL defined for s2i trigger:**

*GitHub-webhook:*

`http://endpoint/s2itrigger/v1alpha1/github/namespaces/{namespace}/s2ibuilders/{s2ibuilderName}?secretCode={secretCode}`

*General-webhook:*

`http://endpoint/s2itrigger/v1alpha1/general/namespaces/{namespace}/s2ibuilders/{s2ibuilderName}`

In the future, we will provide more types of webhook handlers.

