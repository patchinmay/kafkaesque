# TEAM NAME project-kafkaesque
Final Project for CSCI 6421 

Team Members
```
Aarohi Agarwal (@aarohi11 )
Biyas Basak (@biyasbasak)
Chinmay Patil (@patchinmay)
Dilip Varma Sagi (@dilipvarma3)
```

## (Optional) Proposed Project Description
This project emulates a publish subscribe communication model for distributed systems for collecting and distributing real-time data generated from multiple sources using existing systems such as Apache Kafka and RabbitMQ as a reference and making improvements over them. As a part of implementation, a publisher-subscriber model for distributing messages is created in which multiple consumers (VM's, servers, etc.) form consumer groups to  subscribe to a topic to receive data from a message queue known as broker on which the producers publish data on different topics. Some of the advantages of implementing a publisher-subscriber model is it aims at scalability and also addresses an old messaging problem called group messaging. This project also explores how to partition the log messages across topics and replicate them across these partitions to achieve fault tolerance.
. 
