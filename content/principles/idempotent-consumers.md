---
title: "Idempotent consumers"
draft: false
weight: 30
---

## Principle
**Consuming one or more messages (in the same order) more than once, leads to the same end state in the consumer.**

### Description
The receiver of a request performs an operation in such a way that it produces the same result even if it is performed multiple times. Thus, if the same message is received multiple times, the receiver will deal with it in a safe manner. In a consumer of messages, once all have been processed the last state received is the state of the system which is reflective of reality.

#### Consequences
* The consumer is responsible for the handling of duplicate messages to ensure the same end state is achieved.
* The consumer should never assume that a message will be produced once, and once only.
* The producer should help the consumer by including a [sequence number](/principles/messages-have-sequence-numbers) and the consumer should track these

### Example
* The receiver can use de-duplication and ignores the repeated message
* The receiver can safely reapply the operation with the exact same results that the previous delivery caused
* A consumer of messages may choose to track which messages have been processed and drop those which are duplicates
* A consumer of messages may apply all messages that come in and accept that it will store audit logs that indicate values being updated to themselves
* Event A (colour = red), event B (colour = blue), event C (colour = green), event B (colour = blue), event C (colour = green) leads to the colour being Green.

The state of the system is determined as follows:
```
Messages: A → B → C → A → B → C

System = A + B + C
```

## References
