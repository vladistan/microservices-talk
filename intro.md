=! Microservices !=

==== Microservices ====

*<1-> What are the micro services?
*<2-> Where did they come from?
*<3-> Core principles
*<4-> Why should I bother?
*<5-> Challenges and pitfalls
*<6-> Good practices
*<7-> Pro-tips

=! Microservices : what's that?  !=

==== Microservices : what's that?  ====

*<1-> Post continuous delivery SOA
*<2-> Small !independently releasable! services,  that !work together!, modeled around a !business domain!.

=! Prehistoric technology !=

==== Prehistoric technology ====

*<1-> SOA
*<2-> Domain driven design
*<3-> Continous delivery

=! Case study !=

==== Case study ====

<<<WebSiteMockup.png,height=6cm>>>

==== Case study  ====

<[columns]

[[[0.6\textwidth]]]

<<<WebSiteMockup.png,height=4cm>>>

[[[0.6\textwidth]]]

* Catalog
* Recommendations / Promotions
* Shopping Cart
* Search
* Orders 
* RMA
* Customer Support

[columns]>


==== Application Composition : Monolith  ====

<<<AppCompositionTraditional.png,height=6cm>>>

==== Application Composition : Monolith  ====

<[columns]

[[[0.6\textwidth]]]

<<<AppCompositionTraditional.png,height=4cm>>>

[[[0.6\textwidth]]]

* Works most of the time
* Somewhat scalable
* Manageable up to a point
* All or nothing updates
* Tight coupling

[columns]>

==== SOA ====

*<1-> Break up application into set of independent services
*<2-> Add extra layers
**<2-> Integration Layer (ESB)
**<2-> Service Layer
*<3-> Rename existing layers
**<3->  Frontend $\rightarrow$ Consumer Interface Layer
**<3->  Database $\rightarrow$ Operational System
**<3->  Middleware $\rightarrow$ Business Process Layer

==== Application Composition : SOA  ====

<<<AppCompositionSOA.png,height=6cm>>>

==== Application Composition : SOA  ====

<[columns]

[[[0.6\textwidth]]]

<<<AppCompositionSOA.png,height=3cm>>>

[[[0.6\textwidth]]]

* Did well in some organizations
* Not so well in others
* Reasons for failure
** Conway's Law
** Ignoring CAP theorem
** Ignoring Fallacies of distributed computing

[columns]>


=! Conway's Law !=

==== Conway's Law ====

<[block]{}

organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations

\hspace*\fill{\small -- M. Conway}

[block]>

==== Conway's Law ====

<[center]
<<<AppCompositionSOA.png,height=4cm>>>
[center]>

organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations

=! Fallacies of distributed computing !=

==== Fallacies of distributed computing ====

* The network is reliable
* Latency is zero
* Bandwidth is infinite
* The network is secure
* Topology doesn't change
* There is one administrator
* Transport cost is zero
* The network is homogeneous

=! CAP Theorem !=

==== CAP Theorem ====

* Consistency
* Availability
* Partitioning ''tolerance''


=! Domain Driven Design !=

==== Domain Driven Design ====

*<1-> Bounded contexts
*<2-> Draw boundaries around business domains
*<3-> Do not partition system based on technology

=! Application Composition : Microservices !=

==== Application Composition : Microservices ====

<[center]
<<<AppCompositionMicroservices.png,height=7cm>>>
[center]>

==== Application Composition : Microservices ====

<[columns]

[[[0.6\textwidth]]]

<<<AppCompositionMicroservices.png,height=5cm>>>

[[[0.6\textwidth]]]

* Modeled around business domain
* Autonomous
* Hide implementation detail
* Decentralized
* Isolate the failure
* Highly observable
* Culture of automation

[columns]>

=! Microservices : Good Parts !=

==== Microservices : Good Parts ====

*<1-> Small and focused
*<2-> Independent
*<3-> Loosely coupled
*<4-> Allow try and pilot new tech
*<5-> Firm module boundaries
*<6-> Decentralized data

=! Why bother? !=

==== Why bother? ====

*<1-> Latest Buzzword
*<2-> All the cool kids are doing it
*<3-> !Probably, not good reasons!

==== Why bother? ====

*<1-> Faster dev cycles
*<2-> Team autonomy
*<3-> Smoother scaling


==== Challenges ====

*<1-> Complex runtime
*<2-> Distributed deployment
*<3-> Extensive communication
*<4-> Handling failures

==== Good practices ====

*<1-> Humane registries
*<2-> Team composition
*<3-> Isolate failures
**<4-> Fail fast
**<5-> Bulkheading
*<6-> Standardize communications
**<7-> REST or Message Queues
*<8-> Robust Service Discovery
*<9-> Consider something like Consul / Zookeeper / ETCd
*<10-> Monitor everything

==== Deployments ====

*<1-> Avoid huge build jobs
*<2-> One service per host
**<3-> Host is either physical host, VM or container
*<4-> Test
**<5-> Contract Tests
**<6-> Consumer driven development

==== Potential pitfalls ====

*<1-> Incorrect partitioning
*<2-> Distributed point of failure
*<3-> Misunderstanding your network


====  Refactoring to Microservices ====

*<1-> Strangler pattern
*<2-> Use static analysis tool to find natural boundaries
*<3-> Shadow systems


=! Personal Experiences !=

==== Monitor Everything ====

*<1-> Exception catchers
*<2-> Centralized log collections
*<4-> Synthetic transactions


==== Understand your networking ====

*<1-> Microservices increase network chatter
*<2-> More failures with UDP based protocols (DNS, discovery)
*<3-> More hiccups with TCP based protocols
*<4-> Run out of sockets
**<4-> Decrease TCP timeouts, seconds instead of minutes
*<5-> Batch the transactions.
**<5-> But can't have batching service


==== Robust CI/CD pipeline ====
*<1-> 1 Service = 1 Repo = 1 Build Job = 1 Artifact
*<2-> Instantaneous deployments
*<3->  Pre-build AMis, Containers
*<4-> Test coverage
*<5-> Consumer Driven Tests
**<6->  Avoid integration tests written by service devs
**<7->  https://github.com/realestate-com-au/pact


==== Consider using client side load balancing ====

*<1-> Service side load balancers create point of failure
*<2-> Hard to deploy and manage HW load balancers
*<3-> Problem of running out of sockets
*<4-> Netflix Ribbon Library https://github.com/Netflix/ribbon/wiki/Working-with-load-balancers


==== Never make MapReduce pipeline talk to service outside of your cluster ====

<<<HDFSAntiPattern.png,height=5cm>>>

==== Never make MapReduce pipeline talk to service outside of your cluster ====

<<<HDFSAntiPatternFix.png,height=5cm>>>

=! Further resources !=

==== Further resources ====


<<<ericevans-domaindrivendesign.jpg,height=6cm>>>



==== Further resources ====

<<<samnewman-microservices.jpg,height=6cm>>>


==== Further resources ====




* Toughtworks Youtube channel


=! ??? !=


=! Thank you !=



