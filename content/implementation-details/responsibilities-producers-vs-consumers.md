---
title: "Responsibilities: Producers versus Consumers"
weight: 30
---

## Description
Aspect | Producer | Consumer
:----- | :------- | :-------
Contract | Defines, publishes | Codes against published schema
Contract Testing | Tests implementation against published schema | Tests implementation against published schema
Sequencing | Inserts sequence number | Reads and reorders, then processes
Versioning | Responsible evolution, deprecation | Stay up to date, process what you can, fail gracefully
Message Payload | Publishes all data in the contract | Reads & validates what it needs, forgives what it doesn't need

## References
