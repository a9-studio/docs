---
editable: false
sourcePath: en/_api-ref-grpc/vpc/v1/api-ref/grpc/Network/list.md
---

# Virtual Private Cloud API, gRPC: NetworkService.List

Retrieves the list of Network resources in the specified folder.

## gRPC request

**rpc List ([ListNetworksRequest](#yandex.cloud.vpc.v1.ListNetworksRequest)) returns ([ListNetworksResponse](#yandex.cloud.vpc.v1.ListNetworksResponse))**

## ListNetworksRequest {#yandex.cloud.vpc.v1.ListNetworksRequest}

```json
{
  "folder_id": "string",
  "page_size": "int64",
  "page_token": "string",
  "filter": "string"
}
```

#|
||Field | Description ||
|| folder_id | **string**

Required field. ID of the folder to list networks in.
To get the folder ID, use a [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/grpc/Folder/list#List) request. ||
|| page_size | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `page_size`,
the service returns a [ListNetworksResponse.next_page_token](#yandex.cloud.vpc.v1.ListNetworksResponse)
that can be used to get the next page of results in subsequent list requests. Default value: 100. ||
|| page_token | **string**

Page token. To get the next page of results, set `page_token` to the
[ListNetworksResponse.next_page_token](#yandex.cloud.vpc.v1.ListNetworksResponse) returned by a previous list request. ||
|| filter | **string**

A filter expression that filters resources listed in the response.
The expression must specify:
1. The field name. Currently you can use filtering only on the [Network.name](#yandex.cloud.vpc.v1.Network) field.
2. An `=` operator.
3. The value in double quotes (`"`). Must be 3-63 characters long and match the regular expression `[a-z][-a-z0-9]{1,61}[a-z0-9]`. ||
|#

## ListNetworksResponse {#yandex.cloud.vpc.v1.ListNetworksResponse}

```json
{
  "networks": [
    {
      "id": "string",
      "folder_id": "string",
      "created_at": "google.protobuf.Timestamp",
      "name": "string",
      "description": "string",
      "labels": "string",
      "default_security_group_id": "string"
    }
  ],
  "next_page_token": "string"
}
```

#|
||Field | Description ||
|| networks[] | **[Network](#yandex.cloud.vpc.v1.Network)**

List of Network resources. ||
|| next_page_token | **string**

This token allows you to get the next page of results for list requests. If the number of results
is larger than [ListNetworksRequest.page_size](#yandex.cloud.vpc.v1.ListNetworksRequest), use
the `next_page_token` as the value
for the [ListNetworksRequest.page_token](#yandex.cloud.vpc.v1.ListNetworksRequest) query parameter
in the next list request. Subsequent list requests will have their own
`next_page_token` to continue paging through the results. ||
|#

## Network {#yandex.cloud.vpc.v1.Network}

A Network resource. For more information, see [Networks](/docs/vpc/concepts/network).

#|
||Field | Description ||
|| id | **string**

ID of the network. ||
|| folder_id | **string**

ID of the folder that the network belongs to. ||
|| created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. ||
|| name | **string**

Name of the network.
The name is unique within the folder.
Value must match the regular expression ``\\|[a-zA-Z]([-_a-zA-Z0-9]{0,61}[a-zA-Z0-9])?``. ||
|| description | **string**

Optional description of the network. 0-256 characters long. ||
|| labels | **string**

Resource labels as `key:value` pairs.
No more than 64 per resource.
The maximum string length in characters for each value is 63.
Each value must match the regular expression `[-_0-9a-z]*`.
The string length in characters for each key must be 1-63.
Each key must match the regular expression `[a-z][-_0-9a-z]*`. ||
|| default_security_group_id | **string**

ID of default security group for network. ||
|#