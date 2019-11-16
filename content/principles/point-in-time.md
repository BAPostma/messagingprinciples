---
title: "Point in time"
draft: false
weight: 20
---

## Principle
**Messages only contain the current view of state and not include previous state (delta), rather they represent a state at a point in time.**

### Description

#### Consequences
* Consumers will have to determine the difference themselves based on the data that they have.
* Producers will not have to determine the difference before emitting the message. 

### Example
**Correct**
```js
MILEAGE_UPDATED_EVENT {
	mileage: 12345
}
```

**Incorrect**
```js
MILEAGE_UPDATED_EVENT {
	previous: 345
	current: 12345
}
```

## References
