---
editable: false
sourcePath: en/_api-ref-grpc/compute/v1/api-ref/grpc/HostGroup/list.md
---

# Compute Cloud API, gRPC: HostGroupService.List {#List}

Retrieves the list of host groups in the specified folder.

## gRPC request

**rpc List ([ListHostGroupsRequest](#yandex.cloud.compute.v1.ListHostGroupsRequest)) returns ([ListHostGroupsResponse](#yandex.cloud.compute.v1.ListHostGroupsResponse))**

## ListHostGroupsRequest {#yandex.cloud.compute.v1.ListHostGroupsRequest}

```json
{
  "folderId": "string",
  "pageSize": "int64",
  "pageToken": "string",
  "filter": "string",
  "orderBy": "string"
}
```

#|
||Field | Description ||
|| folderId | **string**

Required field. ID of the folder to list host groups in.
To get the folder ID, use [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/grpc/Folder/list#List) request. ||
|| pageSize | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `pageSize`,
the service returns a [ListHostGroupsResponse.nextPageToken](#yandex.cloud.compute.v1.ListHostGroupsResponse)
that can be used to get the next page of results in subsequent list requests. ||
|| pageToken | **string**

Page token. To get the next page of results,
set `pageToken` to the [ListHostGroupsResponse.nextPageToken](#yandex.cloud.compute.v1.ListHostGroupsResponse)
returned by a previous list request. ||
|| filter | **string**

A filter expression that filters resources listed in the response.
The expression consists of one or more conditions united by `AND` operator: `<condition1> [AND <condition2> [<...> AND <conditionN>]]`.

Each condition has the form `<field> <operator> <value>`, where:
1. `<field>` is the field name. Currently you can use filtering only on the limited number of fields.
2. `<operator>` is a logical operator, one of `=`, `!=`, `IN`, `NOT IN`.
3. `<value>` represents a value.
String values should be written in double (`"`) or single (`'`) quotes. C-style escape sequences are supported (`\"` turns to `"`, `\'` to `'`, `\\` to backslash). ||
|| orderBy | **string**

By which column the listing should be ordered and in which direction,
format is "createdAt desc". "id asc" if omitted.
The default sorting order is ascending ||
|#

## ListHostGroupsResponse {#yandex.cloud.compute.v1.ListHostGroupsResponse}

```json
{
  "hostGroups": [
    {
      "id": "string",
      "folderId": "string",
      "createdAt": "google.protobuf.Timestamp",
      "name": "string",
      "description": "string",
      "labels": "string",
      "zoneId": "string",
      "status": "Status",
      "typeId": "string",
      "maintenancePolicy": "MaintenancePolicy",
      "scalePolicy": {
        // Includes only one of the fields `fixedScale`
        "fixedScale": {
          "size": "int64"
        }
        // end of the list of possible fields
      }
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| hostGroups[] | **[HostGroup](#yandex.cloud.compute.v1.HostGroup)**

Lists host groups for the specified folder. ||
|| nextPageToken | **string**

This token allows you to get the next page of results for list requests. If the number of results
is larger than [ListHostGroupsRequest.pageSize](#yandex.cloud.compute.v1.ListHostGroupsRequest), use
`nextPageToken` as the value
for the [ListHostGroupsRequest.pageToken](#yandex.cloud.compute.v1.ListHostGroupsRequest) query parameter
in the next list request. Each subsequent list request will have its own
`nextPageToken` to continue paging through the results. ||
|#

## HostGroup {#yandex.cloud.compute.v1.HostGroup}

Represents group of dedicated hosts

#|
||Field | Description ||
|| id | **string**

ID of the group. ||
|| folderId | **string**

ID of the folder that the group belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. ||
|| name | **string**

Name of the group. The name is unique within the folder. ||
|| description | **string**

Description of the group. ||
|| labels | **string**

Resource labels as `key:value` pairs. ||
|| zoneId | **string**

Availability zone where all dedicated hosts are allocated. ||
|| status | enum **Status**

Status of the group.

- `STATUS_UNSPECIFIED`
- `CREATING`
- `READY`
- `UPDATING`
- `DELETING` ||
|| typeId | **string**

ID of host type. Resources provided by each host of the group. ||
|| maintenancePolicy | enum **MaintenancePolicy**

Behaviour on maintenance events.

- `MAINTENANCE_POLICY_UNSPECIFIED`
- `RESTART`: Restart instance to move it to another host during maintenance
- `MIGRATE`: Use live migration to move instance to another host during maintenance ||
|| scalePolicy | **[ScalePolicy](#yandex.cloud.compute.v1.ScalePolicy)**

Scale policy. Only fixed number of hosts are supported at this moment. ||
|#

## ScalePolicy {#yandex.cloud.compute.v1.ScalePolicy}

#|
||Field | Description ||
|| fixedScale | **[FixedScale](#yandex.cloud.compute.v1.ScalePolicy.FixedScale)**

Includes only one of the fields `fixedScale`. ||
|#

## FixedScale {#yandex.cloud.compute.v1.ScalePolicy.FixedScale}

#|
||Field | Description ||
|| size | **int64** ||
|#