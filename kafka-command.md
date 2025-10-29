
### KAFKA
%KAFKA_HOME%\bin\windows\kafka-server-start.bat %KAFKA_HOME%\config\server.properties

%KAFKA_HOME%\bin\windows\kafka-stop-start.bat 

### ZOOKEEPER
%KAFKA_HOME%\bin\windows\zookeeper-server-start.bat %KAFKA_HOME%\config\zookeeper.properties
%KAFKA_HOME%\bin\windows\zookeeper-server-stop.bat 

### Kafdrop
java -jar "C:\kafdrop-4.2.0.jar" --kafka.brokerConnect=localhost:9092


### TOPICS
#### Creating a topic
%KAFKA_HOME%/bin/windows/kafka-topics.bat --bootstrap-server localhost:9092 --create --partitions 3 --replication-factor 1  --topic getting-started
#### Listing topics
%KAFKA_HOME%/bin/windows/kafka-topics.bat --bootstrap-server localhost:9092 --list --exclude-internal
#### Describing a topic
%KAFKA_HOME%/bin/windows/kafka-topics.bat --bootstrap-server localhost:9092 --describe --topic getting-started
#### Deleting a top
%KAFKA_HOME%/bin/windows/kafka-topics.bat --bootstrap-server localhost:9092 --topic getting-started --delete


### PRODUCERS


### CONSUMERS
#### Listing consumer groups
%KAFKA_HOME%/bin/windows/kafka-consumer-groups.bat --bootstrap-server localhost:9092 --list
#### Describing a consumer group
%KAFKA_HOME%/bin/windows/kafka-consumer-groups.bat --bootstrap-server localhost:9092 --group cli-consumer --describe --all-topics
#### describe all groups
%KAFKA_HOME%/bin/windows/kafka-consumer-groups.bat --bootstrap-server localhost:9092 --describe --all-groups --all-topics
#### Describe more in detail
%KAFKA_HOME%/bin/windows/kafka-consumer-groups.bat --bootstrap-server localhost:9092 --describe --all-groups --state
#### Deleting a consumer group
%KAFKA_HOME%/bin/windows/kafka-consumer-groups.bat --bootstrap-server localhost:9092 --group cli-consumer --delete


### RECORDS
#### Publishing records
%KAFKA_HOME%\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic getting-started --property "parse.key=true" --property "key.separator=:"
#### Consuming records
%KAFKA_HOME%\bin\windows\kafka-console-consumer.bat  --bootstrap-server localhost:9092 --topic getting-started --group cli-consumer --from-beginning --property "print.key=true" --property "key.separator=:"

### OFFSETS
#### Resetting the entire topic
%KAFKA_HOME%\bin\windows\kafka-consumer-groups.bat --bootstrap-server localhost:9092 --topic getting-started --group cli-consumer --reset-offsets --to-earliest --execute
####  Resetting the specific patitions: <topic-name>:<first-partition>,<second-partition>,...,<N-th-partition>
%KAFKA_HOME%\bin\windows\kafka-consumer-groups.bat --bootstrap-server localhost:9092 --topic getting-started:0,1 --group cli-consumer --reset-offsets --to-offset 2 --execute
#### Deleting offsets
%KAFKA_HOME%\bin\windows\kafka-consumer-groups.bat --bootstrap-server localhost:9092 --topic getting-started --group cli-consumer --delete-offsets

