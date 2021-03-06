# Helm chart for Crowi

## Installing the Chart

To install the chart with the release name `crowi`:

```bash
$ git clone git@github.com:lightnet328/helm-crowi.git
$ cd helm-crowi
$ helm dep build
$ helm inspect values . > crowi.yaml
# Edit the values files
$ vim crowi.yaml
$ helm install --name crowi --values crowi.yaml .
```

## Uninstalling the Chart

To uninstall/delete the `crowi` deployment:

```bash
$ helm delete crowi
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the Crowi chart and their default values.

| Parameter                             | Description                                         | Default                                                              |
| ------------------------------------- | --------------------------------------------------- | -------------------------------------------------------------------- |
| `image.registry`                      | Crowi image registry                                | `docker.io`                                                          |
| `image.repository`                    | Crowi Image name                                    | `crowi/crowi`                                                   |
| `image.tag`                           | Crowi Image tag                                     | `1.7.0`                                                              |
| `image.pullPolicy`                    | Image pull policy                                   | `IfNotPresent`                                                       |
| `service.type`                        | Kubernetes Service type                             | `ClusterIP`                                                          |
| `service.port`                        | Kubernetes Service port                             | `3000`                                                               |
| `persistence.enabled`                 | Use a PVC to persist data                           | `false`                                                              |
| `persistence.accessMode`              | Use volume as ReadOnly or ReadWrite                 | `ReadWriteOnce`                                                      |
| `persistence.storageClass`            | Storage class of backing PVC                        | `nil`                                                                |
| `persistence.size`                    | Size of data volume                                 | `8Gi`                                                               |
| `mongodb.enabled`                     | Enable mongodb                                      | `true`                                                               |
| `redis.enabled`                       | Enable redis                                        | `true`                                                               |
| `elasticsearch.enabled`               | Enable elasticsearch                                | `true`                                                               |
| `elasticsearch.serviceAccountName`    | Kubernetes service account                          | `elasticsearch`                                                      |
| `elasticsearch.serviceAccount.create` | Create service account                              | `true`                                                               |
| `elasticsearch.rbac.create`           | If true, create & use RBAC resources                | `true`                                                               |
| `elasticsearch.plugins`               | Elasticsearch node plugins                          | `analysis-kuromoji` |
| `elasticsearch.data.replicas`         | Desired number of Elasticsearch data eligible nodes | `3`                                                                  |
