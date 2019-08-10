## Chapter 4 Integration

* Looking for ideal integration technologies:
  1. *Avoid breaking changes*, use technologies that allows you to change with the environment.
  2. *Keep your APIs technology agnostic*, the one certainty is change, keep the API's used to talk between microservices technology agnostic.
  3. *Make the service simple for consumers*, perhaps there is a need for a client library to be provided. Documentation is a must.
  4. *Hide internal implementation detail*, if the consumer needs to understand internal implementation this will lead to coupling. Changes on the server side shouldn't impact consumers except for major version changes.
* Simple CRUD operations are usually not sufficient for enterprise services.
* Avoid sharing a DB for multiple services. The DB table will couple the implementation of the of the data model to every service which works with that table.
* Synchronous vs Asynchronous, synchonous -> request/response, asynchronous -> event based. Event based is more decoupled in its nature but relies on clients synchronizing on multiple events. Synchonous is easier to reason and understand for consumers.
* Orchestration vs choregraphy, more and more complex logic in the business process means the logic is spread out over the multiple services. In general, systems that tend more toward the choregraphed approach are more loosely coupled, and are more flexible and amenable to change. There is more work to monitor and track processes across system boundaries.
* Remote procedure call refers to a technique of making a local call and having it execute on a remote service somewhere. Many implementations are binary in nature, make appear that the work in happening locally.
* Local calls are not like remote calls. The core idea of RPC is that the complexity is hidden in the remote call. Local calls don't have the same costs associated with them. Latency/response times, marshalling and unmarshalling payloads can all be costly. The network can be unreliable and in the worst case scenario the developer will not know if they're making an external call.
* Vendor/language specific implementations of RPC can end up being very brittle and lock in surrounding services to using the same vendor/language because of its brittleness (in disguise for ease of integration).
* Beware too much convenience, short term gain over long term pain and coupling of layers of an application can be hard to unwind after the decision to couple them is made.
* Implementing Asynchronous Event-Based collaboration:
  1. Two main problems, a way for our microservices to emit events and a way for consumers to find those events that happened.
  2. Traditionally message brokers have been designed to handle both problems RabbitMQ and Kafka are no exception.
  3. These systems are designed to be scalable and resilient but doesn't come for free, you can incur higher development and operation costs.
  4. Be wary of moving smarts from endpoints to middleware. Middleware should be dumb.
* Complexities of Asynchronous Architectures:
  1. Event driven architectures seems to lead to significant more decoupled, scalable systems.
  2. Programming style leads to increase in complexity.
  3. Bugs can creep in leading to catastropic failover, good montioring and event flows through the system should be given careful consideration.
* DRY - (sometimes simplified to don't duplicate code) avoid duplicating our system behaviour and knowledge. One of the things we want to avoid is overly coupling a microservice and consumers such that any small change to the microservice itself causes unnecessary changes to the consumer.
* Versioning:
  1. Defer breaking changes for long as possible.
  2. Postel's Law (robustness principle) "Be conservative in what you do, be liberal in what you accept from others."
  3. Catch breaking changes early.
  4. Use semantic versioning.
  5. Coexist different endpoints.
* Backends for frontends:
  1. The same team that is handling the UI experience also handles the backend integration with the separate decomposed server-side services.
  2. Be sure that this layer doesn't contain logic. These BFF's should only contain behaviour specific to deliverying a particular user experience.
