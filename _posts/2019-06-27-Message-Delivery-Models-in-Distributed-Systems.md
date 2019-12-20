---
title: "Message Delivery Models in Distributed Systems"
date: 2019-06-27
categories: 
  - Distibuted Systems
  - Message Delivery Models
  - Exacly Once 
  - At Least Once 
  - At Most Once
---

**Exacly Once Delivery**

For many critical systems duplicate messages are inacceptable. The messaging system ensures that each message is delivered exactly once by filtering possible message duplicates automatically.

Upon creation, each message is associated with a unique message identifier. This identifier is used to filter message duplicates during their traversal from sender to receiver. [1]

<figure>
    <a href="/assets/images/exactly_once_delivery_sketch.png"><img src="/assets/images/exactly_once_delivery_sketch.png"></a>
    <figcaption>Exacly Once Delivery Sketch</figcaption>
</figure>

**At Least Once**

In case of failures that lead to message loss or take too long to recover from, messages are retransmitted to assure they are delivered at least once.

For each message retrieved by a receiver an acknowledgement is sent back to the message sender. In case this acknowledgement is not received after a certain time frame, the message is resend. [2] 

<figure>
    <a href="/assets/images/at_least_once_delivery_sketch.png"><img src="/assets/images/at_least_once_delivery_sketch.png"></a>
    <figcaption>At Least Once Delivery Sketch</figcaption>
</figure>


**At Most Once**

For each message handed to the mechanism, that message is delivered zero or one times; in more casual terms it means that messages may be lost. [4]

This post just copies and pasted the meanings from some sources by giving references. Hope it helps!


**References**

**[1]** http://www.cloudcomputingpatterns.org/exactly_once_delivery/

**[2]** http://www.cloudcomputingpatterns.org/at_least_once_delivery/

**[3]** https://www.linkedin.com/pulse/exactly-once-delivery-message-distributed-system-arun-dhwaj/

**[4]** https://stackoverflow.com/questions/44204973/difference-between-exactly-once-and-at-least-once-guarantees