# Zeppelin Helm Chart
-------------------------------------------------------------------------------------------------------

Zeppelin is a web based notebook for interactive data analytics with Spark, SQL and Scala.

-------------------------------------------------------------------------------------------------------

# Installation

```
$ kubectl create ns hadoop-cls
```

```
$ helm install zeppelin . -f values.yaml -n hadoop-cls
```

# Upgrade


```
$ helm upgrade  --install zeppelin . -f values.yaml -n hadoop-cls
```

## Related charts

-------------------------------------------------------------------------------------------------------

The Hadoop chart can be used to create a YARN cluster where Spark jobs are executed:

-------------------------------------------------------------------------------------------------------
## Hadoop installation

https://github.com/rkazak07/hadoop-kubernetes-deploy.git


```
$ helm install hadoop-cluster . -f values.yaml -n hadoop-cls
```
```
$ helm install --set hadoop.useConfigMap=true,hadoop.configMapName=hadoop-hadoop stable/zeppelin
```


## Configuration

The following table lists the configurable parameters of the Hadoop chart and their default values.

| Parameter                              | Description                                                      | Default                                                           |
| -------------------------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------------- |
| `zeppelin.image`                       | Zeppelin image                                                   | `apache/zeppelin:0.10.1`                                       
| `zeppelin.resources`                   | Resource limits and requests                                     | `limits.memory=4096Mi,limits.cpu=2000m`                                                           |
| `spark.driverMemory`                   | Memory used by Spark driver (Java notation)                      | `1g`
| `spark.executorMemory`                 | Memory used by Spark executors (Javanotation)                           | `1g`                                                            |
| `spark.numExecutors`                   |Number of Spark executors                                        | `2`
| `hadoop.useConfigMap`                  | Use external Hadoop configuration for Spark executors                                         | `false`                                                               |
| `hadoop.configPath`                    | 	Path in the Zeppelin image where the Hadoop config is mounted   | `/usr/hadoop-3.3.3/etc/hadoop`    |
| `ingress.enabled`                      | Enable ingress                                                  | `false`                                                               |
| `ingress.annotations`                  | Ingress annotations                                                 | `{}`                                                               |
| `ingress.hosts`                        | Ingress Hostnames                                                 | `["zeppelin.local"]`    |
| `ingress.path`                         | Path within the URL structure                                      | `/`                                                            |
| `ingress.tls`                          | Ingress TLS configuration                                          | `[]`                                                               |
| `nodeSelecor`                          | 	Node selector for the Zeppelin deployment                        | `{}`    |


---


## Referances

- Chart can use the hadoop config for the hadoop cluster and use the YARN executor: https://github.com/kubernetes/charts/tree/master/stable/zeppelin
