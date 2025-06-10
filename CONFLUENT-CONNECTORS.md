## Confluent Platform Components Needed

- Confluent KRaft Nodes - Metadata Management
- Confluent Kafka Nodes - Storage
- Kafka Connect - Data store routing of events from Source to Sinks
- Confluent REST Proxy - Rest Interface for Kafka
- Confluent Schema Registry - To manage data contracts for Topics
- Confluent KSQL DB - to process events from multiple topics and store the results in a new topic


## Confluent Kafka Connectors Needed
- [Debezium Source Connector](https://docs.confluent.io/kafka-connectors/debezium-sqlserver-source/current/overview.html)
- [JDBC Source + Sink Connector](https://docs.confluent.io/kafka-connectors/jdbc/current/overview.html)
- [S3 Source Connector](https://docs.confluent.io/kafka-connectors/s3-source/current/index.html)
- [Azure Blob Source Connector](https://docs.confluent.io/kafka-connectors/azure-blob-storage-source/current/index.html)
- [Azure Blob Sink Connector](https://docs.confluent.io/kafka-connectors/azure-blob-storage-sink/current/overview.html)
- [Azure Data Lake Store Sink Connector](https://docs.confluent.io/kafka-connectors/azure-data-lake-gen2-sink/current/overview.html)

## Event Publish & Subscribe Pipeline
- Data will be arriving from REST proxy clients, direct publishing clients and data sources (Azure Blob Store, S3 Buckets, Azure DB for PostgreSQL and Azure SQL Database)
- These events will arrive at the designated topics
- Events from multiple topics will be processed, joined, filtered and enriched at the KSQLDB layer and pushed to finalized topics
- Subscribers will subscribe to these Kafka topics directly or via Confluent REST proxy
- These finalized datasets will also be pushed to Sinks via Kafka connect (Azure Blob, Azure Data Lake Store, Azure SQL Database, Azure AI Search)
- Sinks with curated such as Azure Data Lake Store, Azure Blob Store, AI Search or SQL Database can be used to serve as the data mesh
- Azure Purview can also be used to set up a data catalog from the curated datasets
- Natural language queries can be run against the dataset in AI Search
- Power BI dashboards can be used to run analysis on the dataset in SQL Database or ADLS


