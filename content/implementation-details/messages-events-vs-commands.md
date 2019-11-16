---
title: "Messages: Events versus Commands"
weight: 20
---

## Differences
Aspect | Event | Command
:----- | :---- | :------
Contract | Producer of event determines & publishes schema | Producer of commands has an **agreed** contract with receiver
Contract testing | Consumers test against published schema | Subject to a contract which either party (producer & consumer) can test against
Relationship | Producer of an event has no knowledge of consumers | Producer of a command knows there is one and only one well known consumer
Language and tense | Events are verbs in the past tense | Commands are verbs in the present tense
Message payload | Contains the state that relates to the event, not an entire model or graph | Contains all parameters associated with the execution of the command
Dead-letter queue (DLQ) | Consumer has a private DLQ in its broker where it may store messages | Consumer is able to place the unprocessed command on a DLQ of the publisher's broker

## Similarities
**Sequencing**  
It is a burden upon any consumer to process messages in sequence whenever it has scaled horizontally


**Discriminant**  
It is a burden upon any producer to indicate the message intent of event notification or command invocation through a message header or message name

## References
