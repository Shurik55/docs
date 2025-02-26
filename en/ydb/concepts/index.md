# {{ ydb-full-name }} overview


{{ ydb-full-name }} allows you to create and manage {{ ydb-short-name }} databases in {{ yandex-cloud }}.

To learn more about {{ ydb-full-name }} concepts, see the following articles:

* [{#T}](resources.md)
* [{#T}](serverless-and-dedicated.md)
* [{#T}](dynamodb-tables.md)
* [{#T}](limits.md)

## {{ ydb-short-name }} DBMS {#ydb}

[{{ ydb-short-name }}](https://ydb.tech/en) is a horizontally scalable distributed fault-tolerant DBMS. {{ ydb-short-name }} is designed for high performance with a typical server being capable of handling tens of thousands of queries per second. The system is designed to handle hundreds of petabytes of data. {{ ydb-short-name }} can operate in both single data center and distributed (cross data center) modes on a cluster of thousands of servers.

{{ ydb-short-name }} enables online transaction and online analytical processing (OLTP and OLAP).

To work with {{ ydb-short-name }}, you can use the [{{ ydb-short-name }} CLI]({{ ydb.docs }}/reference/ydb-cli/) and the [SDKs]({{ ydb.docs }}/reference/ydb-sdk/) for C++, Java, Python, Node.js, PHP, and Go. As a database query language, you can use [YQL]({{ ydb.docs }}/yql/reference/), an SQL dialect. To learn about using the {{ ydb-short-name }} tools for application development, see the [Recommendations]({{ ydb.docs }}/best_practices/) section.

To learn more about {{ ydb-short-name }} concepts, see the following articles:

* [Terms and definitions]({{ ydb.docs }}/concepts/databases)
* [Data model and schema]({{ ydb.docs }}/concepts/datamodel)
* [Transactions]({{ ydb.docs }}/concepts/transactions)
* [Secondary indexes]({{ ydb.docs }}/concepts/secondary_indexes)
* [Change Data Capture (CDC)]({{ ydb.docs }}/concepts/cdc)
* [Time to Live (TTL)]({{ ydb.docs }}/concepts/ttl)
* [Scan queries]({{ ydb.docs }}/concepts/scan_query)
* [Database limits]({{ ydb.docs }}/concepts/limits-ydb)
* [{{ ydb-short-name }} cluster]({{ ydb.docs }}/concepts/cluster/)


## Service Level Agreement {#sla}

{{ ydb-full-name }} is subject to the [Service Level Agreement](https://yandex.com/legal/cloud_sla). The service level is defined in [Service Level for Yandex {{ ydb-name }}](https://yandex.com/legal/cloud_sla_ydb).

