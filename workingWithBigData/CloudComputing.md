# Cloud Computing

### 1. Storage

When you have to store large amount of data somewhere, or when you are asked to process massive amount of data then you can use this service.

**Services**:

- AWS [S3]
- Google [Cloud Storage]
- Microsoft Azure [Disk, Data Lake, Blob]

### 2. Compute

Running any server like Ubuntu, Linux or in simple word what I used to think hosting...

**Services**:

- AWS [EC2]
- Google [Compute Engine]
- Microsoft Azure [Virtual Machines]

### 3. NoSQL

Each of these also offers their NoSQL database as well

**Services**:

- AWS [Dynamo DB]
- Google [Big Table]
- Microsoft Azure [CosmosDB]


```
Q: But mongodb is quite popular then why don't everbody use that if its NoSQL and underlying are same, instead of using DaynamoDB and CosmosDB

A: MongoDB is indeed a popular NoSQL database known for its ease of use and flexibility, but it's not the only solution in this space. DynamoDB, CosmosDB, and others have their unique strengths and features which make them better suited for specific use-cases or environments.

Here are some reasons why developers might choose DynamoDB, CosmosDB, or another NoSQL database instead of MongoDB:

1. **Integration with Cloud Platforms:** DynamoDB is provided by Amazon Web Services (AWS) and CosmosDB is provided by Microsoft Azure. If you're already using one of these cloud platforms for your applications, it might be easier and more efficient to use the NoSQL database service provided by that platform due to the tight integration.

2. **Performance at Scale:** While MongoDB performs well in a wide variety of situations, some developers find that DynamoDB or CosmosDB offers better performance for their specific workloads, especially at large scales.

3. **Pricing Models:** The pricing models for these services are different and can be complex. Depending on your usage patterns, one service may be more cost-effective than another.

4. **Global Distribution:** CosmosDB and DynamoDB offer built-in support for globally distributed, multi-region databases. This means that your data can be automatically replicated across different geographic regions for faster access and increased resilience.

5. **Managed Service:** Both DynamoDB and CosmosDB are fully managed services. This means you don't have to worry about the operational aspects of running your database like setting up and configuring servers, handling security patches, or managing backups. MongoDB offers this through MongoDB Atlas, but if you're self-hosting MongoDB, these tasks will fall on your shoulders.

6. **Serverless Applications:** Both DynamoDB and CosmosDB have native support for serverless architectures which can be a significant factor in certain use cases.

Remember, the "best" database for a given application will depend on the specific requirements and constraints of that application. There's no one-size-fits-all answer, and that's why we have such a diverse ecosystem of databases to choose from.
```


### 4. Containers

**Services**:

- AWS [Kubernetes/ ECR/ ECS]
- Google [Kubernetes]
- Microsoft Azure [Kubernetes]

Containers play a crucial role in system design and development for a variety of reasons, offering multiple advantages that streamline the software development process and enhance the efficiency and reliability of software deployments.

1. **Isolation and Consistency:** Containers encapsulate an application and its dependencies into a standalone unit, ensuring that the application runs uniformly irrespective of the differences in the environment (like development, staging, or production). This isolation can significantly reduce issues that arise from differences between development and production environments, a common problem known as "it works on my machine" issue.

2. **Portability:** Since containers include everything an application needs to run, they are highly portable. A developer can build a container on their local machine and then run it anywhere that supports containerization, such as different machines, cloud environments, or different operating systems.

3. **Efficiency and Scalability:** Containers are lightweight because they share the host system's kernel, which makes them more efficient in terms of system resources compared to traditional virtual machines. This efficiency makes it possible to run many containers on a single machine, and scale-out (add more containers) or scale-in (reduce containers) dynamically based on the workload. 

4. **Microservices Architecture:** Containers are an excellent fit for microservices-based architectures. Each microservice can be developed, deployed, scaled, and managed independently in its own container, thus improving the speed of continuous development, integration, and deployment processes.

5. **CI/CD Integration:** Containers fit well with continuous integration and continuous deployment (CI/CD) pipelines. They can be set up and torn down quickly, which is ideal for creating ephemeral environments for testing, and the container images provide a consistent environment from development to production.

6. **Security:** Although not a panacea, containers can offer an additional layer of security by isolating applications from each other and the host system. If an application in one container is compromised, the effects can be limited to that container.

7. **Ecosystem and tooling:** The rise of containerization has been accompanied by a rich ecosystem of tools (like Docker, Kubernetes) that help manage containers, orchestrate multi-container deployments, handle networking between containers, and manage storage, enhancing the overall benefits of using containers in system design.

In essence, the use of containers in system design promotes a more efficient, reliable, and agile software development and deployment process.


### 5. Data Stream

**Services**:

- AWS [Kinesis]
- Google [DataFlow]
- Microsoft Azure [Stream Analytics]

Amazon Kinesis is a set of services offered by Amazon Web Services (AWS) that allow you to process and analyze real-time, streaming data. The primary uses for Kinesis are:

1. **Real-time Analytics:** Kinesis enables real-time analytics on data as it arrives. For example, it can be used to analyze social media trends, system logs, market data, or any other information that needs to be processed in real-time.

2. **Ingestion of Large Data Streams:** Kinesis can be used to ingest massive volumes of data at high velocity, making it ideal for use cases like clickstream data processing, log data ingestion, and Internet of Things (IoT) scenarios.

3. **Data Lakes and Data Warehouse Feeding:** Kinesis can collect, process, and load data into AWS data stores such as S3, Redshift, and Elasticsearch. This enables further complex analytics and machine learning tasks over this data.

4. **Real-time Dashboard:** Kinesis can power live dashboards for real-time monitoring of data. For instance, operational metrics, financial trading information, social media trends, etc.

5. **Processing of Time-series Data:** Time-ordered data such as IoT sensor data, application logs, market data feeds can be handled efficiently with Kinesis, enabling users to analyze patterns over time.

6. **Event-driven Applications:** Kinesis is often used to enable event-driven programming by serving as the backbone for microservices communication, responding to changes in real-time.

The Kinesis suite comprises several services, including Kinesis Data Streams, Kinesis Data Firehose, Kinesis Video Streams, and Kinesis Data Analytics, each tailored to different use cases but all designed to handle massive, continuous data streams.

### 6. Spark/Hadoop

**Services**:

- AWS [EMR]
- Google [DataProc]
- Microsoft Azure [Databricks]

To Process large volume of data...


### 7. Spark/Hadoop

**Services**:

- AWS [EMR]
- Google [DataProc]
- Microsoft Azure [Databricks]


### 7. Data Warehouse

**Services**:

- AWS [RedShift]
- Google [BigQuery]
- Microsoft Azure [Azure SQL, Database]

### 8. Caching

**Services**:

- AWS [ElasticCache(Redis)]
- Google [MemoryStore]
- Microsoft Azure [Redis]