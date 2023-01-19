# Core Concepts

DeltaStream is a serverless database to manage, secure and process all your streams on cloud. This data is stored in streaming storage services such as Apache Kafka or AWS Kinesis and are owned by users and are accessed by other user applications besides DeltaStream. DeltaStream provides a unified relational view of the data in user stores enabling users to organize, secure and process the data with a familiar relational model. To process the data, DeltaStream will read from and write into user storage services.

### Store:: <a href="#_store" id="_store"></a>

A store is the representation of the physical location where user data resides. Stores can be streaming stores, such as Apache Kafka where data is stored in topics, or batch stores like AWS S3 where data is stored in files. DeltaStream reads data from stores, performs the desired computation, and writes the results of the computation to the same store or another. Stores are owned by users and in order to access the data in a store, the user configures connectivity and access to the store. For instance, if a user has an Apache Kafka cluster provided by Confluent Cloud, she can declare a store in DeltaStream by setting up the connectivity and access. Once the store is defined, DeltaStream can read from topics in the Kafka cluster and write into topics in the Kafka cluster.

### Database <a href="#_database" id="_database"></a>

Similar to other relational databases, a database is a logical grouping of schemas in DeltaStream. Databases are the foundation for organizing data in DeltaStream and provide the building block of its namespacing model. Users can create databases for logical groupings for different teams or projects. For instance, you can create a database for a logging project and another for an ads team.

### Schema <a href="#_schema" id="_schema"></a>

A schema is a logical grouping of relational objects such as Streams, Changelogs, Materialized Views, and Tables. As mentioned above, schemas are grouped in a database. A combination of databases and schemas enable users to organize their streams, changelogs, and other database objects in a hierarchical fashion in DeltaStream. Such hierarchies also are one of the bases for providing Role-based Access Control (RBAC) in DeltaStream the same way as other relational databases.

### Relation <a href="#_relation" id="_relation"></a>

DeltaStream provides a relational model for streaming data where data is stored in relations. Currently, we have three types of relations in DeltaStream:

* Stream
* Changelog
* Materialized View

These relations are building blocks of user applications and pipelines in DeltaStream.

#### Stream <a href="#_stream" id="_stream"></a>

A stream is a sequence of immutable, partitioned, and partially ordered events (we use events and records synonymously). A stream is a relational representation of data in streaming stores, such as the data in a Kafka topic or a Kinesis stream. The records in a stream are independent of each other, meaning there is no correlation between two records in a stream. A stream declares the schema of the records, which includes the column name along with the column type and optional constraints.

#### Changelog <a href="#_changelog" id="_changelog"></a>

Similar to a stream, a changelog is a sequence of partitioned and partially ordered events (we use events and records synonymously). Similar to a stream, a changelog is a relational representation of data in the streaming stores, such as the data in a Kafka topic or a Kinesis stream. Changelog defines a PRIMARY KEY for records that is used to represent the change over time for records with the same primary key. Records in a changelog correlate with each other based on the PRIMARY KEY. This means that a record in a changelog either is an insert record if it’s the first time the record with the given PRIMARY KEY is appended to the changelog or upsert records if a previous record with the same PRIMARY KEY has been inserted into the changelog.

#### Materialized View <a href="#_materialized_view" id="_materialized_view"></a>

Materialized view creates a snapshot of a streaming query result and continuously updates the snapshot as records arrive to the query input(s). A materialized view is quariable in DeltaStream, meaning that you can query the materialized view and the result of such a query will be computed using the data in the snapshot at the time of the query. Note that queries on a materialized view are not streaming queries, and they are the same as the queries on tables and materialized views in traditional relational databases.

### Streaming or Continuous Query <a href="#_streaming_or_continuous_query" id="_streaming_or_continuous_query"></a>

A streaming or continuous query in DeltaStream reads from one or more streams or changelogs, processes the data according to the query logic, and generates one or more streams or changelogs. Streaming queries are continuous, meaning that once they are started, they keep running until explicitly terminated. There are two types of streaming queries in DeltaStream:

* **Persistence streaming (continuous) queries:** These queries persist the result of the query in the streaming storage by creating new streams or changelogs.
* **Interactive streaming (continuous) queries:** Once started, these queries continuously run and stream the results of the query to the user.
