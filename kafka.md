# General

Brokers are Kafka servers that producers write to, and consumers read from

Num consumers in a group is upper-bounded by num partitions

Consumers keep track of what messages it has read by a numeric value called Offset

# Producer

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
