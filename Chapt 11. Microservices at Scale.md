## Chapter 11 Microservices at Scale

### Failure is everywhere

* Network fails, hard disks fail, software can fail etc.
* The more components the more likelihood one of those components is going to fail, failure becomes a statistical certainity at scale.
* Need to focus more on handling failure gracefully rather than only trying to prevent the inevitable from happening.

### What do you REALLY need

* Response time/latency, how long should various operations take? The number of concurrent connections?
* Availability, 24/7 uptime or periodical downtime? The SLA with the consumers needs to be known.
* Durability of data, how much data loss is acceptable? How long should the data be kept for?

With the above defined, you will need to measure them to maintain the agreed SLAs.

### Degrading functionality

* Resiliency includes the ability to degrade the functionality not only within a service but also across a distributed microservice environment.

### Architectual Safety Measures

* From an architectual point of view, you want to avoid minimal bad actors bringing down the entire architecture.
* "Strangler appliction", is where a new system intercepts calls made to a legacy applications and gradually replaces them one by one.
* "Cascading failure", is where a downstream service slowing starts bringing down other consumers around it until you have catastrophic failure.

### Antifragile organisation

* Simply planning for failure or building in redundancy is not enough for some organizations. Antifragile organizations actively incite failure on their system to replicate real life scenarios and allow teams to monitor how effectively they respond to failure events (Chaos Monkey). It is important to note that these events are practiced on production systems.
* Timeouts, appropriate defaults for checking downstream service health is an ever evolving problem. You don't want to wait to long before raising an appropriate error but also you don't want to preempt an unhealthy alarm before a problem actually exists.
* Circuit breakers, circuit breakers help localise and isolate the failure and allow upstream services to automatically continue paused calls until the isolated failure is fixed.

### Bulkheads

* On a ship, a bulkhead is a part of the ship that can be sealed off to protect the rest of the ship.
* Isolate yourself from complete failure.
* Circuit breakers are an automatic mechanism to seal a bulkhead, to not only protect the consumer from the downstream problem but also to potentially protect the downstream service from more calls that may be having an adverse impact.
* A good rule of thumb is to have circuit breakers for all synchronous downstream services.
* Load shedding, is the mechanism of redirecting traffic before a downstream circuit breaker is triggered.

### Idempotency

* Idempotent operations, the outcome doesn't change after the first application, even if the operation is subsequently applied multiple times.
* Idempotency becomes very useful if you have the ability to replay operations after a failure has been fixed.

### Scaling

* Go bigger, vertically scale the infrastructure you're using. This might mean, adding more ram, more cpu to instance nodes.
* Splitting workloads, microservices is one part of it, you may also want to decouple parts of an API for example where certain services handle different parts of the API, so you can scale services depending on usage of an API.
* Spreading the risk, don't put all of your eggs in one basket. Multiple microservices spread over multiple nodes over multiple AZs ... 

### Load balancing

* Load balances, distribute calls sent to them to one or more instances based on some algorithm, remove instances when they are no longer healthy, and hopefully add them back in when they are. They also support a dynamic scaling to running services, instances should be able to be added or removed from a load balancer for a particular service.
* Load balances can also handle certain operations that don't need to be handled at the service level, eg. SSL termination, inbound https requests are converted into http requests before sending to the instance.

### Starting again

* You should design for ~10x growth but plan a rewrite before ~100x.

### Scaling Databases

* Availability of service vs durability of data, all data written to the primary database gets copied to the standby replica database. If the primary goes down, my data is safe (durability of data) but without a mechanism to either bring it back up or promote the replica to teh primary, we don't have an available database, even though are data is safe.

#### Scaling for reads

* Read replicas can play an important role in not only keeping the data safe but also providing resiliency if one of the nodes goes down. Data consistency can play a role on how long stale data can be viewed, eventual consistency.
* Caching is another mechanism for scaling for reads.

#### Scaling for writes

* One approach is to use sharding, with sharding you have multiple database nodes. You take a piece of that data to be written, apply some hashing function to the key of the data, and based on the result of the function learn where to send the data.
* Sharding for writes may scale for write volume, but may not improve resiliency.
* Sharding increases the complexity from which reads and writes occur.

### CQRS

* Command-Query Responsibility Segregation, pattern refers to an alternate model for storing and querying information. With CQRS, part of teh system deals with commands, which capture requests to modify state, while another part of the system deals with queries.

### Caching

* Caching is a commonly used performance optimization whereby the previous result of some operation is stored, so that subsequent requests can use this stored value rather than spending time and resources recalculating the value.
* More often than not, caching is about eliminating needless round trips to databases or other services to serve results faster and reduce load on downstream systems.

#### Client side

* The client stores the cached result. The client gets to decide when (and if) it goes and retrieves a fresh copy. Ideally the downstream service will provide hints about what should (and how long) and should not be cached.

#### Proxy

* With proxy caching, everything is opaque to both the client and server. Squid and Varnish are good examples. Not specific to any one data/service type.

#### Server side

* With server side caching everything is opaque to the client. With a cache near or inside a service boundary, it can be easier to reason about things like invalidation of data, or track and optimize cache hits.

#### Keep it simple

* The more caches between you and the source of fresh data, the more stale the data can be, and the harder it can be to determine teh freshness of the data that a client eventually sees.


### CAP theroem

* Three things we can trade off against each other, consistency, availability, and partition tolerance.

#### Sacrificing consistency

* Sacrificing consistency, replication of data is not instantaneous. Systems that are happy to cede consistency to keep partition tolerance and availability are said to be eventually consistent, that is, we expect at some point in the future that all nodes will see the updated data but it won't happen at once so we have to live with the possibility that users see old data.

#### Sacrificing availability

* To keep consistency, each node needs to have a copy of the data it has is the same on every other node. Consistency across a distributed system is really hard.

#### Sacrificing partition tolerance

* Sacrificing partition tolerance means only having one store of the data itself. This is generally not an option for distributed systems.

### Service Discovery

* Services should have a point where they can let the world know where they are.
* Knowing where everything is allows you to monitor the system as a whole.
* Zookeeper, (originally developed as part of the hadoop project). It is used in a number of different use cases including configuration management, synchronizing data between services, leader election, message queues, and as a naming service. Zookeeper at its heart provides a hierarchical namespace for storing information.
* Consul, supports both configuration management and service discovery. It is more optimized for these key uses cases than zookeeper.

### Documenting Services

* Swagger, lets you describe your api using a yaml file. From this yaml file you can automatically create an example webserver for consumers to use before integrating with the real service.
* HAL, Hypertext Application Language is a standard that describes standards for hypermedia controls that we expose. Hypermedia controls are the means by which we allow clients to progressively explore our APIs to use our service's capabilities in a less coupled fashion than other integration techniques.
