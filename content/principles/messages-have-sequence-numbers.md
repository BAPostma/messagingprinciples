---
title: "Messages have sequence numbers"
draft: false
weight: 40
---

## Principle
**Messages contain a sequence number in their header that assist to process them in the correct order.**

### Description
Time is not a reliable indicator for the correct ordering of messages in distributed systems, so a publisher should include a sequence number unless the broker can support this out of the box.

#### Consequences
* Producers need to manage the state of a counter which ensures an atomic increase of the sequence number
* When multiple producers are deployed (e.g. multiple pods for load balancing) the state counter may need to be shared amongst them
* A header will need to be added to all message types that are produced containing the counter

### Example
1. Insert `COUNTER=1000` into Redis cache
1. On production of an message read `COUNTER` from Redis cache
1. Set message header `SequenceNumber=1001`
1. Publish message to broker

## References
