## How to create S2IRun automatically by trigger

​	In the version of 2.1.X or other previous, if users want to rebuild program by S2I-Operator when the source code is updated, must create a new CR S2IRun by manually or click button `rebuild` in the console. This is very troublesome and non-automated, To be automatized, we need something to help us trigger s2i build automated.

​	The module of trigger in S2I-Operator allowed the user to create S2I resources automatically when be triggered by certain events. For example, if user sets a webhook in GitHub or other SCM, When the specified events happen, such as create a commit or other action,  S2I-Operator will receive a POST request, and create s2iRun resource related with the URL defined. 

![](images/s2i-trigger-flow.svg)



​	Currently, only GitHub-webhook and General-webhook are supported. GitHub-webhook handler can handle push events from the GitHub webhook server, and other event types will be ignored. General-webhook handler can handle any request from any server, Whether the method is Get or Post, after receiving the request, it will create s2iRun CR resource automatically, and then S2I-Operator will create a job to clone and build the program. 

**Below is the URL defined for s2i trigger:**

*GitHub-webhook:*

`http://endpoint/s2itrigger/v1alpha1/github/namespaces/{mamespace}/s2ibuilders/{s2ibuilderName}`

*General-webhook:*

`http://endpoint/s2itrigger/v1alpha1/general/namespaces/{mamespace}/s2ibuilders/{s2ibuilderName}`

In the future, we will provide more types of webhook handlers.

