[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/macskay)](https://artifacthub.io/packages/search?repo=macskay)

# Foundry VTT Helm Chart

This repository holds a Dockerfile as well as a helm chart that deploys FoundryVTT to a Kubernetes cluster with or without a persistent volume claim.

## Installing Helm Chart

The Helm Chart is deployed to the Helm Artifactory.
```
 $ helm repo add macskay https://macskay.github.io/helm
 $ helm repo update
```

You can search for all repositoies by using

```
 $ helm search repo macskay
```
