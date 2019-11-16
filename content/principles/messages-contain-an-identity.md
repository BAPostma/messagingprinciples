---
title: "Messages contain an identity"
draft: false
weight: 90
---

## Principle
**A message contains an identity (e.g. a unique identifier) for the entity that it relates to in the originating system.**

### Description
Messages should always contain a field such as a unique identifier. This can be used (when needed) to retrieve more information by querying the originating system or - by being stored in the consumer - for future reference. They do not necessarily have to be globally unique within the distributed system.

#### Consequences
* Producers are required to introduce a key-value pair such to hold an identifier
* Producers prefer to use their own unique identifier for the "(aggregate) root" entity, not one from another system
* Consumers may want to store such unique identifiers or use them as a unique identifier themselves; with caution as the autonomy of systems needs to be maintained

### Example
**Correct**
```json
CHERISHED_PLATE_ATTACHED_EVENT {
	vehicleId: 12345,
	registrationNumber: "BR3NDA"
}
```

**Incorrect**
```json
CHERISHED_PLATE_ATTACHED_EVENT {
	arn: 56789
	registrationNumber: "BR3NDA"
}
```

## References
