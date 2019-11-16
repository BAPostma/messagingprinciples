---
title: "Support Schema Evolution"
draft: false
weight: 70
---

## Principle
**Message schema evolution will be enabled with a version number in the header such that a consumer can decide whether it is capable of processing a message.**

### Description
Message schema evolution or "versioning" is important from the start. With the version in the header, a consumer can peek at a message header without processing the message's contents. A consumer can decide to process the message later via a replay queue if it does not support the version of the schema yet.

#### Consequences
* Consumers won't have to contain if-else logic, extensive null-checks, etc. to handle variations in one type of message
* Consumer code bases can clearly indicate what code is responsible for different shapes of the same message types
* Teams producing messages will have to settle on a method for iterating on its versions
* New versions will cause consumers to have to update their processing capability. This needs to be communicated but will be visible by unprocessed messages sticking in the broker.
* Consumers will have to decide whether to keep messages in the queue or move them to a Dead-letter queue.

### Example
A sensible granularity for [versioning](/implementation-details/naming-conventions) is `MAJOR.MINOR`. A message header would contain:

* `schemaVersion: 1.4`

## References
