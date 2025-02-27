#### Quotas {#serverless-containers-quotas}

Type of limit | Value
----- | -----
Number of containers per cloud | 10
Number of [triggers](../../serverless-containers/concepts/trigger/) per cloud | 100
Total volume of Docker images used in active container revisions | 20 GB
Number of container instances per availability zone | 10
Number of concurrent requests to containers per availability zone | 10
Total RAM for all running container instances per availability zone | 20 GB
Total number of CPUs of all running container instances per availability zone | 10
Number of [provisioned container instances](../../serverless-containers/concepts/container.md#provisioned-instances) per cloud | 2
Number of [user networks](../../serverless-containers/concepts/networking.md##user-network) per cloud | 1

#### Limits {#serverless-containers-limits}

Type of limit | Value
----- | -----
Maximum size of the container image | 10 GB
Maximum RAM per container instance | 8 GB
Maximum size of an HTTP request to the container, including HTTP headers and the request body | 3.5 MB
Maximum size of the container HTTP response, including HTTP headers and the response body | 3.5 MB
Maximum size of temporary files | 512 MB
Maximum time for request processing by the container before timeout, including the first launch initialization^1^ | 1 hour
Maximum total environment variable storage, including variable names^2^ | 4 KB
Maximum number of triggers per [message queue](../../message-queue/concepts/queue.md) | 1
Maximum message size per trigger | 256 KB

^1^ A timeout of over 10 minutes is only available for [long-lived containers](../../serverless-containers/concepts/long-lived-containers.md).
^2^ {{ lockbox-short-name }} secrets are provided via environment variables and are also counted towards this limit.
