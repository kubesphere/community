## Expose Pipiline metrics to Prometheus

​	In order to have a more intuitive statistically view about pipelines. we may need to collect some metrics about pipelines, and then expose an endpoint with metrics where a Prometheus Server can scrape.

​    Now we recommend using  [Jenkins Prometheus Plugin](https://github.com/jenkinsci/prometheus-plugin) to expose metrics about pipelines, and currently, it only contains metrics from the [Metrics-plugin](https://github.com/jenkinsci/metrics-plugin) and summary of build duration of jobs and pipeline stages.

Lots of metrics exposed by Prometheus Plugin are jenkins system metrics, and I picked-up some metrics which useful for kubesphere below. KubeSphere client gets metrics via the select label, for example, want to get pipelines metrics should select label matches with pipeline name. Metrics below describes the statistical information about pipelines and jobs, at the view of kubesphere, it describes the pipelines in DevOps Project, and now the metrics about pipelines have no direct relationship with Jenkins Folder(KubeSphere DevOps Project), in other words, have no metrics about KubeSphere DevOps Project, so if we want the KubeSphere DevOps Project metrics, we must get the metrics about all the pipelines in the KubeSphere DevOps project and do some calculations.
| Metrics                                                      | Type      | Description                                           | Note |
| ------------------------------------------------------------ | --------- | ----------------------------------------------------- | ---- |
| `jenkins_builds_duration_milliseconds_summary`               | `summary` | Summary of Jenkins build times in milliseconds by Job | ms   |
| `jenkins_builds_success_build_count`                         | `counter` | Successful build count                                |      |
| `jenkins_builds_failed_build_count`                          | `counter` | Failed build count                                    |      |
| `jenkins_builds_last_build_result`                           | `gauge`   | Build status of a job as a boolean                    |      |
| `jenkins_builds_last_build_duration_milliseconds`            | `gauge`   | Build times in milliseconds of last build             | ms   |
| `jenkins_builds_last_build_start_time_milliseconds`          | `gauge`   | Last build start timestamp in milliseconds            | ms   |
| `kubesphere_jenkins_builds_stage_duration_milliseconds_summary` | `summary` | Summary of Jenkins build times by Job and Stage       | ms   |
| `jenkins_builds_last_build_result_ordinal`                   | ``        |                                                       |      |

more info please to see **https://github.com/jenkinsci/metrics-plugin#metrics-plugin-for-jenkins**
