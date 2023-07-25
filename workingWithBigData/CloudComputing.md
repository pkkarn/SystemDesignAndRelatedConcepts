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