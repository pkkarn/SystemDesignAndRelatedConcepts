# Resilience

Resilience in system design refers to the ability of a system (typically an IT system like an application or infrastructure) to function and recover quickly from failures or disruptions, be they minor or significant. This includes failures caused by system overload, infrastructure issues, human error, or even deliberate attacks such as DDoS attacks.

There are several principles and techniques used to build resilience into a system:

1. `Redundancy`: Having backup components or systems that can take over if the primary ones fail. For example, maintaining multiple servers that can handle the same tasks so if one goes down, the others can take over.

2. `Fault Tolerance`: The ability of a system to continue operating even when some of its components fail. This involves designing the system in a way that it can automatically detect and isolate faults without causing the whole system to fail.

3. `Autoscaling`: In cloud computing, autoscaling allows systems to handle increases in workload by automatically adding resources when they're needed, and scaling back when they're not. This helps ensure the system can handle traffic spikes without crashing.

4. `Load Balancing`: Distributing workload across multiple servers or resources to ensure no single resource becomes a bottleneck, which can improve resilience and availability

5. `Failover Processes`: These are procedures that allow a system to switch over automatically to a standby system when the main system fails.

6. `Regular Testing`: Regularly testing your system for potential faults and running "failure drills" can help ensure the system can recover quickly from a failure when it happens.

7. `Monitoring and Alerting`: Implementing effective system monitoring and alerting to detect issues as soon as they happen, and before they cause significant problems. This allows for quick reaction to prevent larger issues.

8. `Microservices Architecture`: Designing applications as a collection of small, independent services can help ensure that a failure in one service does not directly impact others.

## What happens in case if something goes down
