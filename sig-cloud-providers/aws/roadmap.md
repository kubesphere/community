# Roadmap

Based on the discussion on the [issue#2000](https://github.com/kubesphere/kubesphere/issues/2000), KubeSphere plans to deliver these features in several phases as below:

## Network

- provision CLB/NLB for LoadBalancer Service - **3.0.0**

  Most work is from frontend, including:
  - Adjust UI to recgonize generated domian name from lb，top priority, including lb service creating/editing/enabling router..etc.
  - Add AWS lb annotations to drop down list
- Application Load Balancer Ingress Controller - 3.1.0
- Nginx Ingress Controller - **3.0.0**
  - Test multiple domains + route53
- Service Mesh: istio -  _Already Supported_
- Service Mesh: app mesh - 3.1.0
- Network Policy - Calico - **3.0.0**
- External DNS - Cloud Map 3.1.0

## Storage

- manage EBS CSI provider - **3.0.0**
- manage EFS CSI provider - **3.0.0**
- mange FSx CSI provider - **3.0.0**

## Image Registry

- Support Amazon ECR - 3.1.0

## Security

- IAM Role for Service Account - 3.1.0
  - Provide seperated displaying section for serviceaccount and show the relationship between sa and IRC rols based on annotations, allow users to edit it.
- Federated authentication for IAM users - **3.0.0**
- EKS encryption provider with KMS - **3.0.0**

## Worker Node management

- create/update/upgrade/delete self managed node groups, on-demand instance, spot instance or mixed type - 3.1.0  
- create/update/upgrade/delete managed node group - 3.1.0 
- EKS on Fargate - 3.1.0
- Horizontal Pod Autoscaler - _Already Supported_
- Cluster Autoscaler / Atlasian escalator - 3.1.0
- Vertical Pod Autoscaler - 3.1.0

## Logging/Metric/Tracing/Alerting

- integrate with AWS managed ElaticSearch/Kibana for logging - **3.0.0**
- integrate with Container Insight for monitoring (metrics/logs) - 3.1.0 
- integrate with X-Ray for tracing - 3.1.0
- integrate with CloudWatch alarm for alerting - 3.1.0
- aws-for-fluent-bit - 3.1.0

## CI/CD

- aws native tools: CodePipeline, CodeBuild, CodeDeploy - still under discussion
- Spinnaker - still under discussion
- GitOps: Flux, Flagger, Argo CD - still under discussion

## Multi Cluster Management

- one place to manage multiple clusters - **3.0.0**
- KubeFed - **3.0.0**

## Machine Learning on EKS

- Amazon SageMaker Operators for Kubernetes - 3.1.0
- KubeFlow - 4.0.0

