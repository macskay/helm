[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/foundry)](https://artifacthub.io/packages/search?repo=foundry)

# Foundry VTT Helm Chart

This repository holds a Dockerfile as well as a helm chart that deploys FoundryVTT to a Kubernetes cluster with or without a persistent volume claim.

## Installing Helm Chart

### Adding macskay repo

The Helm Chart is deployed to the Helm Artifactory.
```
 $ helm repo add macskay https://macskay.github.io/helm/
 $ helm repo update 
```

### Installing Foundry
```
 $ helm upgrade --install -i foundry macskay/foundry
```

## Manual Setup

### Building Docker Image Manually

For the Docker Image to build you need to log in to your Foundry VTT and generate a "Timed URL" for Linux. Insert the URL into the Dockerfile (Beware the link is only valid for a couple of minutes) and run

```
 $ docker build -t foundry:latest
```

Optionally also run a tag for your version for example:
```
 $ docker tag foundry:latest foundry:v9-269
```
You can then push this into your registry.

### Running in Docker

You can run the Hosted Docker Image before deploying it to your Kubernetes by invoking:

```
 $ docker run -p 30000:30000 macskay/foundry:latest
```
