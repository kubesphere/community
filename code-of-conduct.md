# KubeSphere Code of Conduct

This document makes a reference to the rules of behavior for all contributors and maintainers in the community. All members agree to follow them to foster the growth of the community of tolerance, respect, and mutual understanding.

In the attempt to adopt the best practices from the most well-known open-source and cloud-native projects, and work closely with the Cloud Native Computing Foundation (CNCF), our community members follow the rules outlined in the [CNCF Code of Conduct](https://github.com/cncf/foundation/blob/master/code-of-conduct.md).  

## Best Practices of Committing Code

Besides following the conduct above from CNCF, we also hope every contributor in this project could help us to improve the quality of code. Something you should know before checking in any new code lists below:

- As gopher, make sure you already read [the conduct of Go language](https://golang.org/conduct) and [the instruction of writing Go](https://golang.org/doc/effective_go.html).  
- Fork the project under your GitHub account and make the changes you want there.  
- Execute 'go fmt' for every piece of new code.  
- Every pulling request (PR) would be better constructed with only one commit, which could help code reviewer to go through your code efficiently, also helpful for every follower of this project to understand what happens in this PR. If you need to make any further code change to address the comments from reviewers, which means some new commits will be generated under this PR, you need to use 'git rebase' to combine those commits together.
- Every PR should only solve one problem or provide one feature. Don't put several different fixes into one PR.  
- At lease two code reviewers should involve into code reviewing process.
- Please introduce new third-party packages as little as possible to reduce the vendor dependency of this project. For example, don't import a full unit converting package but only use one function from it. For this case, you'd better write that function by yourself.
