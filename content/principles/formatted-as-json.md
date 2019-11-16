---
title: "Formatted as JSON"
draft: false
weight: 80
---

## Principle
**JSON is used as the format for all message payloads. It is not used for headers unless needed.**

### Description
This is a _sensible default_: JSON is used unless otherwise decided by a team and documented in a lightweight Architectural Decision Record (ADR) which is to be stored alongside the producer's code in the repository.

#### Consequences
* Producers will have to include **keys** and **objects** in JSON structures, even when that value is going to be null. Not including it, would break the schema and therefore the _contract_.
* Consumers have to accommodate deserialisation (unmarshalling) of the JSON structure into strongly-typed types in their codebase.
* Regardless of technology choices, message formats are widely compatible and lightweight enough to be processed quickly.

### Example
**Correct**
```js
MILEAGE_UPDATED_EVENT {
	mileage: 12345
}
```

**Incorrect**
```yaml
MileageUpdated:
	mileage: 12345
```

## References
