# Calculate distance on user devices

Date: 2022-11-06

## Status
Accepted

## Context

In order to support the requirement for notifying civilians about opportunities for an interaction with a nearby police officer, we need to periodically
calculate distances between each civilian and police officers with enabled location tracking. This could prove to be a performance issue for the platform
if a large number of concurrent users are searching for available interactions which is very probable, especially during larger events.

## Decision

Don't calculate distances between civilians and available police officers on the platform. Instead return the locations of all available police officers to the
civilian's device (mobile phone) and perform the distance calculations on it. If an available police officer is within the configured radius, notify the user
with a push notification.

Depending on the number of enrolled police officers, we can group their locations in grids and return only available police officers within that grid.

## Consequences

* By adopting this decision, we are offloading a lot of computing from our platform and onto the user's devices which will handle this easily.
* Since we are expecting a lot of requests for available police officer's locations, we will need to optimize that part of the platform and ensure the requests
are handled in an expected timeframe.
* The same decision can be applied to notifying civilians about nearby business locations.

