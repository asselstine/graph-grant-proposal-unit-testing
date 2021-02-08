# Grant Proposal: Subgraph Unit Testing Framework

The Graph Protocol needs a subgraph unit testing framework to ensure mapping logic is correct.

The framework must allow developers to test their mapping logic against a known store state and against test fixtures (events).

Assertions can be made using a snapshot-style approach.

## User Stories

### As a user I want to hydrate the store with a certain state

Users must be able to hydrate the store with a known state of entities. Ideally both:

- Hydrate state programmatically using Entity objects
- Hydrate state using a JSON blob

### As a user I want to call a mapping function with an event

The user must be able to create an event Entity and pass it to a mapping function that is bound to the hydrated store.

### As a user I want to call all of the mappings with event fixtures

The user must be able to call the mappings with test fixtures.

- Fixtures could be set up programmatically as a list of Events
- Fixtures could be loaded from a JSON blob

### As a user I want to stub the state of a contract

Users must also be able to stub the state of a contract, so that if the contract is called certain data is returned.

- Stub contract state programmatically
- Stub contract state using JSON

### As a user I want to assert the state of the store

The user should be able to assert the final state of the store in a snapshot-style approach (compare output against expected).

- Must be able to assert entities
- Possibly assert entire state of store to assert non-existence as well

### As a user I want to assert a subgraph failure

The user should be able to assert that a subgraph fails in an expected way.

### As a user I want to see test run time durations

It could be useful to see how fast tests run.  The log output should include test run duration.

## Scaffolding CLI

It would be really nice to be able to generate hydration and fixture data from mainnet, testnets, or a local node. This would make it easy to generate test data from local nodes or testnets.

### As a user I want to generate hydration and fixture data between two blocks from a node

The user would be able to generate a JSON blob of store state for the starting block, and generate fixtures for the subsequent block up until the final block. This could be run against any node; whether local, testnet, or mainnet.

## Additional Requirements

### Language

The framework should be written in AssemblyScript or TypeScript.

### Performance

The framework should be fast: it should not spin up nodes or child processes.  The framework must stub out the store and test the mappings.
