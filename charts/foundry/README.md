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

#### Configuration

|Parmater|Description|Default Value|
|------|-------|-|
|app.name|Name for all Kubernetes Configs|`foundry`|
|persistence.enabled|Use persistent storage|`false`|
|persistence.storageClassName|Type of PVC|`default`|
|persistence.size|Size of PVC|`2Gi`|
|persistence.claim.name|Name of PVC|`data-pvc-foundry`|
|persistence.claim.existing|If true, creation is skipped|`false`|
|ingress.enabled|Use ingress|`false`|
|ingress.hosts|List of all valid URLs|[`www.example.com`]|
|ingress.className|Ingress class name|`nginx`|
|forceSslRedirect|Always Redirect to HTTPS|`false`|
|ssl.enabled|Enable SSL Ingress|`false`|
|ssl.clusterIssuer.enabled|Enable Cluster Issuer|`false`|
|ssl.clusterIssuer.name|Name of Cluster Issuer|`letsencrypt`|
|image.name|Image to use for Deployment|`macskay/foundry`|
|image.tag|Tag to use for Deployment|`latest`|
|image.pullSecret|K8s Secret to Use for pulling Images|`""`|
|conatainer.port|Port to expose in Service|`30000`|


## Manual Setup

### Building Docker Image Manually

For the Docker Image to build you need to log in to your Foundry VTT and generate a "Timed URL" for Linux. Inject the URL into the Dockerfile (Beware the link is only valid for a couple of minutes) via variable `TOKEN_URL` while building as shown below

Example:
```
 $ docker build -t foundry:stable --build_args TOKEN_URL <insert_url>
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
