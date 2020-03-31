# KubeSphere Special Interest Groups

Most community activities are organized into a variety of Special Interest Group (SIG).

## Why Special Interest Groups

KubeSphere SIGs are organizations responsible for the design and implementation of some relatively large architectural aspects of the overall KubeSphere project. SIGs operate with a fair amount of autonomy within the broader scope of the project.

Generally, SIGs focus on specific technologies and features. For example, the storage SIG primarily focuses on design, integration and development for the Kubernetes-based storage within KubeSphere.

## Run a SIG

Leads are responsible for running a SIG. Running the group involves a few activities:

- **Meetings**. Prepare the agenda and run the regular SIG meetings. Ensure the meetings are recorded, and properly archived on YouTube.

- **Operation**. Operate the related Slack channel and GitHub issue, make sure the questions and proposals are answered in time.

- **Notes**. Ensure that meeting notes are kept up to date. Provide a link to the recorded meeting in the notes. The lead may delegate note-taking duties.

- **Roadmap**. Establish and maintain a roadmap for the SIG outlining the areas of focus for the SIG over the next three months.

### Be Open

The community design process is done in open way. SIGs should communicate primarily through the public tools, through design documents in the SIG’s folder, through GitHub issues, and GitHub PRs. Avoid private emails or messages when possible.

### Make Decisions

In general, SIGs operate in a highly cooperative environment. The members of a SIG discuss designs in the open and take input from the community at large when making technical choices. The SIG leads are ultimately responsible for setting the direction of the SIG and making the technical choices affecting the SIG.

## SIGs

The SIGs at present are:

| Group | Lead | Design Docs |  Slack Channel | Meeting Notes | Description |
|-------|-------------|-------|---------------|--------------|--------------------|
| Apps | [Hongliang Wang](https://github.com/hlwanghl) | [Design documentation](./contribution/design/sig-observability) | [#apps](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | App charts for the built-in App Store |
| App Store | [Zhengyi Lai](https://github.com/zheng1) | [Design documentation](./contribution/design/sig-observability) | [#appstore](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | App Store, App template management |
| Architecture| [Lu Liu](https://github.com/leoendless), [Benjamin Huo](https://github.com/benjaminhuo) | [Design documentation](./contribution/design/sig-observability) | [#architecture](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | system architecture |
| Console | [Lu Liu](https://github.com/leoendless) | [Design documentation](./contribution/design/sig-observability) | [#console](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | dashboard |
| DevOps | [Jeff Zhang](https://github.com/zryfish) | [Design documentation](./contribution/design/sig-observability) | [#devops](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | pipeline, s2i, b2i, image registry |
| Docs | [Pengfei Zhou](https://github.com/FeynmanZhou) | [Design documentation](./contribution/design/sig-observability) | [#docs](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | User docs, kubesphere.io |
| Installation | [Feng Guo](https://github.com/pixiake) | [Design documentation](./contribution/design/sig-observability) | [#installation](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | KubeSphere installer and deployment |
| Microservice management| [Jeff Zhang](https://github.com/zryfish) | [Design documentation](./contribution/design/sig-observability) | [#microservice](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | architecture, microservice governance |
| Multi-cluster| [Jeff Zhang](https://github.com/zryfish) | [Design documentation](./contribution/design/sig-observability) | [#multicluster](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | multi-cluster management |
| Multi-tenancy| [Hongming Wan](https://github.com/wansir) | [Design documentation](./contribution/design/sig-observability) | [#multitenancy](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | workspace, IAM |
| Network | [Zhengyi Lai](https://github.com/zheng1) | [Design documentation](./contribution/design/sig-observability) | [#network](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | network policy, CNI plugins, SDN |
| Observability | [Benjamin Huo](https://github.com/benjaminhuo) | [Design documentation](./contribution/design/sig-observability) | [#observability](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | Logging, Monitoring, Alerting, Notification |
| Release | [Calvin Yu](https://github.com/calvinyv) | [Design documentation](./contribution/design/sig-observability) | [#release](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | release of each version |
| Storage | [Xin Wang](https://github.com/wnxn) | [Design documentation](./contribution/design/sig-observability) | [#storage](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | CSI plugins |
| Testing | [Yaping Liu](https://github.com/liuyp2018) | [Design documentation](./contribution/design/sig-observability) | [#testing](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | test, release |
