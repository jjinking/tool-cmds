# General

Kafka is a distributed streaming platform, not a message queue

Brokers are Kafka servers that producers write to, and consumers read from

Replication vs Partitions

Kafka depends on Zookeeper to serve metadata (i.e. service discovery) to producers and consumers

Topics are a category of messages


# Producers

Write data to a specific topic

## Batching

Specify amount to batch + time limit

More batching results in higher throughput because better data compression, but higher latency

## Acks settings

- 0
  - No acks from brokers
  - High throughput, low latency, message loss can occur

- 1
  - Acks from primary partition only, not from replicas
  - Medium throughput, medium latency, rare message loss

- 2
  - Acks from all brokers
  - Low throughput, high latency, very rare message loss
  
## Methods

- Simple send
- Sync send
- Async send
  - callback
  
## Serilization

- Avro
  - Hadoop project
  - Binary format
  - Language independent, with support for Java and Python
  - Uses JSON schema
  - Schema updates with backwards-compatibility
- JSON
  - Use with JSON schema
- Protobuf
  - Language and platform-neutral
  - Define structure and generate source code
- Thrift
  - Binary, compact binary, and HTTP-friendly

Store JSON Schema in schema registry
- checked by Producer and Consumer to serialize data
- Added to properties during Producer/Consumer object initialization

## Partitioning

Producers can use the hash of the key to write to a particular partition

If no key provided, uses round-robin


# Consumers

- Poll partitions for data

## Consumer groups

- Consumer group is set in Properties object during instantiation of consumer
- Consumer groups can poll different partitions of same topic and work together to process unique messages
  - Num consumers in a group is upper-bounded by num partitions (no adv to have more consumers than partitions)
- Consumers keep track of what messages it has read from a specific partition by a numeric value called Offset
- Each consumer must run on separate thread
- Re-list all subscriptions whenever `subscribe()` is called - not additive
- Multiple consumer groups must deal with order guarantee

## Partition Rebalance

Consumer assignment to partition changes when the number of consumers changes (add or remove)
 
First consumer acts as leader
- talks to zookeeper
- assigns partitions to new consumers

## Poll loop

- Partition assignment
- Message fetching
- Rebalancing - changing assignments

## Commits

- Kafka keeps track of offsets of consumers also
- Discrepancies between offset in consumer and Kafka can result in data loss or data duplication in a rebalancing event
- Manually call `commitSync()` to sync up commits after finishing processing data in consumer


