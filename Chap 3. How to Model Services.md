## Chapter 3 How to Model Services

* What makes a good micro service?
  1. Loose coupling - The whole point of a microservice is being able to make a change to one service and deploy it, without needing to change any other part of the system.
  2. High cohesion - We want behaviour to sit together and unrelated behaviour to sit elsewhere. 
  3. The bounded context - The idea is that any given domain consists of multiple bounded contexts, and residing within each are things that do not need to be communicated outside as well as things that are shared externally with other bounded contexts. Each bounded context has an explicit interface, where it decides what models to share with other contexts.
  4. Modules and services - Modular boundaries (derived from bounded contexts) become excellent candidates for microservices.
  5. Premature decomposition - "We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%.". If you do not have a good understanding of the boundaries where a domain exists do not commit to early boundaries that you decide upon.
  6. Business capabilities - try to avoid thinking of bounded contexts in terms of the data but rather the capabilities those contexts provide the rest of the domain.
  7. Turtles all the way down - When considering the boundaries of your microservices, first think in terms of the larger, coarser-grained contexts, and then subdivide along these nested contexts when you're looking for the benefits of splitting out these seams. Align with organizational structure when choosing a nested or full separation approach.
  8. Communication in terms of business concepts - The modelling of your software after your business domain shouldn't stop at the idea of bounded contexts. The same terms and ideas that are shared between parts of your organisation should be reflected in your interfaces. It can be useful to think of forms being sent between microservices, much as forms are sent around an organisation.
  9. The technical boundary - making decisions to model service boundaries along technical seams isn't always wrong. Using the reason of performance objectives of a bounded context should not be the primary driver rather a secondary one.
