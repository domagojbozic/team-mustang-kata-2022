# Use redis for storing temporary locations

Date 2022-11-5

# Status

Accepted

# Context

In a system there is a requirement to store large amount of location data that has a short time to live period. For such storage we need automatic eviction policy of outdated data.

# Decision
Use redis as a storing unit for locations that are temporary with short time to live and expected to change frequently

# Consequences

## Positive
 * Very fast in memory data storage
 * Opens sourced - lowers costs
 * High availability and scalability

## Negative
* Requires a lot of memory
* Lack of redundant memory cosses lower performance