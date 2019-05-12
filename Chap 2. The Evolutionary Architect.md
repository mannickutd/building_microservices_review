## Chapter 2 The Evolutionary Architect

* "Architects have an important job. They are in charge of making sure we have a joined up technical vision, one that should help us deliver the system our customers need."
* Architects need to shift there thinking away from creating a perfect end product (for a moment in time) and instead focus on helping create a framework in which the right systems can emerge and continue to grow as we learn more.
* More accurate analogies can be drawn with city planners rather than engineers and architects in more traditional industries. A town planners role is to look at a multitude of sources of information and then attempt to optimize the layout of a city to best suit the needs of citizens today, taking into account potential future use. A town planner does their best to anticipate changes but accepts that trying to exert direct control over all aspects of what happens in futile. 
* For software architecture what are the zones? The zones relate to the service boundaries or perhaps the course grained groups of services. As architects you are less worried about what happens inside zones but rather how zones communicate effectively. Ensuring the overall health of the system is balanced and maintained.
* The coding architect - If an architect is to ensure the zone is habitable for all stakeholders (developers, users, operations) they need to feel the impact of their decisions. At the very least this means spending time with the different groups to understand the lower level problems theyre encountering.
* A great way to help frame our decision making is to define a set of principles and practices that guide it, based on the goals we're trying to achieve.
  1. Strategic goals, this should speak of where the company is going (probably from the PM department or higher) and how it sees itself as best making its customers happy. These will be high level goals that might not even include technology. The architect has a role to align the technology with the strategic goals.
  2. Principles, are rules that you have made in order to align what you're doing to some larger goals. Fewer than 10 is usually a good number.
  3. Practices, are how we ensure are principles are being carried out. They are a set of detailed, practical guidance for performing tasks. They will often be technology specific, and should be low level enough that any developer can understand them.
  4. Required standard, one of the key ways to ensure what should be constant from service to service is to define what a good service looks like. There are some common characteristics that well behaved services should exhibit.
  5. Ben Christensen "It needs to be a cohesive system made of many small parts with autonomous lifecycles but all coming together."
  6. Monitoring, it is essential to draw up coherent, cross service views of the systems views. All services should support a consistent approach to recording (pushing) health metrics to a central location.
  7. Interfaces, picking a small number of well defined interface technologies.
  8. Architectual safety, we cannot have one badly behaved system ruin the party for everyone. We have to code, architect for failure of services within the system, as well as the network itself. Building in circuit breakers is a wise choice to handle spikes or unintended usage of the system. Being consistent with HTTP codes for example, if all services are being consistent it is much easier to manage the health of different parts of the system.
  9. Goverance through code, defining and agreeing upon standards is one thing, making sure everyone abides by the rules is another. Exemplars and service templates go along way to helping developers achieve what you want.
  10. Technical debt, is about incurring short term benefit with incurring a cost to operate or refactor the service later on. Part of an architects job is about ensuring that the right balance is achieved.
  11. Exception handling, if enough exceptions are found it may reflect a new understanding of the world.
  12. Governance and leading from the center, "Governance ensures that enterprise objectives are achieved by evaluating stakeholder needs, conditions and options; setting direction through prioritisation and decision making; and monitoring performance, compliance and progress against agreed-on direction and objectives.
  13. Building a team, much of the role of the technical leader is about being part of the team that will help build out the vision. Architects are an active participant in shaping and implementing the vision.
* Core responsibilities of the evolutionary architect:
  1. Vision - Ensure there is a clearly communicated technical vision for the system that will help your system meet the requirements of your customers and organisation.
  2. Empathy - Understand the impact of your decisions on your customers and colleagues.
  3. Collaboration - Engage with as many of your peers and colleagues as possible to help define, refine, and execute the vision.
  4. Adaptability - Make sure that the technical vision changes as your customers or organisation requires it.
  5. Autonomy - Find the right balance between standardizing and enabling autonomy for your teams.
  6. Governance - Ensure that the system being implemented fits the technical vision.
