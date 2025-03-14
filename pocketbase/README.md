# Pocketbase
This is an unofficial helm chart for running Pocketbase on K8s with Helm.

## Installation

You can install pocketbase on K8S by running the command:

```
helm repo add techwolf12 https://helm.techwolf12.nl/
helm repo update
helm upgrade pocketbase techwolf12/pocketbase --version 0.25.9 --install
```

## Run tests

You can run pocketbase tests by running the command:

`helm test pocketbase`

## Parameters

### PocketBase configuration

| Name                                            | Description                                                                                                                                           | Value                                         |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| `replicaCount`                                  | How many replicas of pocketbase should be deployed, it is ignored if autoscaling is enabled                                                           | `1`                                           |
| `nameOverride`                                  | String to partially override the deployment name (will maintain the release name)                                                                     | `""`                                          |
| `fullnameOverride`                              | String to fully override the deployment name                                                                                                          | `pocketbase`                                  |
| `flags.encryptionEnv`                           | The PB_ENCRYPTION_KEY 32 characters string, see https://pocketbase.io/docs/going-to-production/#:~:text=enable%20settings%20encryption for more infos | `""`                                          |
| `image.repository`                              | The repository (and image name) where the pocketbase docker image is stored                                                                           | `rg.fr-par.scw.cloud/sepropriodev/pocketbase` |
| `image.pullPolicy`                              | Deployment pull policy                                                                                                                                | `IfNotPresent`                                |
| `image.tag`                                     | Overrides the image tag whose default is the chart appVersion                                                                                         | `""`                                          |
| `persistence.storage`                           | How much storage space should be reserved for PocketBase                                                                                              | `2Gi`                                         |
| `persistence.storageClass`                      | The PV storage class (a storageClass with Retain policy is recommended)                                                                               | `""`                                          |
| `ingress.enabled`                               | Whether to enable the ingress                                                                                                                         | `false`                                       |
| `ingress.clusterIssuer`                         | The Cert Manager cluster issuer (https://cert-manager.io/docs/configuration/acme/http01/)                                                             | `letsencrypt-prod`                            |
| `ingress.dns`                                   | The dns name which will expose PocketBase                                                                                                             | `""`                                          |
| `resources`                                     | The resources associated with the deployment                                                                                                          | `{}`                                          |
| `autoscaling.enabled`                           | Whether to enable autoscaling                                                                                                                         | `false`                                       |
| `autoscaling.minReplicas`                       | number of min replicas                                                                                                                                | `1`                                           |
| `autoscaling.maxReplicas`                       | number of max replicas                                                                                                                                | `10`                                          |
| `autoscaling.targetCPUUtilizationPercentage`    | targetCPUUtilizationPercentage                                                                                                                        | `80`                                          |
| `autoscaling.targetMemoryUtilizationPercentage` | targetMemoryUtilizationPercentage                                                                                                                     | `80`                                          |


## Upgrading

Please always make backups before upgrading.

```
helm upgrade pocketbase techwolf12/pocketbase --version 0.25.9 --install
```