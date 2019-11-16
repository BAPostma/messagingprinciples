---
title: "Commands over APIs"
draft: false
weight: 50
---

## Principle
**The use of a message (command) to trigger another system into action is used instead of calling that system's API to trigger the action.**

### Description
This principle acts as a _sensible default_. The use of commands is preferred over calling APIs. When a target system is unavailable, it can start to process commands at the rate it so desires when it has reconnected to the broker. This reduces the need for [Circuit Breaker](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker) patterns and introduces the [Queue Based Load Leveling](https://docs.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling) architecture pattern.

#### Consequences
* For a producer, the triggering of another system becomes "fire and forget" by assuming reliable delivery of the command to the broker
* In the case of System A needing an immediate response from System B, an API may be beneficial since the response can be placed in the body
* Abundant use of commands over APIs helps an architecture to grow into being mostly asynchronous since there are no blocking API calls to be awaited
* Rollback scenario's can be triggered by a following command to "undo" the previous one. This is more difficult to implement when using API calls as the source system is unaware of the state of the target.

### Example
**Correct**
```json
ASSIGN_CAR_TO_SALES_CHANNEL_COMMAND {
	carId: 123
	channel: "Auction"
}
```

**Incorrect**
```
POST /api/AssignCarToSalesChannel?channel=Auction&carId=123
```

## References
