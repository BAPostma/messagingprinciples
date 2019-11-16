---
title: "Messages are Domain Events"
draft: false
weight: 80
---

## Principle
**Emit domain events instead integration events which represents a state change to multiple entities or aggregates inside the domain.**

### Description
Use _domain events_ over _integration events_. The difference being that a domain event represents a state change to multiple entities or aggregates inside a domain (i.e. business concepts). Therefore, it does not represent the fact that an entity (e.g. database model) itself was updated. The consumer of the event may not hold the same entity in its codebase and be unaware.

#### Consequences
* Producers are responsible for the articulation of an event that has happened. An updated entity may lead to multiple attributes being updated, which could each become a domain event.
* Consumers need to support partial updates to their entities/domain model after receiving an event that indicates one of its attributes has changed.

### Example
In the example, the current mileage of a vehicle is updated - which is a domain event "mileage updated". The fact that therefore the vehicle model that holds the mileage attribute has changed, is of no relevance to the consumer of a message.

**Correct**
```json
NEW_MILEAGE_READ_EVENT {
	mileage: 12345,
	date: 2019-01-01
}
```

**Incorrect**
```json
VEHICLE_UPDATED_EVENT {
	colour: "black",
	mileage: 12345
}
```

## References
See for reference [this article](https://docs.microsoft.com/en-us/dotnet/standard/microservices-architecture/microservice-ddd-cqrs-patterns/domain-events-design-implementation#domain-events-versus-integration-events) that explains the difference well.