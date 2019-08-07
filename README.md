# microservice and kafka
Two microservices running and talking to eachother using kafka.

# Installing Kafka 
To download and install Kafka, please refer the [official guide](https://kafka.apache.org/quickstart)

Once you download Kafka, you can issue a command to start ZooKeeper which is used by Kafka to store metadata.
```
zookeeper-server-start.bat .\config\zookeeper.properties
```

Next, we need to start the Kafka cluster locally by issuing the below command.
```
kafka-server-start.bat .\config\server.properties 
```

Now, by default, the Kafka server starts on localhost:9092.

we need a way to tell our application where to find the Kafka servers and create a topic and publish to it. We can do it using application.yaml in both the services.

bring up both the services using 
```
gradlew bootRun
```

hit the below endpoint
```
localhost:9000/kafka/publish?message=HelloFromKafkaProducer
```
note that:
- kafkaexample runs on port 9000
- kafkaconsumer runs on port 8080

Now if check the console logs of the kafkaconsumer service which was bootRun on por 8080, we should be seeing the message from kafka topic "users"
