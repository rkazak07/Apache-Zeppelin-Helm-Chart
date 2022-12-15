# Zeppelin

Zeppelin is a web based notebook for interactive data analytics with Spark, SQL and Scala.


# Hadoop

The Hadoop chart can be used to create a YARN cluster where Spark jobs are executed.

* For Hadoop helm installations, visit  [Hadoop][1] 


### Quick Installation

This chart requires the following charts before install Zeppelin
* [Hadoop][1]

> Create Namespace
```
$ kubectl create ns hadoop-cls
```

### Deploy Chart

```
$ helm install my-release . -f values.yaml -n hadoop-cls
```

### Upgrade Chart

```
$ helm upgrade  --install my-release . -f values.yaml -n hadoop-cls
```

### Delete Chart

```
$ helm delete -n hadoop-cls my-release
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
| `hadoop.configPath`                    | 	Path in the Zeppelin image where the Hadoop config is mounted   | `/usr/hadoop-3.3.4/etc/hadoop`    |
| `ingress.enabled`                      | Enable ingress                                                  | `false`                                                               |
| `ingress.annotations`                  | Ingress annotations                                                 | `{}`                                                               |
| `ingress.hosts`                        | Ingress Hostnames                                                 | `["zeppelin.local"]`    |
| `ingress.path`                         | Path within the URL structure                                      | `/`                                                            |
| `ingress.tls`                          | Ingress TLS configuration                                          | `[]`                                                               |
| `nodeSelecor`                          | 	Node selector for the Zeppelin deployment                        | `{}`    |


---


## Referances

- Chart can use the hadoop config for the hadoop cluster and use the YARN executor: https://github.com/kubernetes/charts/tree/master/stable/zeppelin

[1]: https://github.com/rkazak07/Hadoop-Helm-chart
