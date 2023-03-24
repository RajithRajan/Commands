### Starting Kafka
_Starting zookeeper_

```
./zookeeper-server-start.sh ../config/zookeeper.properties
```
- _In backgroud mode_
```
./zookeeper-server-start.sh -daemon ../config/zookeeper.properties
```

_Starting Kafka server_

```
./kafka-server-start.sh ../config/server.properties
```
- _In backgroud mode_
```
./kafka-server-start.sh -daemon ../config/server.properties
```

### Topics 
_Creating topic_

```
kafka-topics.sh --bootstrap-server <ip>:9092 --create --topic <topic_name> --partitions 3 --replication-factor 1 --config max.message.bytes=64000 --config flush.messages=1 
```

_Delete topic_

```
kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic <topic_name>
```
 
_Listing topics_

```
kafka-topics.sh --bootstrap-server <ip>:9092 --list
```

### Consumer 
_Creating Consumer_ 

```
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic_name>
```

```
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic_name>  --from-beginning --formatter kafka.tools.DefaultMessageFormatter --property print.timestamp=true --property print.key=true --property print.value=true
```

```
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic_name>  --from-beginning --formatter kafka.tools.DefaultMessageFormatter --property print.key=true --property print.value=true
```

_Listing consumer Groups_

```
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
```

### Producer
_Creating Console Producer_ 
```
./kafka-console-producer.sh --bootstrap-server localhost:9092 --topic <topic_name>
```
