## Chapter 5 Splitting the Monolith

* A major aim of the services we build is be highly cohesive and loosely coupled. The problem with monoliths (generalisation) is that they are the opposite of both.
* Seam - a portion of the code that can be treated in isolation and worked on without impacting the rest of the codebase.
* Bounded contexts make excellent seams, by definition they represent cohesive and yet loosely coupled boundaries in an organisation.
* We decompose our system by finding seams along which service boundaries can emerge, and this can be an incremental approach.
