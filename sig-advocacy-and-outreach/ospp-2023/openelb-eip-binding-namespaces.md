## Project

Binding OpenELB EIP to Namespace

## Project Goal

Implement the functionality of assigning OpenELB EIPs to one or more matching namespaces.

## Skills to Learn/Improve

- Golang

- Kubernetes

- OpenELB

## Background

OpenELB is an open-source cloud-native load balancer that can be used to expose services through LoadBalancer-type Services in Kubernetes environments based on bare-metal servers, edge computing, and virtualization.

In a Kubernetes cluster in a cloud environment, load balancing services provided by cloud service providers can typically be used to expose services, but this is not possible in local environments. OpenELB allows users to create LoadBalancer-type Services to expose services in bare-metal servers, edge computing, and virtualized environments, and provides a consistent user experience with that in cloud environments.

## Project Details

OpenELB EIP is the IP pool allocated by OpenELB for LoadBalancer-type Services. The current version of OpenELB supports setting a default EIP, which is equivalent to allocating it to all Namespaces. To manage and allocate IP pools with finer granularity, an EIP with a smaller IP mask or a specified IP range can be created and bound to a specified Namespace. The priorities of different EIPs should also be considered.

## Outcomes

- Complete the development of corresponding functions
- Complete compatibility testing
- Provide documentation for instructions

## Quick Start

You can quickly learn about the basic capabilities of OpenELB by reading [OpenELB Overview](https://openelb.io/docs/overview/).

You can also get hands-on experiences by [installing OpenELB](https://openelb.io/docs/getting-started/installation/) and familiar with the basic usage of OpenELB by [Using OpenELB in Layer 2 Mode](https://openelb.io/docs/getting-started/usage/use-openelb-in-layer-2-mode/); and refer to [Configure IP Address Pools Using Eip](https://openelb.io/docs/getting-started/configuration/configure-ip-address-pools-using-eip/) to learn more about EIP details, and study specific implementations in combination with [OpenELB Code](https://github.com/openelb/openelb).

## Potential Mentors

-   [renyunkang](https://github.com/renyunkang/)