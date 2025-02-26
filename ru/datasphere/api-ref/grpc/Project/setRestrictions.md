---
editable: false
sourcePath: en/_api-ref-grpc/datasphere/v2/api-ref/grpc/Project/setRestrictions.md
---

# DataSphere API v2, gRPC: ProjectService.SetRestrictions {#SetRestrictions}

Set project restrictions.

## gRPC request

**rpc SetRestrictions ([SetProjectRestrictionsRequest](#yandex.cloud.datasphere.v2.SetProjectRestrictionsRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## SetProjectRestrictionsRequest {#yandex.cloud.datasphere.v2.SetProjectRestrictionsRequest}

```json
{
  "projectId": "string",
  "restrictions": [
    {
      "name": "string",
      "boolValue": [
        "bool"
      ],
      "longValue": [
        "int64"
      ],
      "stringValue": [
        "string"
      ]
    }
  ]
}
```

#|
||Field | Description ||
|| projectId | **string**

Required field. ID of the project. ||
|| restrictions[] | **[Restriction](#yandex.cloud.datasphere.v2.Restriction)**

List of restrictions to set. ||
|#

## Restriction {#yandex.cloud.datasphere.v2.Restriction}

#|
||Field | Description ||
|| name | **string**

Name of restriction. ||
|| boolValue[] | **bool**

List of boolean restriction values. Empty if value type is not boolean. ||
|| longValue[] | **int64**

List of long restriction values. Empty if value type is not long. ||
|| stringValue[] | **string**

List of string restriction values. Empty if value type is not string. ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "createdAt": "google.protobuf.Timestamp",
  "createdBy": "string",
  "modifiedAt": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": "google.protobuf.Any",
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "restrictions": [
      {
        "name": "string",
        "boolValue": [
          "bool"
        ],
        "longValue": [
          "int64"
        ],
        "stringValue": [
          "string"
        ]
      }
    ]
  }
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
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| createdBy | **string**

ID of the user or service account who initiated the operation. ||
|| modifiedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[google.protobuf.Any](https://developers.google.com/protocol-buffers/docs/proto3#any)**

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
|| response | **[RestrictionsResponse](#yandex.cloud.datasphere.v2.RestrictionsResponse)**

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

## RestrictionsResponse {#yandex.cloud.datasphere.v2.RestrictionsResponse}

#|
||Field | Description ||
|| restrictions[] | **[Restriction](#yandex.cloud.datasphere.v2.Restriction2)**

List of restrictions. ||
|#

## Restriction {#yandex.cloud.datasphere.v2.Restriction2}

#|
||Field | Description ||
|| name | **string**

Name of restriction. ||
|| boolValue[] | **bool**

List of boolean restriction values. Empty if value type is not boolean. ||
|| longValue[] | **int64**

List of long restriction values. Empty if value type is not long. ||
|| stringValue[] | **string**

List of string restriction values. Empty if value type is not string. ||
|#