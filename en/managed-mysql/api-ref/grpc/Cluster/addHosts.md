---
editable: false
sourcePath: en/_api-ref-grpc/mdb/mysql/v1/api-ref/grpc/Cluster/addHosts.md
---

# Managed Service for MySQL API, gRPC: ClusterService.AddHosts

Adds new hosts in a cluster.

## gRPC request

**rpc AddHosts ([AddClusterHostsRequest](#yandex.cloud.mdb.mysql.v1.AddClusterHostsRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## AddClusterHostsRequest {#yandex.cloud.mdb.mysql.v1.AddClusterHostsRequest}

```json
{
  "cluster_id": "string",
  "host_specs": [
    {
      "zone_id": "string",
      "subnet_id": "string",
      "assign_public_ip": "bool",
      "replication_source": "string",
      "backup_priority": "int64",
      "priority": "int64"
    }
  ]
}
```

#|
||Field | Description ||
|| cluster_id | **string**

Required field. ID of the cluster to add hosts to.

To get this ID, make a [ClusterService.List](/docs/managed-mysql/api-ref/grpc/Cluster/list#List) request. ||
|| host_specs[] | **[HostSpec](#yandex.cloud.mdb.mysql.v1.HostSpec)**

Configuration of the newly added hosts. ||
|#

## HostSpec {#yandex.cloud.mdb.mysql.v1.HostSpec}

#|
||Field | Description ||
|| zone_id | **string**

ID of the availability zone where the host resides.

To get a list of available zones, make the [yandex.cloud.compute.v1.ZoneService.List](/docs/compute/api-ref/grpc/Zone/list#List) request. ||
|| subnet_id | **string**

ID of the subnet to assign to the host.

This subnet should be a part of the cluster network (the network ID is specified in the [ClusterService.CreateClusterRequest.network_id](/docs/managed-mysql/api-ref/grpc/Cluster/create#yandex.cloud.mdb.mysql.v1.CreateClusterRequest)). ||
|| assign_public_ip | **bool**

Option that enables public IP address for the host so that the host can be accessed from the internet.

After a host has been created, this setting cannot be changed.
To remove an assigned public IP address, or to assign a public IP address to a host without one, recreate the host with the appropriate `assign_public_ip` value set.

Possible values:
* `false` - don't assign a public IP address to the host.
* `true` - assign a public IP address to the host. ||
|| replication_source | **string**

[Host.name](/docs/managed-mysql/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.mysql.v1.Host) of the host to be used as the replication source (for cascading replication). ||
|| backup_priority | **int64**

Host backup priority ||
|| priority | **int64**

Host master promotion priority ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "created_at": "google.protobuf.Timestamp",
  "created_by": "string",
  "modified_at": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": {
    "cluster_id": "string",
    "host_names": [
      "string"
    ]
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": "google.protobuf.Empty"
  // end of the list of possible fields
}
```

An Operation resource. For more information, see [Operation](/docs/api-design-guide/concepts/operation).

#|
||Field | Description ||
|| id | **string**

ID of the operation. ||
|| description | **string**

Description of the operation. 0-256 characters long. ||
|| created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| created_by | **string**

ID of the user or service account who initiated the operation. ||
|| modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[AddClusterHostsMetadata](#yandex.cloud.mdb.mysql.v1.AddClusterHostsMetadata)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|| response | **[google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty)**

The normal response of the operation in case of success.
If the original method returns no data on success, such as Delete,
the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty).
If the original method is the standard Create/Update,
the response should be the target resource of the operation.
Any method that returns a long-running operation should document the response type, if any.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## AddClusterHostsMetadata {#yandex.cloud.mdb.mysql.v1.AddClusterHostsMetadata}

#|
||Field | Description ||
|| cluster_id | **string**

ID of the cluster to which the hosts are being added. ||
|| host_names[] | **string**

Names of hosts that are being added. ||
|#