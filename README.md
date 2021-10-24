# CS3219_D

Clone the repo at the GitHub link above

Build the Docker image with `docker build -t kafka_base .`

Launch the kafka cluster with `docker-compose up`

Run `docker ps` to check if the cluster is up if necessary

If the cluster is up, run a kafka client `docker run -it --network host kafka_base /bin/bash`

And run a consumer `./bin/kafka-console-consumer --topic kj_topic --bootstrap-server localhost:9091,localhost:9092,localhost:9093`

In a separate terminal, run a kafka client `docker run -it --network host kafka_base /bin/bash`

Create a topic `./bin/kafka-topics --create --zookeeper localhost:2181 --replication-factor 3 --partitions 3 --topic kj_topic`

And run a producer `./bin/kafka-console-producer --broker-list localhost:9091,localhost:9092,localhost:9093 --topic kj_topic`

In the producer terminal, send a message to the terminal. Check in the consumer terminal that the message is received.

In a separate terminal, run `docker stop broker1`

In the producer terminal, send another message to the consumer

In the consumer terminal, check if the 2nd message is received as well




Credits to Pierre Kieffer for his tutorial on Kafka https://medium.com/@PierreKieffer/deploy-a-kafka-multi-node-cluster-with-docker-72878ddbaf96
