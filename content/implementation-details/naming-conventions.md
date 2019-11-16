---
title: "Naming conventions"
weight: 10
---

## Description
### Values for the `messageType` header
* Events
	* past-simple tense name
	* use underscores for spaces
	* all capitals
	* suffix with `_EVENT`
* Commands
	* present-simple tense name
	* use underscores for spaces
	* all capitals
	* suffix with `_COMMAND`

#### Example
* `MILEAGE_UPDATED_EVENT` instead of `UPDATE_MILEAGE`
* `VEHICLE_HOME_COLLECTED_EVENT` instead of `HOME_COLLECTION_DONE`
* `ASSIGN_SALES_CHANNEL_COMMAND` instead of `SALES_CHANNEL_ASSIGNMENT`
* `DISPATCH_VEHICLE_V5_DOCUMENT_COMMAND` instead of `V5_DISPATCHED_ACTION`

---

### Values for the `schemaVersion` header
* Use the `MAJOR.MINOR` format
* `MAJOR` are considered breaking changes (e.g. field removals, renames or restructuring of hierarchy)
* `MINOR` are considered non-breaking changes (e.g. field additions, addition of new headers, formatting/indentation changes)

#### Example
* `schemaVersion: 12.3` instead of `version: 4`

## References
