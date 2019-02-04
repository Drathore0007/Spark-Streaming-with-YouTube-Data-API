# Kafka and Spark pysaprk

1. Start Zoo-keeper:

 		bin/zkServer.sh start

2. Start kafka sever with zookeeper:

		bin/kafka-server-start.sh config/server.properties

3. Create a topic for your kafka:

		kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic    	topic_name

 4. Start producer 

    	 bin/kafka-console-producer.sh --broker-list localhost:9092 --topic youtube

5. Run your spark code with spark-sumit and with external kafka utils jar file:

		spark-submit --jars ./spark-streaming-kafka-0-8-assembly_2.11-2.2.1.jar spark-code_to_run.py localhost:2181 topic_name

### Note: If you have give topic and zookeeper detail in code than no need to do that while running screapt.

6. Start Spark stream for listening Zooker:


		spark-submit --jars  ./spark-streaming-kafka-0-8-assembly_2.11-2.2.1.jar  codes/spark_stream_test.py localhost:2181 youtube