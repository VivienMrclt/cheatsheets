# Kafka

Documentation - https://zookeeper.apache.org/doc/trunk/

## Elements
- server kafka that we call **broker**
- cluster manager called **zookeper**

## Small rough setup

```
bin/zookeeper-server-start.sh config/zookeeper.properties

---

./bin/kafka-server-start.sh ./config/server.properties

---

./bin/kafka-server-start.sh ./config/server2.properties

---

# Create topic blabla
./bin/kafka-topics.sh --create --topic blabla --bootstrap-server localhost:9092 --replication-factor 2 --partitions 10
# Check creation
./bin/kafka-topics.sh --list --bootstrap-server localhost:9092
# Create producer
./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic blabla group.id=mygroup

# CLI 4

./bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic blabla

```

