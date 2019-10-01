## Chapter 6 Deployment

* Continuous integration, regular check in code, verify the checked in code works, build an artifact once and deploy the artifact in the dev environment.
* CI with microservices, CI builds artifacts for individual microservices. The goal is to be able to build and deploy a service independently of the other services.
* Continuous delivery, is the approach whereby we get constant feedback on the production readiness of each and every check-in, and furthermore treat each and every check-in as a release candidate.
* Focus on maintaining the ability to release one service independently. One CI build per microservice if you want to deploy them separately.
* Move to containerised services, where you have one service per container.
* Culture of automation is the key to managing multiple services.
