# Milestone 1

### Introduction

There is a growing trend in the software world to develop software as autonomous distributed services often known as microservices, and for good reason. Microservices provide requirement based scalability of individual services, smaller services are also easy and quick to deploy, better resiliency, if one service goes down, other services can still at some capacity keep working. 

While microservices certainly have benefits, they have issues that make it difficult to implement and maintain them at scale. One of the big ones being providing an easy and reliable way of communicating between these services. The solution to the problem already exists in the form of message broker for example Apache Kafka and rabbitMQ, our team is trying to implement a publish subscribe framework with a subset of features based on the principles laid down by Apache Kafka and compare them to better understand distributed system principles.


### Challenges

* <strong> Decoupling of services </strong>

The pub-sub messaging framework provides a broker that both producer and consumer services can connect to without knowing the actual address of the destination service. This framework uses asynchronous communication. The consumers or subscribers subscribe to something called a topic in case of kafka, and are notified every time data is available for processing in queue. Whenever the consumers are free, they read the message from queue, read it and then remove it from queue. Multiple consumers can read the same topic at their own pace. This leads to decoupling of services - such that system becomes more robust and failure of one of the nodes in any of the consumer group will not affect the performance of other nodes processing the data.


* <strong> Fault Tolerance and High Availability </strong>

In distributed message queuing systems like Kafka, topics are divided into partitions which can be written by multiple producers at the same time. The subscriber clients form consumer groups to read messages from the partitions. Within a consumer group, each consumer reads messages which form the subset of partition. These partitions are in turn replicated to multiple brokers (message queues) to ensure fault tolerance. The replication factor indicates how many copies of partition are maintained for each topic. Further, the message ordering is handled within replicated queues using leader-follower pattern. Each partition has a single leader to handle read and write requests and a configurable number of followers to replicate writes to leaders in the background. To avoid single point of failure, we will be implementing resource manager instead of a single master node to initiate a new leader election in case of broker hosting the leader fails. This information is then propagated to all the clients subscribed to a topic in that partition.

* <strong> Scalability </strong>

The messages are store in topics which in turn are divided into partition. As partitions form independent units within a topic, these allow brokers to scale out horizontally and manage load within the cluster. The Cluster capacity can be increased by adding new message queues and partitions. This idea is from Kafka which implements topics and partitions as a way of managing and scaling messages delivery.


### Outcome

At the end of this project we will have a publish subscribe distributed messaging system which will be taking data from multiple publishers and will be serving it to all the subscribers. The system is implemented in a way that is highly scalable and fault tolerant.

<strong>References</strong>

* Wu, H., Shang, Z., & Wolter, K. (2019, August). Performance Prediction for the Apache Kafka Messaging System. In 2019 IEEE 21st International Conference on High Performance Computing and Communications; IEEE 17th International Conference on Smart City; IEEE 5th International Conference on Data Science and Systems (HPCC/SmartCity/DSS) (pp. 154-161). IEEE.

* Dixit, S., & Madhu, M. P. (2019). Distributing Messages Using Rabbitmq with Advanced Message Exchanges. International Journal of Research Studies in Computer Science and Engineering (IJRSCSE), 6 (2), 24-28.

* Apache Software Foundation 2017b; Kreps et al. 2011; Goodhope et al. 2012; Wang et al. 2015; Kleppmann and Kreps 2015.*

* Kreps, J., Narkhede, N., & Rao, J. (2011, June). Kafka: A distributed messaging system for log processing. In Proceedings of the NetDB (Vol. 11, pp. 1-7).


