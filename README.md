# Kafka
* Konfiguracja zookeeper
```shell
nano config/zookeeper.properties
```

* Zmiana ścieżki w pliku config/zookeeper.properties
```shell
dataDir=/home/gcharkiewicz/myKafka/kafka_2.13-3.1.0/data/zookeeper
```

* Uruchomienie zookeeper
```shell
bin/zookeeper-server-start.sh config/zookeeper.properties
```

* Konfiguracja kafki 
```shell
nano config/server.properties
```

* Dodanie ścieżek
```shell
listeners=PLAINTEXT://127.0.0.1:9092
zookeeper.connect=127.0.0.1:2181
```

* Uruchomienie kafki
```shell
kafka-server-start.sh config/server.properties
```


* Dodanie pierwszego topicu 
```shell
bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092
```

* Dodanie topicu z partycjami oraz replikami
```shell
bin/kafka-topics.sh --create --topic first_topic --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
```

* Listowanie topiców
```shell
kafka-topics.sh --list --bootstrap-server localhost:9092
```

* Dokładne informacje o topicu 
```shell
kafka-topics.sh --bootstrap-server localhost:9092 --topic first_topic --describe
```

* Usunięcie topicu 
```shell
bin/kafka-topics.sh --create --topic secend_topic --bootstrap-server localhost:9092 --partitions 6 --replication-factor 1

kafka-topics.sh --bootstrap-server localhost:9092 --topic secend_topic --delete
```

## Kafka Console Producer Command Line Interface (CLI)

```shell
kafka-console-producer.sh --bootstrap-server localhost:9092 --topic secend_topic
>Pochmurna środa  
>Kafka
>Wiadomość 
ctrl+c
```

## Kafka Console Consumer Command Line Interface (CLI)

* Czytanie wiadomości w czasie rzeczywistym
```shell
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic new_topic_2
```

* Czytanie starczych wiadomości 
```shell
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic new_topic_2 -- from-beginning
```

## Kafka Consumers in a Group
