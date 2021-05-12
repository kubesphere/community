# Project

KubeSphere Gatekeeper Integration

## Project Goal

Integrate [Gatekeeper](https://github.com/open-policy-agent/gatekeeper) as an admission policy engine to [KubeSphere](https://github.com/kubesphere/kubesphere/).

## Skills to Learn/Improve

* React
* Golang
* OpenAPI
* Open Policy Agent
* Kubernetes

## Background

Kubernetes allows decoupling policy decisions from the inner workings of the API Server by means of admission controller webhooks, which are executed whenever a resource is created, updated or deleted. Gatekeeper is a validating (mutating TBA) webhook that enforces CRD-based policies executed by Open Policy Agent. We can integrate Gatekeeper to KubeSphere, and manage the common rules and policies through CRD.

## Project details

[Open Policy Agent](https://github.com/open-policy-agent/opa), a policy engine for Cloud Native environments hosted by CNCF as an incubation-level project.
[Gatekeeper](https://github.com/open-policy-agent/gatekeeper), policy management tool based on K8s admission webhook and OPA.

We want to integrate Gatekeeper into KubeSphere as an admission policy engine.

## Outcomes

The potential outcomes might include:

- Integrate Gatekeeper during KubeSphere installation
- Complete the basic function integration of Gatekeeper
- Completion test

## Links

* https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/
* https://github.com/open-policy-agent/opa
* https://github.com/open-policy-agent/gatekeeper

## Quickstart

You can start with [a minimal KubeSphere](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/). 

[Install Gatekeeper](https://open-policy-agent.github.io/gatekeeper/website/docs/install).

First, you need to be familiar with KubeSphere and Gatekeeper. 

## Newbie-Friendly Issues

* [KubeSphere community newbie-friendly issues](https://github.com/search?q=user%3Akubesphere+label%3A%22good+first+issue%22+state%3Aopen&type=Issues&ref=advsearch&l=&l=)

## Potential Mentors

* [Hongming](https://github.com/wansir/)
* [Roland](https://github.com/rolandma1986/)
