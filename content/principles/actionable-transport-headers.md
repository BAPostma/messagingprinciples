---
title: "Actionable transport headers"
draft: false
weight: 60
---

## Principle
**A consumer can make high-level decisions on the basis of a message's metadata, without processing the message and inspecting its contents**

### Description
Regardless of the transport mechanism for messages (e.g. a queue, topic or virtual topic, smtp, etc) the consumer should be able to make high-level decisions on the basis of a message's metadata, without processing the message and inspecting its contents.  

The minimum required headers are:

* `correlationId`
* `messageType`
* `schemaVersion`
* `sequenceNumber`

#### Consequences
* A publisher will add the `messageType` header to all emitted messages
* [Naming conventions](/implementation-details/naming-conventions) will be followed for `messageType` headers across the software estate
* A publisher will add the required headers but may omit [sequenceNumber](/principles/messages-have-sequence-numbers) etc. if it is not implemented yet

### Example
Any message would contain headers for:

* `correlationId: 97f81df5-4339-42aa-9dcb-a8d278ebeee1`
* `messageType: REGISTRATION_NUMBER_UPDATED_EVENT`
* `sequenceNumber: 98765`
* `schemaVersion: 1.4`

## References
See [this reference](https://docs.oracle.com/cd/E19509-01/820-2239/bpado/index.html) from Oracle on built-in JMS headers.