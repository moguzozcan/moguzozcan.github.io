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
not need to be written in the same PL. 



