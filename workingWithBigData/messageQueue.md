# Message Queues

Message queues are a core component in system design, especially in distributed systems, and they play a critical role in managing, coordinating, and reliably executing inter-process communications (communication between different services or components in a system). They function by collecting and storing messages from various sources and then making these messages available to be processed.

A message queue typically has the following properties:

1. **Decoupling**: Message queues decouple the sender and receiver. This means that the sender and receiver do not need to interact with the message queue at the same time. The sender can put a message onto the queue and then continue with its other processing. Meanwhile, the receiver can process the message when it is ready to do so.

2. **Asynchronicity**: The process of adding (sending) and removing (receiving) messages from the queue is asynchronous. Senders can add messages to the queue at their own rate, and receivers can process these messages independently.

3. **Reliability**: Message queues offer reliable communication. Even if the receiver fails temporarily, the message will be retained in the queue and can be processed when the receiver is back online. This is crucial for applications where data loss is not acceptable.

4. **Scalability**: By adding more workers (services or components that process the messages), you can easily scale the system. If there are a lot of messages in the queue, you simply add more workers.

5. **Ordering**: Some message queue systems guarantee the order of messages. For example, if message A is put in the queue before message B, message A will be processed before message B.

6. **Delivery semantics**: Message queues often support different types of delivery semantics, such as "at most once" (where messages are delivered once and duplicates are not allowed), "at least once" (where messages are assured to be delivered, but duplicates may occur), and "exactly once" (where messages are guaranteed to be delivered exactly once).

Common examples of message queue technologies include RabbitMQ, Apache Kafka, Amazon SQS, and Google Cloud Pub/Sub, each with its own set of features and capabilities. 

They are typically used in system architectures to enable event-driven or message-driven architectures, handle variable loads, ensure data is not lost due to system failure, and increase system responsiveness. They are also integral to microservices architectures, where independent services must communicate reliably.

### What it will be used for(Example")

Sure, let's consider a typical e-commerce website as an example. In this scenario, there are several components or services like User Interface, Order Management, Inventory Management, Payment Processing, Shipping, and Email Notification service. All these services need to interact with each other in a seamless and reliable manner.

Here's how a message queue could be used in such a system:

1. **Order Management and Inventory Management**: When a customer places an order, the Order Management service puts a message in the queue stating that an order has been placed. The Inventory Management service, which is subscribed to this queue, picks up the message and updates the inventory accordingly. This interaction can happen asynchronously, which means the Order Management service doesn't have to wait for the Inventory Management service to complete its process.

2. **Payment Processing and Email Notification**: When a payment is processed, a message could be added to the queue to notify the Email service to send a confirmation email to the customer. This decouples the Payment Processing service from the Email service. If the Email service goes down or experiences latency, the Payment Processing service can continue to process payments, and the emails will be sent when the Email service is back online.

3. **Order Management and Shipping**: Once an order is ready to be shipped, the Order Management system places a message in another queue. The Shipping service listens to this queue, and when it gets a message, it initiates the shipment. 

Using message queues in this manner provides several advantages:

- Each service operates independently and can be scaled according to its workload. For instance, if there's a sudden surge in orders, the Order Management service can be scaled up without affecting other services.

- It ensures data consistency and reliability. Even if a service goes down temporarily, the messages are retained in the queue and can be processed when the service is back online.

- It allows for better resource utilization and improved performance, as each service can operate and process messages at its own pace.

Remember, the above example is just one application. Message queues can be used in numerous other scenarios, from simple task queues for background processing, to complex systems for managing distributed transactions, and more.


[It's also known as pub/sub method]

### Examples:

- AWS SQS servoce(Cloud based)