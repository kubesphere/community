# Overview

This document explains how cherry picks are managed on release branches within
the `kubesphere/kubesphere` repository.
A common use case for this task is backporting PRs from master to release
branches.

We copied release process from K8s. See also [cherry-picks](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-release/cherry-picks.md).

## Prerequisites

- [Contributor License Agreement](/cla.md) is
  considered implicit for all code within cherry pick pull requests,
  **unless there is a large conflict**.
- A pull request merged against the `master` branch.
- The release branch exists (example: [`release-3.0`](https://github.com/kubesphere/kubesphere/tree/release-3.0))
- The normal git and GitHub configured shell environment for pushing to your
  kubernetes `origin` fork on GitHub and making a pull request against a
  configured remote `upstream` that tracks
  `https://github.com/kubesphere/kubesphere.git`, including `GITHUB_USER`.
- Have `hub` installed, which is most easily installed via
  `go get github.com/github/hub` assuming you have a standard golang
  development environment.
- A github personal access token which has permissions to access public repositories.

## What Kind of PRs are Good for Cherry Picks

Compared to the normal master branch's merge volume across time,
the release branches see one or two orders of magnitude less PRs.
This is because there is an order or two of magnitude higher scrutiny.
Again, the emphasis is on critical bug fixes, e.g.,

- Loss of data
- Memory corruption
- Panic, crash, hang
- Security

If you are proposing a cherry pick and it is not a clear and obvious critical
bug fix, please reconsider. If upon reflection you wish to continue, bolster
your case by supplementing your PR with e.g.,

- A GitHub issue detailing the problem

- Scope of the change

- Risks of adding a change

- Risks of associated regression

- Testing performed, test cases added

- Key stakeholder SIG reviewers/approvers attesting to their confidence in the
  change being a required backport

If the change is in cloud provider-specific platform code (which is in the
process of being moved out of core Kubernetes), describe the customer impact,
how the issue escaped initial testing, remediation taken to prevent similar
future escapes, and why the change cannot be carried in your downstream fork of
the Kubernetes project branches.

It is critical that our full community is actively engaged on enhancements in
the project. If a released feature was not enabled on a particular provider's
platform, this is a community miss that needs to be resolved in the `master`
branch for subsequent releases. Such enabling will not be backported to the
patch release branches.

## Initiate a Cherry Pick

- Run the [cherry pick script](https://github.com/kubesphere/kubesphere/blob/master/hack/cherry_pick_pull.sh)

  This example applies a master branch PR #3796 to the remote branch
  `upstream/release-3.1`:

  ```shell
  hack/cherry_pick_pull.sh upstream/release-3.1 3796
  ```

  - Be aware the cherry pick script assumes you have a git remote called
    `upstream` that points at the KubeSphere github org.

    Please see our [Development Workflow](development-workflow.md).

  - You will need to run the cherry pick script separately for each patch
    release you want to cherry pick to.

  - If `GITHUB_TOKEN` is not set you will be asked for your github password:
    provide the github [personal access token](https://github.com/settings/tokens) rather than your actual github
    password. If you can securely set the environment variable `GITHUB_TOKEN`
    to your personal access token then you can avoid an interactive prompt.
    Refer [https://github.com/github/hub/issues/2655#issuecomment-735836048](https://github.com/github/hub/issues/2655#issuecomment-735836048)


- Your cherry pick PR will immediately get the
  `do-not-merge/cherry-pick-not-approved` label.