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

| Group | Lead |  Slack Channel | Meeting Notes | Description |
|-------|-------------|-------|--------------|--------------------|
| [Apps](./sig-apps/) | [Hongliang Wang](https://github.com/hlwanghl) | [#sig-apps](https://kubesphere.slack.com/messages/sig-apps) | [Notes](https://docs.google.com/document/d/1nRAK2U9flkz-8z7bT2-T_0VneW3w1fx1fJtB5Bu3JyU/) | App charts for the built-in App Store |
| [App Store](./sig-appstore) | [Zhengyi Lai](https://github.com/zheng1) | [#sig-appstore](https://kubesphere.slack.com/messages/sig-appstore) | [Notes](https://docs.google.com/document/d/1FYxeQOiwN3jL6EPeIA71iB3gXZfNf-PhSufVaywFbxI/) | App Store, App template management |
| [Architecture](./sig-architecture) | [Lu Liu](https://github.com/leoendless), [Benjamin Huo](https://github.com/benjaminhuo) | [#sig-architecture](https://kubesphere.slack.com/messages/sig-architecture) | [Notes](https://docs.google.com/document/d/1lqL0c6SpxLxRbwVk870-9HDeGIwVodSRJV-Uh4hPemQ/) | system architecture |
| [Console](./sig-console) | [Lu Liu](https://github.com/leoendless) | [#sig-console](https://kubesphere.slack.com/messages/sig-console) | [Notes](https://docs.google.com/document/d/1a2RHltQm3armW4Jf7m1aYFTjdvlqiuW5hW2-KBeLqi0/) | dashboard |
| [DevOps](./sig-devops) | [Jeff Zhang](https://github.com/zryfish) | [#sig-devops](https://kubesphere.slack.com/messages/sig-devops) | [Notes](https://docs.google.com/document/d/1ZORl7ZhRlZxKXFle2LGPRJqXzlr6EDhu2A7qzjybfro/) | pipeline, s2i, b2i, image registry |
| [Docs](./sig-docs) | [Pengfei Zhou](https://github.com/FeynmanZhou) | [#sig-docs](https://kubesphere.slack.com/messages/sig-docs) | [Notes](https://docs.google.com/document/d/1tyB2RDJFmfwFfO2ok9dH7ttZRICDiaogSI12Ajz9CD0/) | User docs, kubesphere.io |
| [Installation](./sig-installation) | [Feng Guo](https://github.com/pixiake) | [#sig-installation](https://kubesphere.slack.com/messages/sig-installation) | [Notes](https://docs.google.com/document/d/1sXMKViZ5cchbaBajRZiJsaSdMAQ1GpmDKCcq3UwT3Vg/) | KubeSphere installer and deployment |
| [Microservice management](./sig-microservice) | [Jeff Zhang](https://github.com/zryfish) | [#sig-microservice](https://kubesphere.slack.com/messages/sig-microservice) | [Notes](https://docs.google.com/document/d/1eAAbdIxJwFgNjkU9xvQ8SrezW7pHgPryzOAPjZYjvFg/) | architecture, microservice governance |
| [Multi-cluster](./sig-multicluster) | [Jeff Zhang](https://github.com/zryfish) | [#sig-multicluster](https://kubesphere.slack.com/messages/sig-multicluster) | [Notes](https://docs.google.com/document/d/1P0NaJbAYTK4BnMazJcrc4he-sh2YpZNvG1rkPQrNhpY/) | multi-cluster management |
| Multi-tenancy| [Hongming Wan](https://github.com/wansir) | [#multitenancy](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | workspace, IAM |
| Network | [Zhengyi Lai](https://github.com/zheng1) | [#network](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | network policy, CNI plugins, SDN |
| Observability | [Benjamin Huo](https://github.com/benjaminhuo) | [#observability](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | Logging, Monitoring, Alerting, Notification |
| Release | [Calvin Yu](https://github.com/calvinyv) | [#release](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | release of each version |
| Storage | [Xin Wang](https://github.com/wnxn) | [#storage](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | CSI plugins |
| Testing | [Yaping Liu](https://github.com/liuyp2018) | [#testing](https://kubesphere.slack.com/archives/CLHL8R1C7) | [Notes](https://github.com/kubesphere/kubesphere/issues?q=is%3Aopen+is%3Aissue+label%3Aarea%2Fmonitoring+) | test, release |
