---
editable: false
sourcePath: en/_api-ref-grpc/organizationmanager/v1/api-ref/grpc/OsLogin/createProfile.md
---

# Cloud Organization API, gRPC: OsLoginService.CreateProfile {#CreateProfile}

## gRPC request

**rpc CreateProfile ([CreateOsLoginProfileRequest](#yandex.cloud.organizationmanager.v1.CreateOsLoginProfileRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## CreateOsLoginProfileRequest {#yandex.cloud.organizationmanager.v1.CreateOsLoginProfileRequest}

```json
{
  "organizationId": "string",
  "subjectId": "string",
  "login": "string",
  "uid": "int64",
  "homeDirectory": "string",
  "shell": "string"
}
```

#|
||Field | Description ||
|| organizationId | **string**

Required field.  ||
|| subjectId | **string** ||
|| login | **string**

Required field. must not contain . or end in ~ ||
|| uid | **int64**

1000 - 2^63 - 1 ||
|| homeDirectory | **string** ||
|| shell | **string** ||
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
  "metadata": {
    "osLoginProfileId": "string",
    "organizationId": "string",
    "subjectId": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "id": "string",
    "organizationId": "string",
    "subjectId": "string",
    "login": "string",
    "uid": "int64",
    "isDefault": "bool",
    "homeDirectory": "string",
    "shell": "string"
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
|| metadata | **[CreateOsLoginProfileMetadata](#yandex.cloud.organizationmanager.v1.CreateOsLoginProfileMetadata)**

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
|| response | **[OsLoginProfile](#yandex.cloud.organizationmanager.v1.OsLoginProfile)**

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

## CreateOsLoginProfileMetadata {#yandex.cloud.organizationmanager.v1.CreateOsLoginProfileMetadata}

#|
||Field | Description ||
|| osLoginProfileId | **string** ||
|| organizationId | **string** ||
|| subjectId | **string** ||
|#

## OsLoginProfile {#yandex.cloud.organizationmanager.v1.OsLoginProfile}

#|
||Field | Description ||
|| id | **string** ||
|| organizationId | **string** ||
|| subjectId | **string** ||
|| login | **string** ||
|| uid | **int64** ||
|| isDefault | **bool** ||
|| homeDirectory | **string** ||
|| shell | **string** ||
|#