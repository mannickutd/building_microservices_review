## Chapter 9 Security

### Authentication and Authorization

* Authentication is the process by which we confirm that a party is who they say they are.
* Authorization is the mechanism by which we map from a principal to teh action we are allowing them to do.

### Deputy problem

* 'Confused deputy problem' which in the context of service-to-service communication refers to a situation where a malicious party can trick a deputy service into making calls to a downstream service on his behalf that it shouldn't be able to.


### Securing data at rest

* Encrypt sensitive data at rest by default.
* Go with well known encryption protocols.
* Encryption is only as good as the access to the keys that encrypt it, encryption key management is just as important.
* Encrypt data when you first see it and decrypt on demand, don't store unencrypted data.
* Encrypt backups.

### Defense in depth

* Firewall, a good firewall will restrict access to certain ports, throttle connections from ip ranges and detect other sorts of malicious attacks.
* Intrusion detection systems (IDS), monitor networks, hosts for suspicious behaviour.
* Intrusion prevention systems (IPS), monitor systems and step in and stop malicious behaviour.
* Network segregation, virtual private clouds where hosts are allocated to different subnets act as another perimeter to add security measures.
* Operating system, the OS is heavily relied upon but is rarely written by the team/company who are responsible for the service. Patching and vulnerability checks should be automated.
