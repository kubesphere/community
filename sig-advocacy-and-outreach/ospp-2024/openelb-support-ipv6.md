
# Project

OpenELB support IPV6

## Project Goal

OpenELB consists of two major components: controller and speaker.

- The controller is responsible for allocating/reclaiming IP addresses for services.
- The speaker is responsible for announcing the allocated IP addresses externally.

Therefore, the project also has two main goals:

- The controller supports IPv6 IPAM (IP address management).
- The speaker supports IPv6 announcement in different modes.

## Skills to Learn/Improve

- Golang
- Kubernetes
- OpenELB
- Network
- Gobgp
- NDP(Neighbor Discovery Protocol)
- keepalived

## Background

OpenELB is an open-source cloud-native load balancer that can be used to expose services through LoadBalancer-type Services in Kubernetes environments based on bare-metal servers, edge computing, and virtualization.

In a Kubernetes cluster in a cloud environment, load balancing services provided by cloud service providers can typically be used to expose services, but this is not possible in local environments. OpenELB allows users to create LoadBalancer-type Services to expose services in bare-metal servers, edge computing, and virtualized environments, and provides a consistent user experience with that in cloud environments.

## Project Details

OpenELB EIP is the IP pool allocated by OpenELB for LoadBalancer-type Services. The current version of OpenELB only supports IPv4. [Kubernetes has already supported IPv4/IPv6 dual-stack](https://kubernetes.io/docs/concepts/services-networking/dual-stack/) and has been stable since version 1.23. Therefore, we also need to support IPv6 IPAM and adapt the announcement of allocated IP addresses to different speaker modes.

## Outcomes

- Complete the development of corresponding functions
- Complete compatibility testing
- Provide documentation for instructions

## Quick Start

You can quickly learn about the basic capabilities of OpenELB by reading [OpenELB Overview](https://openelb.io/docs/overview/).

You can also get hands-on experiences by [installing OpenELB](https://openelb.io/docs/getting-started/installation/) and familiar with the basic usage of OpenELB by [Using OpenELB in Layer 2 Mode](https://openelb.io/docs/getting-started/usage/use-openelb-in-layer-2-mode/); and refer to [Configure IP Address Pools Using Eip](https://openelb.io/docs/getting-started/configuration/configure-ip-address-pools-using-eip/) to learn more about EIP details, and study specific implementations in combination with [OpenELB Code](https://github.com/openelb/openelb).

## Potential Mentors

- [renyunkang](https://github.com/renyunkang/)
- Email: rykren1998@gmail.com