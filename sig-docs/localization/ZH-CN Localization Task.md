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
| [All-in-one Installation on Linux](https://kubesphere.io/docs/quick-start/all-in-one-on-linux/) | https://github.com/hantmac |      https://github.com/kubesphere/website/pull/490   |
| [Minimal KubeSphere on Kubernetes](https://kubesphere.io/docs/quick-start/minimal-kubesphere-on-k8s/) | https://github.com/shenhonglei | [424](https://github.com/kubesphere/website/pull/424) |
| [Create Workspace, Project, Account and Role](https://kubesphere.io/docs/quick-start/create-workspace-and-project/) |   https://github.com/ckyx                         |         |
| [Deploy Bookinfo and Manage Traffic](https://kubesphere.io/docs/quick-start/deploy-bookinfo-to-k8s/) |    https://github.com/ckyx                        |         |
| [Compose and Deploy Wordpress](https://kubesphere.io/docs/quick-start/wordpress-deployment/) | https://github.com/Jaycean | [479](https://github.com/kubesphere/website/pull/479) |
| [Enable Pluggable Components](https://kubesphere.io/docs/quick-start/enable-pluggable-components/) | https://github.com/Jaycean | [476](https://github.com/kubesphere/website/pull/476) |
| [Index Page](https://kubesphere.io/docs/quick-start/)        | https://github.com/Jaycean | [363](https://github.com/kubesphere/website/pull/363) |

| Installing on Linux                                          | Translator                  | PR Link |
| ------------------------------------------------------------ | --------------------------- | ------- |
| [Index Page](https://kubesphere.io/docs/installing-on-linux/) | https://github.com/hantmac  |  https://github.com/kubesphere/website/pull/434   |
| [Overview](https://kubesphere.io/docs/installing-on-linux/introduction/intro/) | https://github.com/willzhang  |         |
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
| [Overview](https://kubesphere.io/docs/installing-on-kubernetes/introduction/overview/) | https://github.com/willzhang | [540](https://github.com/kubesphere/website/pull/540)        |
| [Prerequisites](https://kubesphere.io/docs/installing-on-kubernetes/introduction/prerequisites/) | https://github.com/willzhang |[600](https://github.com/kubesphere/website/pull/600)         |
| [Deploy KubeSphere on DigitalOcean](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-do/) | https://github.com/willzhang |[595](https://github.com/kubesphere/website/pull/595)         |
| [Deploy KubeSphere on GKE](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-gke/) | https://github.com/willzhang | [600](https://github.com/kubesphere/website/pull/600) |
| [Deploy KubeSphere on AKS](https://kubesphere.io/docs/installing-on-kubernetes/hosted-kubernetes/install-kubesphere-on-aks/) | https://github.com/willzhang | [578](https://github.com/kubesphere/website/pull/578)        |
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
| [Upgrade with KubeKey](https://kubesphere.io/docs/upgrade/upgrade-with-kubekey/) | [Wei Zhang](https://github.com/arugal)     |         |
| [Upgrade with ks-installer](https://kubesphere.io/docs/upgrade/upgrade-with-ks-installer/) | [Wei Zhang](https://github.com/arugal)   |         |
| [Changes after Upgrade](https://kubesphere.io/docs/upgrade/what-changed/) | https://github.com/caojiele  |         |
| [FAQ](https://kubesphere.io/docs/upgrade/upgrade-faq/)       | https://github.com/caojiele  |         |

| Cluster Administration                                       | Translator | PR Link |
| ------------------------------------------------------------ | ---------- | ------- |
| [Cluster Status Monitoring](https://kubesphere.io/docs/cluster-administration/cluster-status-monitoring/) | [Kai Zhang](https://github.com/mvpzhangkai)         |  [478](https://github.com/kubesphere/website/pull/478)       |
| [Application Resources Monitoring](https://kubesphere.io/docs/cluster-administration/application-resources-monitoring/) | [Kai Zhang](https://github.com/mvpzhangkai) | [544](https://github.com/kubesphere/website/pull/544)        |
| [Mail Server](https://kubesphere.io/docs/cluster-administration/cluster-settings/mail-server/) | https://github.com/shenhonglei | [458](https://github.com/kubesphere/website/pull/458) |
| [Node Management](https://kubesphere.io/docs/cluster-administration/nodes/) | [Kai Zhang](https://github.com/mvpzhangkai) | [557](https://github.com/kubesphere/website/pull/557)|
| [Cluster Shutdown and Restart](https://kubesphere.io/docs/cluster-administration/shut-down-and-restart-cluster-gracefully/) |[Kai Zhang](https://github.com/mvpzhangkai)  |[583](https://github.com/kubesphere/website/pull/583) |
| [Alerting Policy (Node Level)](https://kubesphere.io/docs/cluster-administration/cluster-wide-alerting-and-notification/alerting-policy/) | [Kai Zhang](https://github.com/mvpzhangkai) | [577](https://github.com/kubesphere/website/pull/577) |
| [Alerting Message (Node Level)](https://kubesphere.io/docs/cluster-administration/cluster-wide-alerting-and-notification/alerting-message/) | [Kai Zhang](https://github.com/mvpzhangkai) | [568](https://github.com/kubesphere/website/pull/568)|
| [Index Page](https://kubesphere.io/docs/cluster-administration/) | [Kai Zhang](https://github.com/mvpzhangkai) | [559](https://github.com/kubesphere/website/pull/559) |

| Project User Guide                                           | Translator                                    | PR Link                                               |
| ------------------------------------------------------------ | --------------------------------------------- | ----------------------------------------------------- |
| [Index Page](https://kubesphere.io/docs/project-user-guide/) | [shenhonglei](https://github.com/shenhonglei) | [464](https://github.com/kubesphere/website/pull/464) |
| [Deployments](https://kubesphere.io/docs/project-user-guide/application-workloads/deployments/) | https://github.com/hantmac                    |                                                       |
| [StatefulSets](https://kubesphere.io/docs/project-user-guide/application-workloads/statefulsets/) | [Kai Zhang](https://github.com/mvpzhangkai)  |                                                       |
| [DaemonSets](https://kubesphere.io/docs/project-user-guide/application-workloads/daemonsets/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Jobs](https://kubesphere.io/docs/project-user-guide/application-workloads/jobs/) | [shenhonglei](https://github.com/shenhonglei) | [623](https://github.com/kubesphere/website/pull/623) |
| [CronJobs](https://kubesphere.io/docs/project-user-guide/application-workloads/cronjob/) | [Kai Zhang](https://github.com/mvpzhangkai) |                                                       |
| [Services](https://kubesphere.io/docs/project-user-guide/application-workloads/services/) | https://github.com/hantmac                    |                                                       |
| [Container Image Settings](https://kubesphere.io/docs/project-user-guide/application-workloads/container-image-settings/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Introduction](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/introduction/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Monitor MySQL](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/get-started/monitor-mysql/) | [Kai Zhang](https://github.com/mvpzhangkai) |                                                       |
| [Monitor Sample Web](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/get-started/monitor-sample-web/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Overview](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/visualization/overview/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Panels](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/visualization/panel/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Querying](https://kubesphere.io/docs/project-user-guide/custom-application-monitoring/visualization/querying/) | [Kai Zhang](https://github.com/mvpzhangkai)   |                                                       |
| [Alerting Policy (Workload Level)](https://kubesphere.io/docs/project-user-guide/alerting/alerting-policy/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Alerting Message (Workload Level)](https://kubesphere.io/docs/project-user-guide/alerting/alerting-message/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [App Templates](https://kubesphere.io/docs/project-user-guide/application/app-template/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Deploy Apps from App Templates](https://kubesphere.io/docs/project-user-guide/application/deploy-app-from-template/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Deploy Apps from App Store](https://kubesphere.io/docs/project-user-guide/application/deploy-app-from-appstore/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [ConfigMaps](https://kubesphere.io/docs/project-user-guide/configuration/configmaps/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Secrets](https://kubesphere.io/docs/project-user-guide/configuration/secrets/) | [Kai Zhang](https://github.com/mvpzhangkai) |                                                       |
| [Image Registries](https://kubesphere.io/docs/project-user-guide/configuration/image-registry/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Grayscale Release Overview](https://kubesphere.io/docs/project-user-guide/grayscale-release/overview/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Blue-green Deployment](https://kubesphere.io/docs/project-user-guide/grayscale-release/blue-green-deployment/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Canary Release](https://kubesphere.io/docs/project-user-guide/grayscale-release/canary-release/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Traffic Mirroring](https://kubesphere.io/docs/project-user-guide/grayscale-release/traffic-mirroring/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |
| [Volume Snapshots](https://kubesphere.io/docs/project-user-guide/storage/volume-snapshots/) | [Kai Zhang](https://github.com/mvpzhangkai)|                                                       |

| DevOps User Guide                                            | Translator | PR Link |
| ------------------------------------------------------------ | ---------- | ------- |
| [Index Page](https://kubesphere.io/docs/devops-user-guide/)  | [Kai Zhang](https://github.com/mvpzhangkai) | [585](https://github.com/kubesphere/website/pull/585) |
| [Credential Management](https://kubesphere.io/docs/devops-user-guide/how-to-use/credential-management/) | [Kai Zhang](https://github.com/mvpzhangkai) | [594](https://github.com/kubesphere/website/pull/594) |
| [Set CI Node for Dependency Cache](https://kubesphere.io/docs/devops-user-guide/how-to-use/set-ci-node/) | [Kai Zhang](https://github.com/mvpzhangkai) | [618](https://github.com/kubesphere/website/pull/618) |
| [Set Email Server for KubeSphere Pipelines](https://kubesphere.io/docs/devops-user-guide/how-to-use/jenkins-email/) | [Kai Zhang](https://github.com/mvpzhangkai) | [620](https://github.com/kubesphere/website/pull/620) |
| [Integrate SonarQube into Pipeline](https://kubesphere.io/docs/devops-user-guide/how-to-integrate/sonarqube/) | [Kai Zhang](https://github.com/mvpzhangkai) | [642](https://github.com/kubesphere/website/pull/642) |
| [Choose Jenkins Agent](https://kubesphere.io/docs/devops-user-guide/how-to-use/choose-jenkins-agent/) | [Kai Zhang](https://github.com/mvpzhangkai) | [668](https://github.com/kubesphere/website/pull/668) |
| [Create a Pipeline Using a Jenkinsfile](https://kubesphere.io/docs/devops-user-guide/how-to-use/create-a-pipeline-using-jenkinsfile/) | [Kai Zhang](https://github.com/mvpzhangkai) | [693](https://github.com/kubesphere/website/pull/693) |
| [DevOps Project Management](https://kubesphere.io/docs/devops-user-guide/how-to-use/devops-project-management/) | [Kai Zhang](https://github.com/mvpzhangkai) | [665](https://github.com/kubesphere/website/pull/665) |
| [Role and Member Management in devops-user-guide](https://kubesphere.io/docs/devops-user-guide/how-to-use/role-and-member-management/) | [Kai Zhang](https://github.com/mvpzhangkai) | [719](https://github.com/kubesphere/website/pull/719) |
| [Jenkins System Settings](https://kubesphere.io/docs/devops-user-guide/how-to-use/jenkins-setting/) | [Kai Zhang](https://github.com/mvpzhangkai) |  [739](https://github.com/kubesphere/website/pull/739) |
| [How to integrate Harbor in Pipeline](https://kubesphere.io/docs/devops-user-guide/how-to-integrate/harbor/) | [Kai Zhang](https://github.com/mvpzhangkai) | [750](https://github.com/kubesphere/website/pull/750) |

| App Store                                                    | Translator                              | PR Link                                               |
| ------------------------------------------------------------ | --------------------------------------- | ----------------------------------------------------- |
| [Index Page](https://kubesphere.io/docs/application-store/)  | [Felixnoo](https://github.com/Felixnoo) | [698](https://github.com/kubesphere/website/pull/698) |
| [Deploy RabbitMQ on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/rabbitmq-app/) |                                         |                                                       |
| [Deploy MongoDB on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/mongodb-app/) |                                         |                                                       |
| [Deploy NGINX on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/nginx-app/) |                                         |                                                       |
| [Deploy Redis on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/redis-app/) |                                         |                                                       |
| [Deploy Tomcat on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/tomcat-app/) |                                         |                                                       |
| [Deploy MySQL on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/mysql-app/) |                                         |                                                       |
| [Deploy etcd on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/etcd-app/) |                                         |                                                       |
| [Deploy Memcached on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/memcached-app/) |                                         |                                                       |
| [Deploy MinIO on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/minio-app/) |                                         |                                                       |
| [Deploy PostgreSQL on KubeSphere](https://kubesphere.io/docs/application-store/built-in-apps/postgresql-app/) |                                         |                                                       |
| [Application Lifecycle Management](https://kubesphere.io/docs/application-store/app-lifecycle-management/) |                                         |                                                       |

| Workspace Administration and User Guide                      | Translator                              | PR Link                                               |
| ------------------------------------------------------------ | --------------------------------------- | ----------------------------------------------------- |
| [Workspace Overview](https://kubesphere.io/docs/workspace-administration/workspace-overview/) | [Felixnoo](https://github.com/Felixnoo) | [707](https://github.com/kubesphere/website/pull/707) |
| [Upload Helm-based Applications](https://kubesphere.io/docs/workspace-administration/upload-helm-based-application/) | [Felixnoo](https://github.com/Felixnoo) | [718](https://github.com/kubesphere/website/pull/718) |
| [Role and Member Management](https://kubesphere.io/docs/workspace-administration/role-and-member-management/) | [Felixnoo](https://github.com/Felixnoo) | [716](https://github.com/kubesphere/website/pull/716) |
| [Import Helm Repository](https://kubesphere.io/docs/workspace-administration/app-repository/import-helm-repository/) | [Felixnoo](https://github.com/Felixnoo) | [728](https://github.com/kubesphere/website/pull/728) |
