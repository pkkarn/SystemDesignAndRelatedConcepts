# Distributed Storage Solutions

Distributed storage solutions refer to the approach of storing data across multiple nodes, typically in a networked, distributed computing environment. These solutions provide several benefits over traditional, centralized storage models:

1. `Fault Tolerance`: In distributed storage, data is often replicated across multiple nodes. This replication increases data availability and protects against data loss. If one node fails, the system can retrieve the data from another node.

2. `Scalability`: As the amount of data grows, more nodes can be added to the network to accommodate it. This scalability is often more cost-effective than expanding a centralized storage system.

3. `Speed`: Distributed storage systems can potentially deliver data faster than centralized ones. This is because data is often stored geographically close to where it is used, and multiple nodes can deliver data simultaneously.

4. `Concurrency`: Multiple users or applications can access and work with the data simultaneously, enabling higher degrees of collaboration and efficiency.

Examples of distributed storage systems include distributed file systems like Hadoop's HDFS, distributed object storage like Amazon S3, and distributed databases like Google's Spanner or Apache Cassandra. However, each solution has its own set of trade-offs to consider, including consistency models, latency, and the complexity of managing a distributed system.

## SLA's

SLAs, or Service Level Agreements, are formally documented agreements between a service provider and a customer that clearly define the services provided, the standards by which the service will be measured, and the penalties or remedies if the service levels are not met.

SLAs are used across many industries, especially in IT services, telecommunications, and cloud computing. They usually include details about:

1. `Services`: The specific services provided by the service provider.

2. `Performance Metrics`: How the service performance will be measured, often in terms of availability, uptime, response times, etc.

3. `Responsibilities`: The responsibilities of both parties involved in the agreement.

4. `Penalties/Rewards`: The consequences if the service provider fails to meet the agreed-upon levels of service, or potentially rewards if service exceeds expectations.

5. `Dispute Resolution`: The mechanisms to resolve any disputes that arise in relation to the agreement.

Terms and Termination: The duration of the agreement and conditions under which it can be terminated.

By setting clear expectations about service levels, SLAs help to build trust and understanding between service providers and their customers. They also provide a basis for assessing service performance and addressing any service-related issues that arise.


Example: They can have 99% uptime in SLAs, which looks interesting but if you would calculate then you will find out it still 3.65 days of downtime in an agreement.


## Examples of Database Storage Solutions

1. `AWS S3`: 
- pay as you go
- different tiers
-- Hot - Fast as geographically located
-- Cool - bit slower but faster than cold
-- Cold - cheapest and take long than above

`Others`

2. Google Cloud Storage
3. Microsoft Azure