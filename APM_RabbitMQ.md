---
title: APM RabbitMQ
tags: Intern, APM
description: RabbitMQ
---


# OpenStack RabbitMQ Deep Dive for Integration and Monitoring
    Link:https://messeiry.com/openstack-rabbitmq-deep-dive/
    
## What is RabbitMQ ?
- Open source message broker
- Lightweight and easy to deploy on-premises and in the cloud
- Can be deployed in distributed and federated configurations to meet high-scale, high-availability requirements

- Rabbit MQ uses AMQP 0-9-1 protocol (Advanced Message Queuing Protocol); which enables conforming client applications to communicate with conforming messaging middleware brokers.

### RabbitMQ
- Message brocker that implement AMQP(Advanced Message Queuing Protocol)
- AMPQP standardlizes messaging using Producers, Broker and Consumers
- Messaging increases loose coupling and scalability
![](https://i.imgur.com/qrM5NNk.png)
- Publishing: Producer send Message to Exchange and Exchange forward Message to the queue
- Consuming: Consumer pick up the Message from the queue

![](https://i.imgur.com/uMHY3gQ.png)

- Guarantee of sending messages to queue and ack from consumer
- Failure
    - Redilivery
        - scenario 1: Producer doesn't get confirm from queue cause dupicated meesages
        - scenario 2: Ack failure (Message remain in the queue) cause a consumer get the message again 

![](https://i.imgur.com/dJ3QMgE.png)

- Message will be sent with routing keys
- Type of exchange:
    - Fanout: Send the message to all the queue
    - Direct: Send to the queue where routing key=binding key
    - Topic: allows partial match (ex: routing key=red. binding key= red.blue will send the message)
    - *(star) can substitute for exactly one word (shape.* )
    - #(hash) can substitute for zero or more word(shape.# )
    - Header: message header instead of routing key
- Default(nameless) exchange
    - routing key = queue name
    ![](https://i.imgur.com/7zOLmcP.png)
    - if routing key =queue name then send message to the queue
    - Special exchange created by RabbitMQ
    - Compares routing key with queue name
    - Indirectly allows sending directly to queue

    
- Core concept of Rabbit Message Queue
    - Producer emits massages to exchange
    - Consumer recieves messages from queue
    - Binding connects an exchange with a queue using binding key
    - Exchange compares routing key with binding key
    - Messages distribution depends on exchange type



## OpenStack and RabbitMQ
- OpenStack uses a message queue to coordinate operations and status information among services (像openstack的神經)
- **非同步**的傳訊息方式
- 再傳Messages時，直接丟到exchange中就不理他，在大系統的時候不用像同步系統會有互相等process完成才能繼續執行









    
    
    



# An agent-less approach to application-level dependency map discovery using virtual machine inspection (APM-MQ)

- Application dependency mapping (ADM) creates relationships between interdependent applications.(ex: database and web application)
- The ADT prototype proposes a method to generate accurate application dependency map by intercepting(攔截) VM execution and introspecting(自省) VM state.

- Why we need a distributed application’s performance management system? -> single node’s performance problem in a distributed system would affect whole distributed system’s QoS.
- Too many Divices, NFV, virtual data center(VDC) dirve the ADT
- Dependency mapping system arise, since SW problem is harder to dectact than HW problem.
![](https://i.imgur.com/QUTTa0g.png)


## Existing Technology
- Install daemon on machine background process to collect inter-machine TCP traffic log and generate inter-machine dependency (can only generate **static** DM)

## Socket Based Application
1. Intercept guest OS’s at packet sending system call
2. Perform VM introspection to get running thread and TCP connection information. Send this traffic log to server
3. Convert thread based traffic log into inter-thread traffic log in APM (Application Performance Management) server
4. Generate accurate application dependency map from inter-thread traffic logs

-  Thread level execution
- VM introspection help interception at system call enables quick detection and deployment of changes in the machine
- Multi-process or multi-thread server and the prototype also produces the **trajectory** along with an accurate ADM
![](https://i.imgur.com/RT93Hvf.png)



## Approach for Message Based Application:
- The software architecture of enterprise service bus is widely used and its underlined message passing mechanism is message queue
- Problem in application discovery of queue based application:
![](https://i.imgur.com/021Ubjp.png)

- Advantages of using checksum approach