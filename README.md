# Techzone Deployer Cloud Pak for Integration pipelines

This repository contains a set of Tekton pipelines to deploy Cloud Pak for Integration into an IBM Technology Zone `deployer` cluster.

## Pre-requisites

An IBM Technology Zone `deployer` cluster is assumed to be configured with an appropriate Red Hat OpenShift version for the Cloud Pak for Integration version you wish to deploy, with appropriate sizing. Refer to [IBM Cloud Pak for Integration documentation](https://www.ibm.com/docs/en/cloud-paks/cp-integration/2022.4) for more information.

A `deployer` cluster is configured with the following items:

- ExternalSecrets operator deployed with a ClusterSecretStore configured. The remote ExternalSecrets secret store must include an IBM Entitlement Key.
- Techzone Deployer Tekton tasks deployed ([deploy YAML](https://github.com/cloud-native-toolkit/deployer-tekton-tasks/blob/main/argocd.yaml)).
- OpenShift GitOps configured with [One Touch Provisioning ArgoCD instance](https://github.com/one-touch-provisioning/otp-gitops), and any relevant RBAC rules.
- OpenShift Pipelines operator deployed.

## Repository organisation

There are two versions 2022.4 and 2023.2. At any one time, only the latest version of Cloud Pak for Integration is worked on and supported on a best-effort basis.

## Deploy

The pipeline to deploy Cloud Pak for Integration 2023.2 deploys the platform UI and all Cloud Pak for Integration operators and catalog sources. The responsibility to deploy the actual instances depends on you as the cluster operator, as individual products have their own installation processes.

To deploy the pipeline, run 

```
oc apply -f 2023.2/pipeline.yaml
oc apply -f 2023.2/pipelinerun.yaml
```
