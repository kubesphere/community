# Simplified Chinese Localization Task List of KubeSphere Documentation 3.0

The tables below contain all the guides in KubeSphere documentation that need to be translated into Simplified Chinese. Not all guides in the documentation are in it since some guides are not ready for translation yet. These tables will be updated regularly.

Please claim the guide that you want to translate by submitting a pr to add your name under **Translator**. Your contribution is highly appreciated as it benefits all KubeSphere users of the language.

Please read the following rules before you claim a task:

- Submit your translation to the **master branch** of [website repository](https://github.com/kubesphere/website).
- Click the guide name in the following table which will direct you to the en website. They should be used as source files, which are stored in the path **website/content/en/docs**. You may see some en files are already in the path **website/content/zh/docs**, while some of them may not be the same as the en files in **website/content/en/docs**. In short, use files in the path **website/content/en/docs** as the source file for translation, and save the translated files in the same path in **website/content/zh/docs**.
- When you submit your translation, only submit **one guide at a time in a pull request**, which can greatly improve the review efficiency.
- For more information about the documentation and localization style guide, see [KubeSphere Documentation Style Guide](https://github.com/kubesphere/website/blob/master/KubeSphere%20Documentation%20Style%20Guide.md) and [KubeSphere Localization Style Guide (for Simplified Chinese)](https://github.com/kubesphere/website/blob/master/localization_style_guides/KubeSphere%20Localization%20Style%20Guide%20(for%20Simplified%20Chinese).md).

| Quickstarts                                                  | Translator                 | PR Link |
| ------------------------------------------------------------ | -------------------------- | ------- |
| [All-in-one Installation on Linux](https://kubesphere.io/docs/quick-start/all-in-one-on-linux/) | https://github.com/hantmac |         |
| [Minimal KubeSphere on Kubernetes](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/) | https://github.com/shenhonglei | [424](https://github.com/kubesphere/website/pull/424) |
| [Create Workspace, Project, Account and Role](https://kubesphere.io/docs/quick-start/create-workspace-and-project/) |   https://github.com/ckyx                         |         |
| [Deploy Bookinfo and Manage Traffic](https://kubesphere.io/docs/quick-start/deploy-bookinfo-to-k8s/) |    https://github.com/ckyx                        |         |
| [Compose and Deploy Wordpress](https://kubesphere.io/docs/quick-start/wordpress-deployment/) | https://github.com/Jaycean |         |
| [Enable Pluggable Components](https://kubesphere.io/docs/quick-start/enable-pluggable-components/) | https://github.com/Jaycean |         |
| [Index Page](https://kubesphere.io/docs/quick-start/)        | https://github.com/Jaycean |         |

| Installing on Linux                                          | Translator                  | PR Link |
| ------------------------------------------------------------ | --------------------------- | ------- |
| [Index Page](https://kubesphere.io/docs/installing-on-linux/) | https://github.com/hantmac  |  https://github.com/kubesphere/website/pull/434   |
| [Overview](https://kubesphere.io/docs/installing-on-linux/introduction/intro/) |                             |         |
| [Multi-node Installation](https://kubesphere.io/docs/installing-on-linux/introduction/multioverview/) |                             |         |
| [Air-gapped Installation](https://kubesphere.io/docs/installing-on-linux/introduction/air-gapped-installation/) |                             |         |
| [Port Requirements](https://kubesphere.io/docs/installing-on-linux/introduction/port-firewall/) | https://github.com/caojiele |         |
| [Kubernetes Cluster Configuration](https://kubesphere.io/docs/installing-on-linux/introduction/vars/) | https://github.com/caojiele |         |
| [Persistent Storage Configuration](https://kubesphere.io/docs/installing-on-linux/introduction/storage-configuration/) |                             |         |
| [Add New Nodes](https://kubesphere.io/docs/installing-on-linux/cluster-operation/add-new-nodes/) |                             |         |
| [Remove Nodes](https://kubesphere.io/docs/installing-on-linux/cluster-operation/remove-nodes/) | https://github.com/caojiele |         |
| [Uninstalling KubeSphere and Kubernetes](https://kubesphere.io/docs/installing-on-linux/uninstalling/uninstalling-kubesphere-and-kubernetes/) | https://github.com/caojiele |         |
| [Configure Booster for Installation](https://kubesphere.io/docs/installing-on-linux/faq/configure-booster/) |                             |         |

| Installing on Kubernetes                                     | Translator                  | PR Link |
| ------------------------------------------------------------ | --------------------------- | ------- |
| [Index Page](https://kubesphere.io/docs/installing-on-kubernetes/) | https://github.com/shenhonglei | [427](https://github.com/kubesphere/website/pull/427) |
| [Overview](https://kubesphere.io/docs/installing-on-kubernetes/introduction/overview/) |                             |         |
| [Prerequisites](https://kubesphere.io/docs/installing-on-kubernetes/introduction/prerequisites/) |                             |         |
| [Deploy KubeSphere on DigitalOcean](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-do/) |                             |         |
| [Deploy KubeSphere on GKE](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-gke/) |                             |         |
| [Deploy KubeSphere on AKS](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-aks/) |                             |         |
| [Uninstalling KubeSphere from Kubernetes](https://kubesphere.io/docs/installing-on-kubernetes/uninstalling/uninstalling-kubesphere-from-k8s/) | https://github.com/caojiele |         |

| Multi-cluster Management                                     | Translator | PR Link |
| ------------------------------------------------------------ | ---------- | ------- |
| [Index Page](https://kubesphere.io/docs/multicluster-management/) | [Bingo Liao](https://github.com/forearrow/) |         |
| [Overview](https://kubesphere.io/docs/multicluster-management/introduction/overview/) | [Bingo Liao](https://github.com/forearrow/) |         |
| [Kubernetes Federation in KubeSphere](https://kubesphere.io/docs/multicluster-management/introduction/kubefed-in-kubesphere/) | [Bingo Liao](https://github.com/forearrow/) |         |
| [Direct Connection](https://kubesphere.io/docs/multicluster-management/enable-multicluster/direct-connection/) | [Bingo Liao](https://github.com/forearrow/) |         |
| [Agent Connection](https://kubesphere.io/docs/multicluster-management/enable-multicluster/agent-connection/) | [Bingo Liao](https://github.com/forearrow/) |         |
| [Retrieve KubeConfig](https://kubesphere.io/docs/multicluster-management/enable-multicluster/retrieve-kubeconfig/) | [Bingo Liao](https://github.com/forearrow/) |         |

| Enable Pluggable Components                                  | Translator | PR Link |
| ------------------------------------------------------------ | ---------- | ------- |
| [Index Page](https://kubesphere.io/docs/pluggable-components/) | [Haili Zhang](https://github.com/webup)           |         |
| [KubeSphere App Store](https://kubesphere.io/docs/pluggable-components/app-store/) | [Haili Zhang](https://github.com/webup)           |         |
| [KubeSphere DevOps System](https://kubesphere.io/docs/pluggable-components/devops/) | [Haili Zhang](https://github.com/webup)           |         |
| [KubeSphere Auditing Logs](https://kubesphere.io/docs/pluggable-components/auditing-logs/) | [Haili Zhang](https://github.com/webup)           |         |
| [KubeSphere Events](https://kubesphere.io/docs/pluggable-components/events/) | [Haili Zhang](https://github.com/webup)           |         |
| [KubeSphere Logging System](https://kubesphere.io/docs/pluggable-components/logging/) | [Haili Zhang](https://github.com/webup)           |         |
| [KubeSphere Service Mesh](https://kubesphere.io/docs/pluggable-components/service-mesh/) | [Haili Zhang](https://github.com/webup)           |         |
| [KubeSphere Alerting and Notification](https://kubesphere.io/docs/pluggable-components/alerting-notification/) | [Haili Zhang](https://github.com/webup)           |         |
| [Network Policy](https://kubesphere.io/docs/pluggable-components/network-policy/) | [Haili Zhang](https://github.com/webup)           |         |

| Upgrade                                                      | Translator                   | PR Link |
| ------------------------------------------------------------ | ---------------------------- | ------- |
| [Index Page](https://kubesphere.io/docs/upgrade/)            | https://github.com/reneeteng |         |
| [Overview](https://kubesphere.io/docs/upgrade/upgrade-overview/) | https://github.com/reneeteng |         |
| [Upgrade with KubeKey](https://kubesphere.io/docs/upgrade/upgrade-with-kubekey/) |                              |         |
| [Upgrade with ks-installer](https://kubesphere.io/docs/upgrade/upgrade-with-ks-installer/) |                              |         |
| [Changes after Upgrade](https://kubesphere.io/docs/upgrade/what-changed/) | https://github.com/caojiele  |         |
| [FAQ](https://kubesphere.io/docs/upgrade/upgrade-faq/)       | https://github.com/caojiele  |         |

| Cluster Administration                                       | Translator | PR Link |
| ------------------------------------------------------------ | ---------- | ------- |
| [Cluster Status Monitoring](https://kubesphere.io/docs/cluster-administration/cluster-status-monitoring/) | [Kai Zhang](https://github.com/mvpzhangkai)         |         |
| [Application Resources Monitoring](https://kubesphere.io/docs/cluster-administration/application-resources-monitoring/) |            |         |
| [Mail Server](https://kubesphere.io/docs/cluster-administration/cluster-settings/mail-server/) | https://github.com/shenhonglei | [458](https://github.com/kubesphere/website/pull/458) |
| [Node Management](https://kubesphere.io/docs/cluster-administration/nodes/) |  | |
| [Cluster Shutdown and Restart](https://kubesphere.io/docs/cluster-administration/shuting-down-and-restart-cluster-cracefully/) |  | |
| [Alerting Policy (Node Level)](https://kubesphere.io/docs/cluster-administration/cluster-wide-alerting-and-notification/alerting-policy/) |  | |
| [Alerting Message (Node Level)](https://kubesphere.io/docs/cluster-administration/cluster-wide-alerting-and-notification/alerting-message/) |  | |
| [Index Page](https://kubesphere.io/docs/cluster-administration/) |  | |

| Project User Guide                                           | Translator                                    | PR Link |
| ------------------------------------------------------------ | --------------------------------------------- | ------- |
| [Index Page](https://kubesphere.io/docs/project-user-guide/) | [shenhonglei](https://github.com/shenhonglei) | [464](https://github.com/kubesphere/website/pull/464)        |
| [Deployments](https://kubesphere.io/docs/project-user-guide/application-workloads/deployments/) |                  https://github.com/hantmac                             |         |
| [StatefulSets](https://kubesphere.io/docs/project-user-guide/application-workloads/statefulsets/) |                                               |         |
| [DaemonSets](https://kubesphere.io/docs/project-user-guide/application-workloads/daemonsets/) |                                               |         |
| [Jobs](https://kubesphere.io/docs/project-user-guide/application-workloads/jobs/) |                                               |         |
| [CronJobs](https://kubesphere.io/docs/project-user-guide/application-workloads/cronjob/) |                                               |         |
| [Services](https://kubesphere.io/docs/project-user-guide/application-workloads/services/) |                https://github.com/hantmac                               |         |
| [Container Image Settings](https://kubesphere.io/docs/project-user-guide/application-workloads/container-image-settings/) |                                               |         |
| [Introduction](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/introduction/) |                                               |         |
| [Monitor MySQL](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/get-started/monitor-mysql/) |                                               |         |
| [Monitor Sample Web](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/get-started/monitor-sample-web/) |                                               |         |
| [Overview](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/visualization/overview/) |                                               |         |
| [Panels](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/visualization/panel/) |                                               |         |
| [Querying](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/visualization/querying/) |                                               |         |
| [Alerting Policy (Workload Level)](https://kubesphere.io/docs/project-user-guide/alerting/alerting-policy/) |                                               |         |
| [Alerting Message (Workload Level)](https://kubesphere.io/docs/project-user-guide/alerting/alerting-message/) |                                               |         |

| DevOps User Guide                                            | Translator | PR Link |
| ------------------------------------------------------------ | ---------- | ------- |
| [Index Page](https://kubesphere.io/docs/devops-user-guide/)  |            |         |
| [Credential Management](https://kubesphere.io/docs/devops-user-guide/how-to-use/credential-management/) |            |         |
| [Set CI Node for Dependency Cache](https://kubesphere.io/docs/devops-user-guide/how-to-use/set-ci-node/) |            |         |
| [Set Email Server for KubeSphere Pipelines](https://kubesphere.io/docs/devops-user-guide/how-to-use/jenkins-email/) |            |         |
| [Integrate SonarQube into Pipeline](https://kubesphere.io/docs/devops-user-guide/how-to-integrate/sonarqube/) |            |         |
