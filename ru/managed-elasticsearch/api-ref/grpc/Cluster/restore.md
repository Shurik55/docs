---
editable: false
sourcePath: en/_api-ref-grpc/mdb/elasticsearch/v1/api-ref/grpc/Cluster/restore.md
---

# Managed Service for Elasticsearch API, gRPC: ClusterService.Restore {#Restore}

Creates a new ElasticSearch cluster from the specified backup.

## gRPC request

**rpc Restore ([RestoreClusterRequest](#yandex.cloud.mdb.elasticsearch.v1.RestoreClusterRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## RestoreClusterRequest {#yandex.cloud.mdb.elasticsearch.v1.RestoreClusterRequest}

```json
{
  "backupId": "string",
  "name": "string",
  "description": "string",
  "labels": "string",
  "environment": "Environment",
  "configSpec": {
    "version": "string",
    "elasticsearchSpec": {
      "dataNode": {
        // Includes only one of the fields `elasticsearchConfig_7`
        "elasticsearchConfig_7": {
          "maxClauseCount": "google.protobuf.Int64Value",
          "fielddataCacheSize": "string",
          "reindexRemoteWhitelist": "string",
          "reindexSslCaPath": "string"
        },
        // end of the list of possible fields
        "resources": {
          "resourcePresetId": "string",
          "diskSize": "int64",
          "diskTypeId": "string"
        }
      },
      "masterNode": {
        "resources": {
          "resourcePresetId": "string",
          "diskSize": "int64",
          "diskTypeId": "string"
        }
      },
      "plugins": [
        "string"
      ]
    },
    "edition": "string",
    "adminPassword": "string"
  },
  "hostSpecs": [
    {
      "zoneId": "string",
      "subnetId": "string",
      "assignPublicIp": "bool",
      "type": "Type",
      "shardName": "string"
    }
  ],
  "networkId": "string",
  "securityGroupIds": [
    "string"
  ],
  "serviceAccountId": "string",
  "deletionProtection": "bool",
  "folderId": "string",
  "extensionSpecs": [
    {
      "name": "string",
      "uri": "string",
      "disabled": "bool"
    }
  ]
}
```

#|
||Field | Description ||
|| backupId | **string**

Required field. Required. ID of the backup to restore from. ||
|| name | **string**

Required field. Name of the ElasticSearch cluster. The name must be unique within the folder. ||
|| description | **string**

Description of the ElasticSearch cluster. ||
|| labels | **string**

Custom labels for the ElasticSearch cluster as `` key:value `` pairs. Maximum 64 per resource.
For example, "project": "mvp" or "source": "dictionary". ||
|| environment | enum **Environment**

Deployment environment of the ElasticSearch cluster.

- `ENVIRONMENT_UNSPECIFIED`
- `PRODUCTION`: Stable environment with a conservative update policy when only hotfixes are applied during regular maintenance.
- `PRESTABLE`: Environment with a more aggressive update policy when new versions are rolled out irrespective of backward compatibility. ||
|| configSpec | **[ConfigSpec](#yandex.cloud.mdb.elasticsearch.v1.ConfigSpec)**

Required field. Configuration and resources for hosts that should be created for the ElasticSearch cluster. ||
|| hostSpecs[] | **[HostSpec](#yandex.cloud.mdb.elasticsearch.v1.HostSpec)**

Required. Configuration of ElasticSearch hosts. ||
|| networkId | **string**

Required field. ID of the network to create the cluster in. ||
|| securityGroupIds[] | **string**

User security groups ||
|| serviceAccountId | **string**

ID of the service account used for access to Object Storage. ||
|| deletionProtection | **bool**

Deletion Protection inhibits deletion of the cluster ||
|| folderId | **string**

Required field. ID of the folder to create the ElasticSearch cluster in. ||
|| extensionSpecs[] | **[ExtensionSpec](#yandex.cloud.mdb.elasticsearch.v1.ExtensionSpec)**

optional ||
|#

## ConfigSpec {#yandex.cloud.mdb.elasticsearch.v1.ConfigSpec}

#|
||Field | Description ||
|| version | **string**

Elasticsearch version. ||
|| elasticsearchSpec | **[ElasticsearchSpec](#yandex.cloud.mdb.elasticsearch.v1.ElasticsearchSpec)**

Configuration and resource allocation for Elasticsearch nodes. ||
|| edition | **string**

ElasticSearch edition. ||
|| adminPassword | **string**

Required field. ElasticSearch admin password. ||
|#

## ElasticsearchSpec {#yandex.cloud.mdb.elasticsearch.v1.ElasticsearchSpec}

#|
||Field | Description ||
|| dataNode | **[DataNode](#yandex.cloud.mdb.elasticsearch.v1.ElasticsearchSpec.DataNode)**

Configuration and resource allocation for Elasticsearch data nodes. ||
|| masterNode | **[MasterNode](#yandex.cloud.mdb.elasticsearch.v1.ElasticsearchSpec.MasterNode)**

Configuration and resource allocation for Elasticsearch master nodes. ||
|| plugins[] | **string**

Cluster wide plugins ||
|#

## DataNode {#yandex.cloud.mdb.elasticsearch.v1.ElasticsearchSpec.DataNode}

#|
||Field | Description ||
|| elasticsearchConfig_7 | **[ElasticsearchConfig7](#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfig7)**

Includes only one of the fields `elasticsearchConfig_7`.

Elasticsearch data node configuration. ||
|| resources | **[Resources](#yandex.cloud.mdb.elasticsearch.v1.Resources)**

Resources allocated to Elasticsearch data nodes. ||
|#

## ElasticsearchConfig7 {#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfig7}

Elasticsearch 7.x supported configuration options are listed here.

Detailed description for each set of options is available in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html).

Any options that are not listed here are not supported.

#|
||Field | Description ||
|| maxClauseCount | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum number of clauses a boolean query can contain.

The limit is in place to prevent searches from becoming too large and taking up too much CPU and memory.
It affects not only Elasticsearch's `bool` query, but many other queries that are implicitly converted to `bool` query by Elastcsearch.

Default value: `1024`.

See in-depth description in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-settings.html). ||
|| fielddataCacheSize | **string**

The maximum percentage or absolute value (10%, 512mb) of heap space that is allocated to field data cache.

All the field values that are placed in this cache, get loaded to memory in order to provide fast document based access to those values.
Building the field data cache for a field can be an expensive operations, so its recommended to have enough memory for this cache, and to keep it loaded.

Default value: unbounded.

See in-depth description in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-fielddata.html). ||
|| reindexRemoteWhitelist | **string**

Remote hosts for reindex have to be explicitly allowed in elasticsearch.yml using the reindex.remote.whitelist property.
It can be set to a comma delimited list of allowed remote host and port combinations.
Scheme is ignored, only the host and port are used. ||
|| reindexSslCaPath | **string**

List of paths to PEM encoded certificate files that should be trusted.

See in-depth description in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-reindex.html#reindex-ssl) ||
|#

## Resources {#yandex.cloud.mdb.elasticsearch.v1.Resources}

Computational resources.

#|
||Field | Description ||
|| resourcePresetId | **string**

ID of the preset for computational resources available to a host (CPU, memory etc.).
All available presets are listed in the [documentation](/docs/managed-elasticsearch/concepts/instance-types). ||
|| diskSize | **int64**

Volume of the storage available to a host, in bytes. ||
|| diskTypeId | **string**

Type of the storage environment for the host.
All available types are listed in the [documentation](/docs/managed-elasticsearch/concepts/storage). ||
|#

## MasterNode {#yandex.cloud.mdb.elasticsearch.v1.ElasticsearchSpec.MasterNode}

#|
||Field | Description ||
|| resources | **[Resources](#yandex.cloud.mdb.elasticsearch.v1.Resources)**

Resources allocated to Elasticsearch master nodes. ||
|#

## HostSpec {#yandex.cloud.mdb.elasticsearch.v1.HostSpec}

#|
||Field | Description ||
|| zoneId | **string**

ID of the availability zone where the host resides. ||
|| subnetId | **string**

ID of the subnet the host resides in. ||
|| assignPublicIp | **bool**

The flag that defines whether a public IP address is assigned to the host.

If the value is `true`, then this host is available on the Internet via it's public IP address. ||
|| type | enum **Type**

Required field. Host type.

- `TYPE_UNSPECIFIED`: Host type is unspecified. Default value.
- `DATA_NODE`: The host is an Elasticsearch data node.
- `MASTER_NODE`: The host is an Elasticsearch master node. ||
|| shardName | **string**

The shard name to create on the host. ||
|#

## ExtensionSpec {#yandex.cloud.mdb.elasticsearch.v1.ExtensionSpec}

#|
||Field | Description ||
|| name | **string**

Required field. Name of the extension. ||
|| uri | **string**

URI of the zip archive to create the new extension from. Currently only supports links that are stored in Object Storage. ||
|| disabled | **bool**

The flag shows whether to create the extension in disabled state. ||
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
    "clusterId": "string",
    "backupId": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "id": "string",
    "folderId": "string",
    "createdAt": "google.protobuf.Timestamp",
    "name": "string",
    "description": "string",
    "labels": "string",
    "environment": "Environment",
    "monitoring": [
      {
        "name": "string",
        "description": "string",
        "link": "string"
      }
    ],
    "config": {
      "version": "string",
      "elasticsearch": {
        "dataNode": {
          // Includes only one of the fields `elasticsearchConfigSet_7`
          "elasticsearchConfigSet_7": {
            "effectiveConfig": {
              "maxClauseCount": "google.protobuf.Int64Value",
              "fielddataCacheSize": "string",
              "reindexRemoteWhitelist": "string",
              "reindexSslCaPath": "string"
            },
            "userConfig": {
              "maxClauseCount": "google.protobuf.Int64Value",
              "fielddataCacheSize": "string",
              "reindexRemoteWhitelist": "string",
              "reindexSslCaPath": "string"
            },
            "defaultConfig": {
              "maxClauseCount": "google.protobuf.Int64Value",
              "fielddataCacheSize": "string",
              "reindexRemoteWhitelist": "string",
              "reindexSslCaPath": "string"
            }
          },
          // end of the list of possible fields
          "resources": {
            "resourcePresetId": "string",
            "diskSize": "int64",
            "diskTypeId": "string"
          }
        },
        "masterNode": {
          "resources": {
            "resourcePresetId": "string",
            "diskSize": "int64",
            "diskTypeId": "string"
          }
        },
        "plugins": [
          "string"
        ]
      },
      "edition": "string"
    },
    "networkId": "string",
    "health": "Health",
    "status": "Status",
    "securityGroupIds": [
      "string"
    ],
    "serviceAccountId": "string",
    "deletionProtection": "bool",
    "maintenanceWindow": {
      // Includes only one of the fields `anytime`, `weeklyMaintenanceWindow`
      "anytime": "AnytimeMaintenanceWindow",
      "weeklyMaintenanceWindow": {
        "day": "WeekDay",
        "hour": "int64"
      }
      // end of the list of possible fields
    },
    "plannedOperation": {
      "info": "string",
      "delayedUntil": "google.protobuf.Timestamp"
    }
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
|| metadata | **[RestoreClusterMetadata](#yandex.cloud.mdb.elasticsearch.v1.RestoreClusterMetadata)**

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
|| response | **[Cluster](#yandex.cloud.mdb.elasticsearch.v1.Cluster)**

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

## RestoreClusterMetadata {#yandex.cloud.mdb.elasticsearch.v1.RestoreClusterMetadata}

#|
||Field | Description ||
|| clusterId | **string**

Required. ID of the new ElasticSearch cluster. ||
|| backupId | **string**

Required. ID of the backup used for recovery. ||
|#

## Cluster {#yandex.cloud.mdb.elasticsearch.v1.Cluster}

An Elasticsearch cluster resource.
For more information, see the [Concepts](/docs/managed-elasticsearch/concepts) section of the documentation.

#|
||Field | Description ||
|| id | **string**

ID of the Elasticsearch cluster.
This ID is assigned at creation time. ||
|| folderId | **string**

ID of the folder that the Elasticsearch cluster belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| name | **string**

Name of the Elasticsearch cluster.
The name must be unique within the folder. 1-63 characters long. ||
|| description | **string**

Description of the Elasticsearch cluster. 0-256 characters long. ||
|| labels | **string**

Custom labels for the Elasticsearch cluster as `key:value` pairs.
A maximum of 64 labels per resource is allowed. ||
|| environment | enum **Environment**

Deployment environment of the Elasticsearch cluster.

- `ENVIRONMENT_UNSPECIFIED`
- `PRODUCTION`: Stable environment with a conservative update policy when only hotfixes are applied during regular maintenance.
- `PRESTABLE`: Environment with a more aggressive update policy when new versions are rolled out irrespective of backward compatibility. ||
|| monitoring[] | **[Monitoring](#yandex.cloud.mdb.elasticsearch.v1.Monitoring)**

Description of monitoring systems relevant to the Elasticsearch cluster. ||
|| config | **[ClusterConfig](#yandex.cloud.mdb.elasticsearch.v1.ClusterConfig)**

Configuration of the Elasticsearch cluster. ||
|| networkId | **string**

ID of the network that the cluster belongs to. ||
|| health | enum **Health**

Aggregated cluster health.

- `HEALTH_UNKNOWN`: State of the cluster is unknown ([Host.health](/docs/managed-elasticsearch/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.elasticsearch.v1.Host) of all hosts in the cluster is `UNKNOWN`).
- `ALIVE`: Cluster is alive and well ([Host.health](/docs/managed-elasticsearch/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.elasticsearch.v1.Host) of all hosts in the cluster is `ALIVE`).
- `DEAD`: Cluster is inoperable ([Host.health](/docs/managed-elasticsearch/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.elasticsearch.v1.Host) of all hosts in the cluster is `DEAD`).
- `DEGRADED`: Cluster is in degraded state ([Host.health](/docs/managed-elasticsearch/api-ref/grpc/Cluster/listHosts#yandex.cloud.mdb.elasticsearch.v1.Host) of at least one of the hosts in the cluster is not `ALIVE`). ||
|| status | enum **Status**

Current state of the cluster.

- `STATUS_UNKNOWN`: Cluster state is unknown.
- `CREATING`: Cluster is being created.
- `RUNNING`: Cluster is running normally.
- `ERROR`: Cluster encountered a problem and cannot operate.
- `UPDATING`: Cluster is being updated.
- `STOPPING`: Cluster is stopping.
- `STOPPED`: Cluster stopped.
- `STARTING`: Cluster is starting. ||
|| securityGroupIds[] | **string**

User security groups ||
|| serviceAccountId | **string**

ID of the service account used for access to Object Storage. ||
|| deletionProtection | **bool**

Deletion Protection inhibits deletion of the cluster ||
|| maintenanceWindow | **[MaintenanceWindow](#yandex.cloud.mdb.elasticsearch.v1.MaintenanceWindow)**

Window of maintenance operations. ||
|| plannedOperation | **[MaintenanceOperation](#yandex.cloud.mdb.elasticsearch.v1.MaintenanceOperation)**

Maintenance operation planned at nearest maintenance_window. ||
|#

## Monitoring {#yandex.cloud.mdb.elasticsearch.v1.Monitoring}

Metadata of monitoring system.

#|
||Field | Description ||
|| name | **string**

Name of the monitoring system. ||
|| description | **string**

Description of the monitoring system. ||
|| link | **string**

Link to the monitoring system charts for the Elasticsearch cluster. ||
|#

## ClusterConfig {#yandex.cloud.mdb.elasticsearch.v1.ClusterConfig}

#|
||Field | Description ||
|| version | **string**

Elasticsearch version. ||
|| elasticsearch | **[Elasticsearch](#yandex.cloud.mdb.elasticsearch.v1.Elasticsearch)**

Configuration and resource allocation for Elasticsearch nodes. ||
|| edition | **string**

ElasticSearch edition. ||
|#

## Elasticsearch {#yandex.cloud.mdb.elasticsearch.v1.Elasticsearch}

#|
||Field | Description ||
|| dataNode | **[DataNode](#yandex.cloud.mdb.elasticsearch.v1.Elasticsearch.DataNode)**

Configuration and resource allocation for Elasticsearch data nodes. ||
|| masterNode | **[MasterNode](#yandex.cloud.mdb.elasticsearch.v1.Elasticsearch.MasterNode)**

Configuration and resource allocation for Elasticsearch master nodes. ||
|| plugins[] | **string**

Cluster wide plugins ||
|#

## DataNode {#yandex.cloud.mdb.elasticsearch.v1.Elasticsearch.DataNode}

#|
||Field | Description ||
|| elasticsearchConfigSet_7 | **[ElasticsearchConfigSet7](#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfigSet7)**

Elasticsearch 7.x data node configuration.

Includes only one of the fields `elasticsearchConfigSet_7`. ||
|| resources | **[Resources](#yandex.cloud.mdb.elasticsearch.v1.Resources2)**

Resources allocated to Elasticsearch data nodes. ||
|#

## ElasticsearchConfigSet7 {#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfigSet7}

Elasticsearch 7.x data node configuration.

#|
||Field | Description ||
|| effectiveConfig | **[ElasticsearchConfig7](#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfig72)**

Required field. Effective settings for an Elasticsearch cluster (a combination of settings defined in `userConfig` and `defaultConfig`). ||
|| userConfig | **[ElasticsearchConfig7](#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfig72)**

User-defined settings for an Elasticsearch cluster. ||
|| defaultConfig | **[ElasticsearchConfig7](#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfig72)**

Default settings for an Elasticsearch cluster. ||
|#

## ElasticsearchConfig7 {#yandex.cloud.mdb.elasticsearch.v1.config.ElasticsearchConfig72}

Elasticsearch 7.x supported configuration options are listed here.

Detailed description for each set of options is available in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html).

Any options that are not listed here are not supported.

#|
||Field | Description ||
|| maxClauseCount | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

The maximum number of clauses a boolean query can contain.

The limit is in place to prevent searches from becoming too large and taking up too much CPU and memory.
It affects not only Elasticsearch's `bool` query, but many other queries that are implicitly converted to `bool` query by Elastcsearch.

Default value: `1024`.

See in-depth description in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-settings.html). ||
|| fielddataCacheSize | **string**

The maximum percentage or absolute value (10%, 512mb) of heap space that is allocated to field data cache.

All the field values that are placed in this cache, get loaded to memory in order to provide fast document based access to those values.
Building the field data cache for a field can be an expensive operations, so its recommended to have enough memory for this cache, and to keep it loaded.

Default value: unbounded.

See in-depth description in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-fielddata.html). ||
|| reindexRemoteWhitelist | **string**

Remote hosts for reindex have to be explicitly allowed in elasticsearch.yml using the reindex.remote.whitelist property.
It can be set to a comma delimited list of allowed remote host and port combinations.
Scheme is ignored, only the host and port are used. ||
|| reindexSslCaPath | **string**

List of paths to PEM encoded certificate files that should be trusted.

See in-depth description in [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-reindex.html#reindex-ssl) ||
|#

## Resources {#yandex.cloud.mdb.elasticsearch.v1.Resources2}

Computational resources.

#|
||Field | Description ||
|| resourcePresetId | **string**

ID of the preset for computational resources available to a host (CPU, memory etc.).
All available presets are listed in the [documentation](/docs/managed-elasticsearch/concepts/instance-types). ||
|| diskSize | **int64**

Volume of the storage available to a host, in bytes. ||
|| diskTypeId | **string**

Type of the storage environment for the host.
All available types are listed in the [documentation](/docs/managed-elasticsearch/concepts/storage). ||
|#

## MasterNode {#yandex.cloud.mdb.elasticsearch.v1.Elasticsearch.MasterNode}

#|
||Field | Description ||
|| resources | **[Resources](#yandex.cloud.mdb.elasticsearch.v1.Resources2)**

Resources allocated to Elasticsearch master nodes. ||
|#

## MaintenanceWindow {#yandex.cloud.mdb.elasticsearch.v1.MaintenanceWindow}

#|
||Field | Description ||
|| anytime | **[AnytimeMaintenanceWindow](#yandex.cloud.mdb.elasticsearch.v1.AnytimeMaintenanceWindow)**

Includes only one of the fields `anytime`, `weeklyMaintenanceWindow`. ||
|| weeklyMaintenanceWindow | **[WeeklyMaintenanceWindow](#yandex.cloud.mdb.elasticsearch.v1.WeeklyMaintenanceWindow)**

Includes only one of the fields `anytime`, `weeklyMaintenanceWindow`. ||
|#

## AnytimeMaintenanceWindow {#yandex.cloud.mdb.elasticsearch.v1.AnytimeMaintenanceWindow}

#|
||Field | Description ||
|| Empty | > ||
|#

## WeeklyMaintenanceWindow {#yandex.cloud.mdb.elasticsearch.v1.WeeklyMaintenanceWindow}

#|
||Field | Description ||
|| day | enum **WeekDay**

- `WEEK_DAY_UNSPECIFIED`
- `MON`
- `TUE`
- `WED`
- `THU`
- `FRI`
- `SAT`
- `SUN` ||
|| hour | **int64**

Hour of the day in UTC. ||
|#

## MaintenanceOperation {#yandex.cloud.mdb.elasticsearch.v1.MaintenanceOperation}

#|
||Field | Description ||
|| info | **string** ||
|| delayedUntil | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)** ||
|#