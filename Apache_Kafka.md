## Title
# Apache Kafka
Apache Kafka is a framework implementation of a software bus using stream-processing. Apache Kafka is an open-source distributed event streaming platform used by thousands of companies for high-performance data pipelines, streaming analytics, data integration, and mission-critical applications.

*Interesting!*

## Architecture  
Kafka stores key-value messages that come from arbitrarily many processes called producers. The data can be partitioned into different "partitions" within different "topics". Within a partition, messages are strictly ordered by their offsets (the position of a message within a partition), and indexed and stored together with a timestamp. Other processes called "consumers" can read messages from partitions. 

For stream processing, Kafka offers the Streams API that allows writing Java applications that consume data from Kafka and write results back to Kafka.

There are five major APIs in Kafka: 
- **Producer API** – Permits an application to publish streams of records.
- **Consumer API** – Permits an application to subscribe to topics and processes streams of records.
- **Connector API** – Executes the reusable producer and consumer APIs that can link the topics to the existing applications.
- **Streams API** – This API converts the input streams to output and produces the result.
- **Admin API** – used to manage Kafka topics, brokers and other Kafka objects.
 
The consumer and producer APIs build on top of the Kafka messaging protocol and offer a reference implementation for Kafka consumer and producer clients in Java. The underlying messaging protocol is a binary protocol that developers can use to write their own consumer or producer clients in any programming language. This unlocks Kafka from the Java Virtual Machine (JVM) eco-system. A list of available non-Java clients is maintained in the Apache Kafka wiki.

**Connect API**

Kafka Connect (or Connect API) is a framework to import/export data from/to other systems. It was added in the Kafka 0.9.0.0 release and uses the Producer and Consumer API internally. The Connect framework itself executes so-called "connectors" that implement the actual logic to read/write data from other systems. The Connect API defines the programming interface that must be implemented to build a custom connector. Many open source and commercial connectors for popular data systems are available already. However, Apache Kafka itself does not include production ready connectors.

**Streams API**

Kafka Streams (or Streams API) is a stream-processing library written in Java. It was added in the Kafka 0.10.0.0 release. The library allows for the development of stateful stream-processing applications that are scalable, elastic, and fully fault-tolerant. The main API is a stream-processing domain-specific language (DSL) that offers high-level operators like filter, map, grouping, windowing, aggregation, joins, and the notion of tables. Additionally, the Processor API can be used to implement custom operators for a more low-level development approach. The DSL and Processor API can be mixed, too. For stateful stream processing, Kafka Streams uses RocksDB to maintain local operator state. Because RocksDB can write to disk, the maintained state can be larger than available main memory. For fault-tolerance, all updates to local state stores are also written into a topic in the Kafka cluster. This allows recreating state by reading those topics and feed all data into RocksDB. The latest version of Streams API is 2.8.0. The link also contains information about how to upgrade to the latest version.

**Version compatibility**

Up to version 0.9.x, Kafka brokers are backward compatible with older clients only. Since Kafka 0.10.0.0, brokers are also forward compatible with newer clients. If a newer client connects to an older broker, it can only use the features the broker supports. For the Streams API, full compatibility starts with version 0.10.1.0: a 0.10.1.0 Kafka Streams application is not compatible with 0.10.0 or older brokers. 

**References**
- https://www.confluent.io/lp/apache-kafka
- https://en.wikipedia.org/wiki/Apache_Kafka
