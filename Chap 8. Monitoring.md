## Chapter 8 Monitoring

### Increased complexity

* With multiple independent autonomous services comes increased complexity in determing as a whole which parts of the service are bottlenecks or points of failure.
* Multiple services over multiple servers means request tracking and log debugging becomes vital.

### Metrics

* Service metrics, each service should be exposing metrics relating to its health.
* Metric tracking across multiple services to expose the health of the system as a whole.
* HTTP Error codes are a good start but can only give an indication of when there is a problem.

### Cascading

* Services that then cause upstream errors can complicate error diagnoses.
* Each service instance should check its downstream dependencies on its own healthcheck.

### Standardization

* Standardization for individual services about how and what is being monitored becomes very important to manage a microservice environment. 

### Summary

* For each service
  1. Track inbound response time at a bare minimum. Once you've done that, follow with error rates and then start working on application-level metrics.
  2. Track the health of all downstream responses, at a bare minimum including the response time of downstream calls and at best tracking error rates.
  3. Standardize on how and where metrics are collected.
  4. Log into a standard location, in a standard format if possible. Aggregation is a pain if every service uses a different layout.
  5. Monitor the underlying operating system so you can track down rogue processes and do capacity planning.
* For the system
  1. Aggregate host-level metrics like CPU together with application-level metrics.
  2. Ensure your metric storage tool allows for aggregation at a system or service level, and drill down to individual hosts.
  3. Ensure your metric storage tool allows you to maintain data long enough to understand trends in your system.
  4. Have a single, queryable tool for aggregating and storing logs.
  5. Strongly consider standardizing on the use of correlation IDs.
  6. Understand what requires a call to action, and structure alerting and dashboards accordingly.
  7. Investigate the possibility of unifying how you aggregate all of your various metrics by seeing if a tool like Suro or Riemann makes sense for you.
