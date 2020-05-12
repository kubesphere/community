# Observability Special Interest Group

The Observability SIG is to design and implement the observability features for KubeSphere including monitoring, alerting, notification, logging, K8s events management and auditing.

## Projects

- [FluentBit Operator](https://github.com/kubesphere/fluentbit-operator) facilitates the deployment of Fluent Bit and provides great flexibility in building logging layer based on Fluent Bit.
- [Kube-Events](https://github.com/kubesphere/kube-events) K8s Event Exporting, Filtering and Alerting in Multi-Tenant Environment.
- [Kube-Auditing](https://github.com/wanjunlei/kube-auditing) provides one K8s auditing webhook (Kube-Auditing-Webhook), two CRDs (KubeAuditWebhook, KubeAuditRule) and an integrated controller to perform K8s Audit data filtering, storage and alerting. Not open source yet.
- [Notification Manager](https://github.com/kubesphere/notification-manager) provides notification management capability in multi-tenant K8s environment. It receives alerts from Prometheus Alertmanager or other sources, and then sends notification to K8s tenant users via Email, Wechat, Slack and Webhook etc. Every K8s tenant user can define his own notification settings with CRDs like EmailConfig/EmailReceiver, WechatConfig/WechatReceiver, SlackConfig/SlackReceiver etc. This project is still under active development.
- [KubeSphere Monitoring Dashboard](https://github.com/kubesphere/monitoring-dashboard) inspired by Grafana with significant difference in terms of data storage, multi-tenancy and dashboard sharing to fit KubeSphere's context. But it is not a replacement to Grafana. It requires KubeSphere backend and frontend to work. Custom metrics monitoring feature in KubeSphere 3.0 is backed by this project. This repository is aimed at KubeSphere developers who want to understand dashboard data model, storage, template sharing and how to contribute, as the custom monitoring feature is introduced since v3.0.
- [Event Rule Engine](https://github.com/kubesphere/event-rule-engine) is a rule script evaluating engine for KubeSphere event processing. It runs expression evaluation on json data.
- [Prometheus Operator](https://github.com/kubesphere/prometheus-operator) is the customization of Prometheus operator for KubeSphere.
- [kube-prometheus](https://github.com/kubesphere/kube-prometheus) is the customization of kube-prometheus for KubeSphere.
- [Prometheus Monitoring Mixin for Kubernetes](https://github.com/kubesphere/kubernetes-mixin) is the customization of kubernetes-mixin for KubeSphere.
- [Node exporter](https://github.com/kubesphere/node_exporter) is the customization of Node exporter for KubeSphere. 
- [Fluent Bit](https://github.com/kubesphere/fluent-bit) is the customization of Fluent Bit for KubeSphere.

## Documents

- [Concept of KubeSphere Logging](./concepts-and-designs/kubesphere-logging.md)
- [Concept of KubeSphere Monitoring](./concepts-and-designs/kubesphere-monitoring.md)
- [Development Guide of KubeSphere Logging](./development/kubesphere-logging-development-guide.md)
- [Development Guide of KubeSphere Monitoring](./development/kubesphere-monitoring-development-guide.md)

## Members

- Benjamin Huo ([@benjaminhuo](https://github.com/benjaminhuo)), Lead
- Dan Ma ([@Ma-Dan](https://github.com/Ma-Dan)), Member
- Guangzhe Huang ([@huanggze](https://github.com/huanggze)), Member
- Junot Xiang ([@junotx](https://github.com/junotx)), Member
- Wanjun Lei ([@wanjunlei](https://github.com/wanjunlei)), Member

## Meetings

[Meeting notes](https://docs.google.com/document/d/18SOB2NRQWS-Qad4oebzIjtQzUG831PFvQtvN5tBwNrM/)

## Contact

- Slack [#sig-observability](https://kubesphere.slack.com/messages/sig-observability)
