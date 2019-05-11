## Chapter 1 Microservices

* Microservices are small autonomous services that work together.
* Microservice characteristics:
  1. Cohesion - the drive to have related code grouped togther.
  2. Focus the service boundary on business boundaries, making it obvious where code lives for a given piece of functionality.
  3. Jon Eaves "Can be re-written in two weeks."
  4. Sam Newman "Small enough but no smaller."
  5. Separate entity, deployed as an isolated service on a platform as a service.
  6. Isolation adds overhead but drastically simplifies building and managing a distributed system.
  7. All communication between the services is via network calls. Enforces separation and avoids tight coupling.
  8. You need to be able to deploy a service without deploying or affecting any other service.
* Microservice benefits:
  1. The system is composed of multiple, collaborating services, developers have freedom to use the right technology for the service regardless of the existing technologies used.
  2. There are overheads with embracing new technologies for different parts of the architecture, it is about finding the right balance to embracing new technologies and leveraging tools and knowledge of existing and common technolgies.
  3. Resilience engineering is the bulkhead. If one component of a system fails, but that failure doesn't cascade, you can isolate the problem and the rest of the system can carry on working. Service boundaries become obvious bulkheads.
  4. Having isolated services, architecture scales each component independently.
  5. Isolated services allows each service to be deployed independently, supports best practices with CI/CD.
  6. Organizational alignment, smaller teams working on smaller codebases tend to be more productive.
  7. Composability, opportunity for reuse of functionality without coupling the codebases.
  8. Optimizing services for replacement. Codebases can decay very quickly.
* Service Orientated Architecture (SOA) is a design approach where multiple services collaborate to provide some end set of capabilities.
* Microservices is an approach to SOA similar to scrum is an approach to agile software development.
* Shared libraries is another decompositional technique which most developers and languages have a very clear understanding of.
* Microservices are not a silver bullet. They come with all the associated complexities of distributed systems.
