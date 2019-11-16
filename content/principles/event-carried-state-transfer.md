---
title: "Event-carried state transfer (ECST)"
draft: false
weight: 10
---

## Principle
**Messages contain the state associated with the event in such a way that they don't need to contact the source system in order to do further work.**

### Description
This principle helps to avoid query-back ("skinny") messages, which contain too little information to be useful. Messages should be enriched ("fat") with enough data to provide all the details about the **event** not the **domain object** that it's related to.

#### Consequences
* A message does not contain the full state of impacted entities, rather just the data associated with the event.
* Where a consumer requires the latest state, there must also be guaranteed order of delivery. (E.g. Messages may arrive out of order resulting in processing using stale data)

### Example
A message that is sent after the domain event of a vehicle's registration number being updated, would contain enough information for the receiver.
* Skinny: "reg updated, here's an ARN"
* Too fat: "reg updated, here's the whole agreement, dealer information and information about the vehicle which happens to include a reg"
* Correct: "reg updated, here's an ARN as a unique identifier, here's the registration number that it was changed to"

## References
See for reference [stateful-event-pattern](http://www.grahambrooks.com/event-driven-architecture/patterns/stateful-event-pattern/) and [event-driven systems](https://martinfowler.com/articles/201701-event-driven.html). In domain-driven design, enriched messages are considered conducive to the autonomy of teams.