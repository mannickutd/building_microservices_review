## Chapter 7 Testing

### Testing quadrant

* Acceptance testing (business facing, support programming) - Did we build the right thing? Usually automated.
* Exploratory testing (business facing, critique product) - Usability; how can I break the system? Usually manual.
* Unit testing (technology facing, support programming) - Did we build it right? Usually automated.
* Property testing (technology facing, critique product) - Response time; scalability; performance; security tools.

### Testing pyramid

As you move up the pyramid, increasing scope and more confidence, testing time increases.
As you move down the pyramid, faster better isolation, testing time decreases.

* UI (top of the pyramid)
* Service (middle of the pyramid)
* Unit (bottom of the pyramid)

"One problem with this model is that terms mean different things to different people/teams. 'Service' is especially overloaded and there is many definitions of a unit test out there."

### Unit tests

* "These are tests that typically test a single function or method call. The tests generated as a side effect of test driven development (TDD). We're not launching services here, and are limiting the use of external files or network configurations."
* "The primary goal of these tests is to give us very fast feedback about whether our functionality is good."

### Service tests

* "Service tests are designed to bypass the user interface and test services directly... For a system comprising a number of services, a service test would test an individual service's capabilities."
* External collaborators should be stubbed out, if they are needed for the test the testing time can be increased significantly.

### End to end tests

* "End to end tests are tests rn against your entire system. Usually mimicking interaction/user behaviour."

### Tradeoffs

* How many, usually an order of magnitude going down the pyramid, eg. 10, 100, 1000.
* Service tests, how to stub the external collaborators and keep the stubs consistent/inline with the actual service it is stubbing. Maintaining the canned responses can become as big a task as maitaining the tests themselves.
* Which team is responsible for maintaining all of the stubs? the consumer/owner of the service? https://docs.pact.io/
* Ideally end to end tests should be run whenever we are deploying a new service candidate.
* End to end tests tend to be very flaky and brittle, the larger the ecosystem of microservices the more moving parts there is. All these moving parts can introduce flaky and brittleness to the end to end tests with a 'sometimes' failing test suite.
* End to end tests can take a long time to execute which limits how quickly the feedback loop a developer can respond.
* Blue/green deployment is a post deployment release testing technique. Test a service after it has been released.
* Mean time to repair vs mean time between failures important metrics to look at from a team perspective.

### Summary

* "Optimize for fast feedback, and separate types of tests accordingly."
* "Avoid the need for end-to-end tests wherever possible by using consumer-driven contracts."
* "Use consumer-driven contracts to provide focus points for conversations between teams."
* "Try to understand the trade-offs between putting more effort into testing and detecting issues faster in production; optimize for MTBF vs MTTR."


