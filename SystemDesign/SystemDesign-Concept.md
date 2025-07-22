## What is **DDD?**

Benefits of DDD in System DesignBusiness Alignment: The software reflects real-world business processes, improving usability and relevance.

Clear Communication: Ubiquitous language reduces misunderstandings between technical and business teams.

Flexibility: Modular bounded contexts allow the system to adapt to changing business requirements.

Maintainability: Clear boundaries and encapsulated logic make the codebase easier to maintain and evolve.

## **CQRS**(Command **Query **Responsibility**Segregation)**

CQRS (Command Query Responsibility Segregation) is a design pattern that separates the read and write operations of a system into two distinct models:

Command: Handles write operations (e.g., creating, updating, or deleting data). Commands modify the system’s state and typically don’t return data.
Query: Handles read operations (e.g., fetching data). Queries retrieve data without modifying the system’s state.

## GRPC

gRPC is a high-performance, open-source framework for remote procedure calls (RPC) developed by Google. It uses HTTP/2 for transport, Protocol Buffers (Protobuf) for efficient data serialization, and supports multiple programming languages. gRPC is designed for low-latency, scalable, and distributed systems, making it ideal for microservices, mobile apps, and real-time communication.**Key features:* Bidirectional streaming: Supports client-streaming, server-streaming, and bidirectional streaming.

* Strong typing: Uses Protobuf for defining service contracts, ensuring type safety.
* Efficient: Binary serialization reduces payload size compared to JSON/XML.
* Language support: Includes C++, Java, Python, Go, Node.js, and more.
* Authentication: Supports TLS and token-based authentication.

Use cases:* Microservices communication

* Real-time data streaming
* Cross-platform APIs

To get started, define a .proto file with your service and message definitions, compile it using a Protobuf compiler, and implement the client and server logic in your preferred language.

# NGINX

NGINX is a high-performance web server, reverse proxy, and load balancer known for its speed, stability, and low resource usage. It’s widely used for serving static content, proxying requests to application servers, and handling tasks like caching, load balancing, and SSL termination.

# N8N

n8n (pronounced "n-eight-n") is an open-source, low-code workflow automation platform that allows users to connect and automate tasks across various applications and services. It uses a node-based interface where "nodes" represent actions (e.g., sending an email, updating a spreadsheet, or fetching data from an API) that are linked to form workflows triggered by specific events. It supports over 400 integrations with tools like Google Sheets, Slack, and OpenAI, and offers flexibility for both no-code visual building and custom JavaScript/Python coding for advanced tasks.

# Forward Proxy

A forward proxy is a server that sits between a client (e.g., a user's device) and the internet, acting as an intermediary to forward client requests to external servers and return the responses. It’s typically used to enhance privacy, security, or control access.

# Reverse Proxy

A reverse proxy is a server that sits between external clients (e.g., users on the internet) and internal servers, forwarding client requests to the appropriate backend server and returning the server’s response to the client. It’s used to enhance security, performance, and scalability of web services.

## Repository Pattern

The Repository Pattern is a design pattern commonly used in software engineering to provide a clean and maintainable way to access and manage data between the business logic and the data storage layer (e.g., a database). It acts as an abstraction layer, decoupling the application’s business logic from the data access logic, making the codebase more modular, testable, and maintainable.

## Unit of Work

* Unit of Work: Acts as a coordinator that tracks changes to objects (e.g., insertions, updates, deletions) during a business transaction and commits them to the data store as a single unit. If any operation fails, the entire transaction is rolled back.
* Atomicity: Ensures that all changes are either fully applied or not applied at all, preventing partial updates.
* Change Tracking: Monitors changes to objects (e.g., entities in an ORM) and determines what needs to be persisted.
* Transaction Management: Manages database transactions, ensuring consistency and reducing the need for manual transaction handling in the business logic.
* Collaboration with Repositories: The Unit of Work typically works with one or more repositories, coordinating their operations to persist changes to the database.

Components1. Unit of Work Interface: Defines methods like commit, rollback, and methods to access repositories.

1. Concrete Unit of Work: Implements the interface, managing the transaction and coordinating with repositories.
2. Repositories: Used by the Unit of Work to perform CRUD operations on specific entities.
3. Data Context: Represents the connection to the data store (e.g., a database session in an ORM like Entity Framework or Hibernate).

## FAULT Tolerance

## Polly

## Circuit Breaker

## Caching

## Rate Limiting

## API Gateway

## Load Balancer

## WebHook

## Idempotent API

# What are solid principles ?

S- Single responsibility - Each class should have single job/responsibility.
O - Open/Closed Principle. Classes must be open to extension but closed to modification.
L - Liskov principle - If class A is subtype of class B then, Class B should be able to replace Class A with out disrupting the behaviour of our program.
I - Interface segregation - Clients should not be forced to depend on methods that they do not use.
D - Dependency inversion - High level modules should not depend on low level modules. Both must depend on abstraction.

# What are DRY, YAGNI, KISS principles ?

DRY- Do not repeat yourself.
Avoid duplication. Makes the software more maintainable and less error-prone.

YAGNI - You are not going to need it.
Avoid unnecessary features/functionalities to the software. This helps software focussed on essential requirements and makes it more maintainable.

KISS: Keep the implementation simple,stupid.
Keeping the software design and implementation as simple as possible.
This make software more understandable,maintainable and testable.

## Facade Design Pattern

The Facade Design Pattern is a structural pattern that provides a simplified interface to a complex system of classes, libraries, or frameworks. The primary goal of the Facade pattern is to present a clear, simplified, and minimized interface to the external clients while delegating all the complex underlying operations to the appropriate classes within the system. The Facade (usually a wrapper) class sits on the top of a group of subsystems and allows them to communicate in a unified manner.

As the name suggests, Facade means the Face of the Building. Suppose you created one building. The people walking outside the building can only see the walls and glass of the Building. The People do not know anything about the wiring, the pipes, the interiors, and other complexities inside the building. That means the Facade hides all the complexities of the building and displays a friendly face to people walking outside the building.

##### Understanding Facade Design Pattern in C# with one Real-Time Example:

* Identify Complex Subsystems: First, identify the complex parts of your system that need simplification. These could be complex libraries or systems with multiple interacting classes.
* Create a Facade Class: Design a facade class that provides a simple interface to the complex subsystems.
* Delegate Calls to Subsystems: The facade should delegate the client requests to the appropriate objects within the subsystem. The facade should handle all the intricacies and dependencies of the subsystems.
* Client Code Interaction: The client interacts with the system through the facade, simplifying its use of the complex subsystems.

## SAGA Pattern

## Cheorgphy

## Orchestration

## Strangler Pattern

The Strangler Pattern (or Strangler Fig Pattern) is a software engineering approach used to incrementally replace an existing system (often a legacy system) with a new one. Instead of a complete, high-risk rewrite, the pattern involves gradually building new functionality around the edges of the old system, slowly "strangling" it until the legacy system is fully replaced or significantly reduced.

## CAP theorem

## HLD and LLD

## Distributed locking system

## Apache Kafka

## Zookeeper

## Pub/Sub System

## CDN

A Content Delivery Network (CDN) is a geographically distributed network of servers that cache and deliver content to users from locations closest to them. The goal is to enhance the speed, reliability, and availability of content delivery while reducing latency and network congestion. CDNs store copies of static content (e.g., videos, images, web pages) on edge servers located at Internet Exchange Points (IXPs) or within Internet Service Provider (ISP) networks. By serving content from nearby servers, CDNs minimize the distance data travels, improving load times and user experience. They also reduce bandwidth costs, enhance redundancy, and provide security benefits like DDoS mitigation

## Event Sourcing

Event sourcing is a design pattern in software engineering where an application's state is derived by storing and replaying a sequence of events, rather than storing the current state directly. Each event represents a state change, capturing what happened, when, and why. These events are stored in an event log, which serves as the single source of truth.**Key Concepts:1. **Events as the Source of Truth**: Instead of updating a database with the current state (e.g., updating a user's balance in a table), you append immutable events (e.g., "UserDepositedMoney: $100") to an event store.

1. **Rebuilding State**: The application's current state is computed by replaying all relevant events in order. For example, to determine a user's account balance, you sum all deposit and withdrawal events.
2. **Immutability**: Events are never modified or deleted; they are appended to the log, ensuring a complete audit trail.
3. **Event Store**: A specialized database or log that stores the sequence of events, optimized for appending and retrieving events.

## ElasticSearch

## AutoScaling

## WebSocket

## Vertical Scaling and Horizontal Scaling

Vertical Scaling and Horizontal Scaling are two approaches to improving the performance and capacity of a system, particularly in the context of computing, databases, or application infrastructure. Here's a concise explanation of each:Vertical Scaling (Scaling Up)* Definition: Increasing the capacity of a single server or machine by adding more resources, such as CPU, RAM, storage, or processing power.

* How it works: You upgrade the existing hardware or replace it with a more powerful machine to handle increased load.
* Examples:
  * Adding more RAM to a database server.
  * Upgrading to a faster CPU or increasing disk space on a single machine.
* Advantages:
  * Simpler to implement, as it typically requires no changes to the application architecture.
  * Lower latency since all resources are on a single machine.
  * Often easier to manage for smaller systems.
* Disadvantages:
  * Limited by the maximum capacity of a single machine (hardware constraints).
  * Can be expensive, as high-end hardware costs grow exponentially.
  * Single point of failure; if the machine goes down, the entire system is affected.
  * Scaling has a ceiling (e.g., you can’t infinitely add RAM or CPU).

Horizontal Scaling (Scaling Out)* Definition: Increasing system capacity by adding more machines or nodes to distribute the workload across multiple servers.

* How it works: You add more servers to a cluster, and the workload is balanced across them, often using load balancers or distributed systems.
* Examples:

  * Adding more web servers to handle increased traffic.
  * Distributing database queries across multiple nodes in a cluster (e.g., sharding or replication).
* Advantages:

  * Virtually limitless scaling, as you can keep adding more machines.
  * Improved fault tolerance; if one node fails, others can take over.
  * Often more cost-effective, as it uses commodity hardware.
  * Better suited for distributed systems and cloud environments.
* Disadvantages:

  * More complex to implement, as it requires changes to application architecture (e.g., load balancing, data consistency).
  * Potential for increased latency due to network communication between nodes.
  * Managing distributed systems can be challenging (e.g., ensuring data consistency, handling node failures).

  When to Use*

  Vertical Scaling: Best for applications with moderate growth, simpler architectures, or when quick scaling is needed without redesigning the system. Example: Legacy systems or small-scale databases.

  * Horizontal Scaling: Ideal for modern, cloud-native applications, high-traffic systems, or when fault tolerance and massive scalability are critical. Example: Web applications, microservices, or big data systems.

  Real-World Context*

  Vertical Scaling: Upgrading a single AWS EC2 instance from a t2.micro to a t2.large.

  Horizontal Scaling: Adding more nodes to a Kubernetes cluster or using a NoSQL database like MongoDB with sharding.

## Blue Green Deployment
