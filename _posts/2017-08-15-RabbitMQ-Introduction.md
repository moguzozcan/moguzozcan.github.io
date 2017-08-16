---
layout: post
title: "Introduction to RabbitMQ"
date: 2017-08-15
---

Let's temper into RabbitMQ. 
1. Installation: 
Firstly, Erlang is required to install RabbitMQ server. Link is here: http://www.erlang.org/downloads.
After successfully installing Erlang, download RabbitMQ installer exe from: https://www.rabbitmq.com/install-windows.html
Then just run the installer, rabbitmq-server-3.6.10.exe. It will set RabbitMQ up and running as a service, with a default configuration.

2. What is RabbitMQ:
RabbitMQ is a messaging queue, where the applications define some queues connect and send messages on those queues. It is called message
broker or queue manager. It allows two separate and different applications to be able to talk to each other easily. The applications does 
not need to be written in the same programming language. Producer, generates messages and consumer is getting the message. Messages can 
also be stored in the queue.

RabbitMQ uses AMQP(Advanced Messaging Queue) protocol. 

3. A sample tutorial:
I've worked on the RabbitMQ tutorials provided in the official website. [1]
The first tutorial is the very basic application, where there is one producer and one consumer. Producer sends a message and consumer 
receives it. Steps:

1. Create a maven project from your IDE, I prefer IntelliJ IDEA. Then edit the parent pom for dependencies like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>io.github.moguzozcan</groupId>
    <artifactId>rabbitmq-tutorial</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>com.rabbitmq</groupId>
            <artifactId>amqp-client</artifactId>
            <version>4.0.2</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-simple</artifactId>
            <version>1.6.4</version>
        </dependency>
    </dependencies>
</project>
```

Don't forget to change your groupId and artifactId wrt to the names you select while creating the maven project.

2. Create a Java class named "Send.java" and copy the following content. The official resource is giving some errors, they forget to 
handle ```java TimeoutException``` that ```java factory.newConnection();``` throws. I've added this correction and now it works without 
a problem.

```java
import com.rabbitmq.client.ConnectionFactory;
import com.rabbitmq.client.Connection;
import com.rabbitmq.client.Channel;

import java.util.concurrent.TimeoutException;

public class Send {

    private final static String QUEUE_NAME = "hello";

    public static void main(String[] argv) throws java.io.IOException, TimeoutException {
        ConnectionFactory factory = new ConnectionFactory();
        factory.setHost("localhost");
        Connection connection = null;
        connection = factory.newConnection();

        Channel channel = connection.createChannel();

        channel.queueDeclare(QUEUE_NAME, false, false, false, null);
        String message = "Hello World!";
        channel.basicPublish("", QUEUE_NAME, null, message.getBytes());
        System.out.println(" [x] Sent '" + message + "'");

        channel.close();
        connection.close();
    }
}
```

3. Create a class named Recv.java and copy the following content. 

```java
import com.rabbitmq.client.*;

import java.io.IOException;
import java.util.concurrent.TimeoutException;

public class Recv {
    private final static String QUEUE_NAME = "hello";

    public static void main(String[] argv) throws java.io.IOException, java.lang.InterruptedException, TimeoutException {

        ConnectionFactory factory = new ConnectionFactory();
        factory.setHost("localhost");
        Connection connection = factory.newConnection();
        Channel channel = connection.createChannel();

        channel.queueDeclare(QUEUE_NAME, false, false, false, null);
        System.out.println(" [*] Waiting for messages. To exit press CTRL+C");

        Consumer consumer = new DefaultConsumer(channel) {
            @Override
            public void handleDelivery(String consumerTag, Envelope envelope,
                                       AMQP.BasicProperties properties, byte[] body)
                    throws IOException {
                String message = new String(body, "UTF-8");
                System.out.println(" [x] Received '" + message + "'");
            }
        };
        channel.basicConsume(QUEUE_NAME, true, consumer);
    }
}
```

4.Firstly, run Send.java then run Recv.java and you will see that the messages are being sent w/out a problem.

There are some important commands while using RabbitMQ Server, I've listed them here:
-rabbitmq-server.bat : to start server
-rabbitmqctl.bat list_queues : list queues
-rabbitmqctl.bat status : shows the current status of the server

References:
[1] http://www.rabbitmq.com/tutorials/tutorial-one-java.html
