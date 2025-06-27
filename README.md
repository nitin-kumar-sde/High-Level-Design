# 🎡 High-Level Design (HLD) Complete Roadmap with Resources

🚀🚀 Welcome to the all-in-one guide to master **High-Level Design (HLD)**.


Whether you're preparing for **system design interviews**, building your next **SaaS or distributed system**, or leading **architecture discussions**, this repo has you covered.

---

# 📘 Table of Contents

1. [🔍 What is HLD?](#-what-is-hld)
2. [🔩 What does HLD comprise?](#-what-does-hld-comprise)
3. [📡 Networking & Communication](#-networking--communication)
4. [🛠 Asynchronous Processing](#-asynchronous-processing)
5. [🎪 Architectural Paradigms](#-architectural-paradigms)
6. [💰 Caching Techniques](#-caching-techniques)
7. [👒 Databases](#-databases)
8. [🧮 Consistent Hashing](#-consistent-hashing)
9. [📈 Scalability & Performance](#-scalability--performance)
10. [⛓️ Consistency, Availability, Partitioning (CAP)](#-consistency-availability-partitioning-cap)
11. [🔐 Security & Authentication](#-security--authentication)
12. [⛺ Fault Tolerance & Resiliency](#-fault-tolerance--resiliency)
13. [👁️ Observability & Monitoring](#-observability--monitoring)
14. [⚖️ Trade-Offs & Design Decisions](#-trade-offs--design-decisions)
15. [📚 Recommended Books](#-recommended-books--courses)

---

# 🔍 What is HLD?

High-Level Design (HLD) defines the overall architecture and structure of the system — like viewing the system from 10,000 feet above. It focuses on how different subsystems and services interact to achieve business goals, without delving into class-level implementation.

A well-thought HLD ensures your system is scalable, resilient, maintainable, and easy to evolve.


[Learn More →](https://www.geeksforgeeks.org/system-design/what-is-high-level-design-learn-system-design/)

---

# 🔩 What does HLD comprise?

High-Level Design (HLD) captures the macro architecture — how different components fit together and interact to meet system goals. 

It primarily focuses on the following key areas

- 💼 Component Responsibilities
- 💬 Inter-Component Communication
- 🏛️ Architecture Style
- 🌍 Database & Storage Decisions
- 📺 Caching Strategy
- 🔐 Security Considerations
- 💪 Fault Tolerance & Resilience
- 📈 Scalability and Availabilty
- 🤖 Monitoring & Observability
- 🧭 Deployment & Infrastructure Overview
- ⌛ Testing Strategy at the System Level


---

# 📡 Networking & Communication

## 🤝 Network Communication Models

There are primarily two fundamental types of communication models in networked systems -  Client-Server and Peer-to-Peer (P2P).

### 📦 Client-Server Communication

A client requests a service, and a server provides it.

Example: Your web browser (client) loading a website (server).

Peer-to-Peer (P2P) Communication

Each participant (peer) acts as both a client and a server.

Example: File sharing (BitTorrent), blockchain networks.

[Learn More →](https://www.geeksforgeeks.org/computer-networks/difference-between-client-server-and-peer-to-peer-network/)


## 🌐 Network Protocols

Protocols are the essential rules governing how computers communicate and exchange data.

### ⏱️ HTTP 

**HTTP (Hypertext Transfer Protocol)** is the primary web protocol. It uses a client-server request-response model to exchange web content. It's fundamentally stateless, treating each interaction independently

### Example

HTTP Request (Client asks)

```
GET /homepage.html HTTP/1.1
Host: www.example.com

```

HTTP Response (Server answers)
```
HTTP/1.1 200 OK
Content-Type: text/html

<!DOCTYPE html>
<html><body>Hello!</body></html>
(Server says "OK," sends back HTML content)
```


### 🔌 WebSockets

**WebSockets** provide a persistent, **full-duplex** communication channel between a client and a server over a **single, long-lived TCP connection**. They enable instant, two-way data exchange, unlike HTTP's request-response cycle.

#### 💡 Key Characteristics 

* **⚡ Real-time:** Enables instant data flow.
* **↔️ Bi-directional:** Both client and server can send messages anytime.
* **🤝 Persistent:** Connection stays open after an initial HTTP handshake.
* **💨 Low Latency:** Reduced overhead for continuous communication.
* **Efficiency:** Smaller message frames post-handshake.

[Learn More →](https://www.geeksforgeeks.org/what-is-web-socket-and-how-it-is-different-from-the-http/)

## 📇 Inter-Service Communication Styles

### 💼 REST (Representational State Transfer)

**REST** is an **architectural style** for designing networked applications, primarily leveraging **HTTP**. It defines a standardized, stateless way for systems to interact with **resources** identified by **URIs** (URLs).

#### 💡 Key Characteristics 

* **Client-Server:** Clear separation for independent scaling.
* **Stateless:** Every request is self-contained; server remembers no prior client context.
* **Uniform Interface:** Consistent interaction via standard HTTP methods and resource identification.
* **Cacheable:** Responses indicate if they can be stored for performance.

### 📮 RPC (Remote Procedure Call)

**RPC (Remote Procedure Call)** is a communication paradigm that allows a program to execute a function (or "procedure") in a different address space, typically on a **remote computer**, as if it were a local function call. It aims to make inter-service communication appear seamless to the developer, abstracting away the underlying network complexities.

#### 💡 Key Characteristics 

* **⚡ Synchronous by Default:** Client typically waits for the remote procedure to complete and return a result.
* **🔌 Direct Communication:** Services call each other directly.
* **⚙️ High Performance:** Often optimized for speed, using efficient serialization (e.g., Protobuf) and transport protocols (e.g., HTTP/2 in gRPC).
* **🌍 Language Agnostic:** Frameworks support calling procedures across different programming languages.
* **Abstracts Networking:** Developers write code as if calling a local function; the RPC framework handles serialization, network transmission, and deserialization.

[Learn More →](https://www.geeksforgeeks.org/difference-between-rest-api-and-rpc-api/)

## 🪟 API Gateway

An **API Gateway** acts as the **single entry point** for all external clients to access a set of backend services (especially in microservices architectures). It sits in front of your services, handling incoming requests and routing them to the appropriate destination.

#### 💡 Key Characteristics

* **🌐 Single Entry Point:** Consolidates multiple service endpoints into one unified API for clients.
* **🎯 Intelligent Routing:** Directs requests to the correct backend service based on defined rules.
* **🔐 Centralized Security:** Handles authentication, authorization, and API key validation before requests reach services.
* **🚦 Traffic Management:** Implements rate limiting, throttling, and basic load balancing to protect backend services.
* **🔄 Request/Response Transformation:** Modifies data formats or aggregates responses from multiple services.
* **📊 Observability:** Provides centralized logging and monitoring for all API traffic.
* **🛡️ Resilience:** Can incorporate circuit breakers and retry mechanisms to enhance system stability.

[Learn More →](https://www.geeksforgeeks.org/system-design/what-is-api-gateway-system-design/)

## 🌎 How internet works

These three pillars work in concert to deliver web content to you efficiently

* **📞 DNS (Domain Name System)**  - The internet's "phonebook." It translates human-readable domain names (like `example.com`) into numerical IP addresses (like `192.0.2.1`) that computers understand, enabling your browser to find servers.
* **🌐 ISPs (Internet Service Providers)** - Your "on-ramp" to the internet. These companies provide the physical network infrastructure and connectivity that links your device to the global web, managing the flow of data packets.
* **🚀 CDNs (Content Delivery Networks)** - Networks of geographically distributed servers that **cache and deliver content** (images, videos, static files) from a location **closest to the user**. They drastically reduce latency and improve website performance by serving content from "edge" locations, offloading traffic from origin servers.

**⛲ All in One:** - DNS directs requests, ISPs provide the connectivity, and CDNs ensure fast, reliable content delivery by bringing data closer to you, forming the fundamental backbone of the internet experience.

### 📘 Learn More

- [📞DNS](https://www.geeksforgeeks.org/computer-networks/domain-name-system-dns-in-application-layer/)
- [🌐 ISP](https://www.geeksforgeeks.org/isp-full-form/)
- [🚀 CDN](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/)

---

# 🛠 Asynchronous Processing 

In high-performance, distributed systems, **asynchronous processing** is a foundational pattern that improves **responsiveness**, **scalability**, and **fault isolation** by offloading non-critical or time-intensive operations to background workflows.

Instead of executing every task inline (synchronously), asynchronous systems **defer certain tasks**, allowing the system to respond immediately and handle deferred work independently.

## 🧠 Common Use Cases

- **🎥 Time-Intensive Tasks** - Used when operations take too long to complete inline (e.g., file processing, ML inference).

- **🤖 Background Jobs** - For tasks that don’t require immediate user feedback (e.g., sending emails, notifications).

- **⌛ Load Buffering** - Helps absorb high traffic spikes and smooth load before hitting downstream systems.

- **⚛︎ Service Decoupling** - Allows independent scaling, deployment, and failure isolation between producers and consumers.


## 💌 Message Queues / Brokers

A **Message Queue** (or **Message Broker**) is a system component that enables **asynchronous communication** between decoupled services by allowing messages to be placed in a queue by producers and consumed by consumers at their own pace.

This decoupling ensures that services remain **resilient**, **scalable**, and **non-blocking**, especially under heavy load or varying processing speeds.

[Learn More →](https://imehboob.medium.com/message-queue-101-your-ultimate-guide-to-understand-message-queue-b2256961ab01)

### ♻️ When to Use 

- ⚛ Consumers process messages asynchronously and independently
- 🔗 Decoupling between data producers and consumers
- 📢 For tasks that don’t require immediate action
  
### 📦 Common Message Brokers

| Broker        | Description                                                    |
|---------------|----------------------------------------------------------------|
| [RabbitMQ](https://www.rabbitmq.com/) | Traditional queue-based system, supports complex routing       |
| [Amazon SQS](https://aws.amazon.com/sqs/)| Fully managed, scalable message queue by AWS                |

## 🌊 Message Streams

A **Message Stream** enables continuous, ordered, and real-time flow of data between services. Unlike queues, where messages are removed after consumption, streams retain data for a fixed duration, allowing multiple consumers to independently read messages at their own pace.

[Learn More →](https://medium.com/@abdullahjaffer96/low-level-data-design-part-4-stream-processing-b613be855743)

### ♻️ When to Use 

- ⚛ Consumers process messages asynchronously and independently
- 🔗 Multiple consumer groups process messages simultaneously
- 📢 For tasks that don’t require immediate action

  
### 📦 Common Message Streams
| Stream        | Description                                                    |
|---------------|----------------------------------------------------------------|
| [Apache Kafka](https://kafka.apache.org/) | Distributed event streaming platform, supports high-throughput, real-time data pipelines |
| [Amazon Kinesis](https://aws.amazon.com/kinesis/) | Managed real-time data streaming service on AWS, ideal for analytics and ingestion |


## 📡 Real-Time Pub/Sub

Real-Time Pub/Sub (Publish–Subscribe) is a communication pattern where senders (publishers) broadcast messages to topics, and receivers (subscribers) get updates instantly, without knowing each other.

It enables loose coupling, scalable fan-out, and real-time delivery, powering systems like chat apps, collaborative editors, live dashboards, and IoT devices.

[Learn More →](https://medium.com/@kyberneees/introducing-realtime-pub-sub-enabling-developers-to-build-the-modern-web-with-realtime-pub-sub-f18cee59c637)

### ♻️ When to Use 

- ⚛ Instant updates to multiple consumers (e.g., live feed, multiplayer game)
- 🔗 Decoupling between data producers and consumers
- 📢 Asynchronous communication with minimal delay

### 📦 Common Message Pub Sub
| Stream        | Description                                                    |
|---------------|----------------------------------------------------------------|
| [Reddis PubSub](https://redis.io/docs/latest/develop/interact/pubsub/) | Lightweight, in-memory pub/sub system for low-latency, ephemeral message delivery |
| [Amazon SNS](https://aws.amazon.com/sns/) | Fully managed pub/sub service on AWS for real-time event broadcasting to multiple endpoints |

## 📘 Resources

- [Message Queues](https://medium.com/must-know-computer-science/system-design-message-queues-245612428a22)
- [Streams](https://medium.com/@abdullahjaffer96/low-level-data-design-part-4-stream-processing-b613be855743)
- [Real time Pub Sub](https://aws.amazon.com/what-is/pub-sub-messaging/)


---

# 🎪 Architectural Paradigms

Choosing how to structure your application is a foundational decision in system design. It impacts everything from development speed and scalability to maintainability and team organization. Let's explore the primary architectural styles.

## 🏰 Monolithic Architecture

A monolithic application is built as a **single, tightly coupled, and indivisible unit**. All its components run within one process, sharing a single codebase and database.

### 💡 Key Characteristics

* 📦 **Single Unit** - One large, comprehensive application.
* 🔗 **Shared Everything** - Single codebase, single deployment, single database.
* 🌱 **Simpler Start** - Easy to develop and deploy initially.
* 🌍 **Global Scaling** - Scales by duplicating the entire application.
* 🕸️ **High Interdependency**  - Changes in one part can impact the whole.
* 🐌 **Slower Evolution (at scale)** - Can become unwieldy to maintain and update as it grows.

## 🧩 Microservices Architecture 

Microservices architecture designs an application as a **collection of small, independent, and loosely coupled services**, each representing a distinct business capability. They communicate over networks (APIs, messages) and can be developed, deployed, and scaled autonomously.

### 💡 Key Characteristics

* ⚙️ **Independent Services** - Each focuses on a specific function (e.g., "User Service").
* 🚀 **Autonomous Units**  - Independent development, deployment, and scaling.
* 🏘️ **Decentralized Data**  - Each service typically owns its own database.
* 💬 **Network Communication** - Services talk via APIs (REST, RPC) or message queues.
* 🌈 **Technology Flexibility** - Different services can use different tech stacks.
* ⚠️ **Increased Operational Overhead**  - More components to manage, monitor, and debug.


## 📊 Comparison Monolith vs. Microservices

| Feature          | Monolithic Architecture                                  | Microservices Architecture                               |
| :--------------- | :------------------------------------------------------- | :------------------------------------------------------- |
| **Structure** | Single, unified, tightly coupled application            | Collection of small, independent, loosely coupled services |
| **Deployment** | Single deployable unit (entire application)              | Each service deployed independently                     |
| **Scalability** | Scales entirely; scale one function = scale all          | Scales independently; scale only services under load      |
| **Coupling** | High (components highly interdependent)                  | Low (services communicate via APIs/messages)             |
| **Data Mgmt.** | Centralized, shared database                             | Decentralized (each service owns its data)               |
| **Tech Stack** | Usually uniform across the entire app                    | Heterogeneous (different tech for different services)    |
| **Complexity** | Lower *initial* complexity; higher *long-term* complexity | Higher *initial* complexity; manageable *long-term* complexity |
| **Resilience** | Single point of failure can bring down whole app         | Fault isolation (one service failure doesn't halt others) |
| **Team Size** | Larger, shared teams                                     | Smaller, autonomous teams per service                    |

[Learn More →](https://www.geeksforgeeks.org/monolithic-vs-microservices-architecture/)

## 🥊 Event-Driven Architecture (Choreography)

**Event-Driven Architecture (EDA)** is an architectural paradigm where services communicate indirectly through **events**. Instead of making direct requests, services publish events when something significant happens, and other services subscribe to and react to these events.

### 💡 Key Characteristics

- ⏳ **Asynchronous Communication** - Producers don't wait for consumers; events are processed independently.
- 🎭 **Decoupled Services** - Services don't need to know about each other directly, only about the events.
- ♟️ **Real-time Responsiveness** - Ideal for immediate reactions to system changes.
- 🪁 **Scalable & Resilient** - Individual services can fail or scale without impacting the entire flow.
- 🚌 **Event Broker/Bus** - A central component (like Kafka or RabbitMQ) mediates events between producers and consumers.

## 🤹‍♀️ Workflow (Orchestration)

A **centralized orchestrator (or "conductor" service)** explicitly controls and coordinates the sequence of steps in a business process. It knows the entire workflow, telling each service exactly what to do and when.

### 💡 Key Characteristics

- 🪜 **Sequence of Steps** - Defined order of operations.
- 🕰️ **Often Long-Running** - Can span minutes, hours, or even days.
- 🤝 **Involve Multiple Services** - Typically requires interaction between several distinct components or microservices.
- 💾 **Require State Management** - Progress needs to be tracked to resume or compensate for failures.
- ✅ **Business Outcome-Oriented** - Designed to achieve a specific functional result (e.g., "process an order").

## 📊 Comparison Orchestration vs Choreography

| Feature             | Orchestration                                                       | Choreography                                                         |
| :------------------ | :------------------------------------------------------------------ | :------------------------------------------------------------------ |
| **Control** | **🧠 Centralized** Dedicated orchestrator service manages flow. | **🏘️ Decentralized** Services react to events autonomously. |
| **Flow Visibility** | **✅ Clear** Easy to see entire workflow in one place.              | **🤯 Distributed**  Harder to visualize end-to-end flow.           |
| **Observability/Tracing** | **🔍 Easier**  Centralized point for monitoring and tracing workflow state. | **🧩 Challenging**  Requires robust distributed tracing tools; fragmented view. |
| **Coupling** | **🔗 Tighter**  Orchestrator is coupled to each service it calls. | **🤝 Looser** Services only coupled to the event contract.         |
| **Resilience** | Orchestrator failure can **💥 halt workflow**.                        | More **✨ resilient** Failures are often isolated.              |
| **Complexity** | Easier for **simple, fixed workflows** to start.                      | More complex to design and debug **distributed flows** at scale.   |

[Learn More →](https://www.geeksforgeeks.org/system-design/orchestration-vs-choreography/)

---

# 💰 Caching Techniques

Caching is a technique to store frequently accessed data in a fast-access storage layer (memory or disk) to reduce latency and offload backend systems.

[Learn More →](https://www.geeksforgeeks.org/caching-system-design-concept-for-beginners/)

## 💎 Standard Terms
| Term                 | Meaning                                              |
| -------------------- | ---------------------------------------------------- |
| Cache Hit        | Data found in the cache                              |
| Cache Miss       | Data not found, fetched from source                  |
| Cache Eviction   | Removing data when cache is full                     |
| Cache Population | How data is loaded into cache (on demand or upfront) |
| Cache Invalidation | Process of removing or updating stale cache entries when the source data changes |

## 🪙 Cache Population Strategies
**Lazy Loading**
Cache is populated only on first request (miss) → then stored.

**Eager Loading**
- Server writes to DB and cache both
- Asychronous system can populate cache 

##  🗓️ Levels of Caching
| Level                 | Example                         | Use Case                                        |
| --------------------- | ------------------------------- | ----------------------------------------------- |
| Client-Side       | Browser cache, localStorage     | Static assets, previous API results             |
| CDN-Level         | Cloudflare, Akamai              | Images, videos, HTML – reduces edge latency     |
| App/Service-Level | Redis, Memcached                | Frequently accessed DB results, config, session |
| Database-Level    | Query cache, materialized views | Reduces expensive joins/aggregates              |

## 🏵️ Scaling Distributed Caching
| Strategy                         | Description                                   |
| -------------------------------- | --------------------------------------------- |
| Sharding                    | Divide cache across nodes (based on key hash) |
| Replication             | Redundancy for high availability              |
| TTL & Expiry            | Control staleness and memory usage            |
| Consistent Hashing           | Smooth rebalancing during scale-up/down       |
|Write-through / Write-behind | Control how writes sync with DB               |

## 📘 Resources
- [Caching Tutorial](https://medium.com/must-know-computer-science/system-design-caching-acbd1b02ca01)

---

# 👒 Databases

Database is a structured collection of data that enables efficient storage, retrieval, modification, and management of information. Databases are at the core of nearly every backend architecture and directly influence scalability, consistency, and performance of distributed systems.

## 🎻 Types of Databases

### 🧱 Relational Databases (RDBMS)
- **Structure**: Tables with fixed schema (rows and columns).
- **Examples**: MySQL, PostgreSQL, Oracle, SQL Server.
- **Strengths**: Strong consistency, transactions (ACID), structured queries (SQL).
- **Use Cases**: Financial systems


### ⛲ NoSQL Databases
A class of databases designed for specific data models and flexible schemas.

#### 📝 Document Stores
- **Structure**: JSON-like documents (flexible fields).
- **Examples**: MongoDB
- **Use Cases**: Content management, product catalogs.

####  🗝️ Key-Value Stores
- **Structure**: Key ↔ Value pairs.
- **Examples**:  DynamoDB.
- **Use Cases**: Real-time high throughput data.


####  🕸️ Graph Databases
- **Structure**: Nodes and edges representing entities and relationships.
- **Examples**: AWS Neptune.
- **Use Cases**: Social networks, recommendation systems, fraud detection.


## 🗽 Transactions & ACID Properties

### 🗼 Transaction
A **transaction** is a sequence of one or more operations performed as a **single logical unit of work**. 

It must be **all-or-nothing**: either every operation succeeds, or none of them does.


### 🧪 ACID Properties

ACID ensures the reliability and integrity of database transactions:

#### ✂️ Atomicity
- Guarantees that **all operations** in a transaction are completed.
- If any operation fails, the **entire transaction is rolled back**.
- 👉 Deducting money from one account and adding to another.

#### 📊 Consistency
- Ensures the database moves from **one valid state to another**.
- All **constraints, rules, and triggers** are maintained.
- 👉 No transaction can leave the database in a corrupt state.

#### ⏳ Isolation
- Ensures **concurrent transactions** don't interfere with each other.
- Transactions appear to run **serially**, even if executed in parallel.
- 👉 Prevents dirty reads, non-repeatable reads, and phantom reads.

#### 📦 Durability
- Once a transaction is **committed**, its changes are **permanent**.
- Survives power failures, crashes, or system shutdowns.
- 👉 Data is persisted to disk/log before commit is acknowledged.


## 🚀 Database Scaling

As data volume and query load grow, databases must **scale** to maintain performance. Vertical scaling (bigger machine) hits limits — so we adopt **horizontal scaling** via **partitioning** and **sharding**.


### 🧩 Partitioning

**Partitioning** is the process of **splitting a large table into smaller pieces** (partitions) to improve query performance and manageability. It's often done within a **single database server**.

#### 🚁 Types of Partitioning
- **Horizontal Partitioning**: Rows are divided across partitions.
  - 👉 Example: Orders for 2023 vs 2024.
- **Vertical Partitioning**: Tables are split across partitions.
  - 👉 Example: Table 1 in partition 1, Table 2 in partition2.


### ✈️ Sharding

**Sharding** is a form of horizontal partitioning where **data is split across multiple independent database servers** (shards). Each shard holds a subset of the data.

#### ♟️ Key Concepts
- **Shard Key**: The field used to determine which shard stores the data.
- **Shard Router**: Routes queries to the correct shard.
- **Rebalancing**: Moving data when shards become uneven.

### 🎲 Types of Sharding
- **Range-Based**: Based on value ranges (e.g., user_id 1–1000).
- **Hash-Based**: Distributes data using a hash of the shard key.


#### ✅ Benefits:
- Enables horizontal scaling.
- Isolates data — increases fault tolerance.
- Reduces latency when sharded close to the user.

#### ⚠️ Challenges:
- Cross-shard queries are complex.
- Rebalancing shards can be tricky.
- Harder to maintain **strong consistency**.

### 🧬 Read & Write Replicas

To scale database **reads and writes independently**, many systems adopt a **replication strategy** — where data from a primary (write) database is copied to one or more replicas.


##### ✍️ Write Replica (Primary / Leader)
- **Handles all writes** and **critical read operations**.
- Maintains the **source of truth**.
- Writes are **synchronously** committed here.
- ✅ Ensures **strong consistency**.


#### 📖 Read Replicas (Secondary / Followers)
- Asynchronous copies of the primary database.
- Used to **distribute read load** across multiple servers.
- ⚠️ May lag behind the primary (eventual consistency).


## 🪂 Database Indexes – Optimally Querying 

Indexes are special data structures that improve the **speed of data retrieval** operations on a database table at the cost of **slightly slower writes** and **extra storage**.

Think of them like the **index of a book** — instead of scanning every page, you directly jump to what you want.

### ⚠️ Trade-offs

- ✅ Faster reads.
- ❌ Slower writes (INSERT/UPDATE/DELETE must update indexes).
- ❌ More storage required.

## 🌷 Choosing right Database for your Use Case

Selecting the right database depends on your **access patterns**, **consistency needs**, and **scale**.

| Use Case                         | Recommended Database Type        |
|----------------------------------|----------------------------------|
| ACID Properties / Transactions     | Relational (PostgreSQL, MySQL)   |
| Strong Consistency                 |  Relational (PostgreSQL, MySQL)   |
| Relations between Tables and Constraints           | Relational (PostgreSQL, MySQL)|
| Flexible Schema  | No SQL   |
| High Scaling without constraints   | No SQL |
| Network Structure   | No SQL |

[Read More →](https://www.geeksforgeeks.org/how-to-choose-the-right-database-for-your-application/)

🔑 **Tip**: Design for your **read/write ratio**, **consistency vs availability**, and **schema flexibility** needs.

For more details of Design Schema design and other best practices, Please check - [LLD DB Schema Designing](https://github.com/nitin-kumar-sde/Low-Level-Design/blob/main/README.md#-db-schema-designing)

---

[🧮 Consistent Hashing](#-consistent-hashing)

> TBD

---

# 📈 Scalability & Performance

**Scalability** is your system's ability to handle **increased load** by adding resources, maintaining performance.
 
It is measured by **throughput** - The **volume of requests** your system can handle over time. 


**Performance** is how **fast and efficiently** your system operates, measured by:

It is measured by **Latency**  - **time taken** in processing a request. Aim for low latency for good user experience.

## 💡 Key Scaling Approaches

- **⬆️ Vertical Scaling (Scale Up)** - Adding more power (CPU, RAM) to a **single server**. Simpler initially but has limits.
- **➡️➡️ Horizontal Scaling (Scale Out)** - Adding more **servers** to distribute load. More complex but offers greater potential.

Effective system design considers both scalability to manage growth and performance (low latency, high throughput) to ensure a responsive and efficient user experience.


## 📊 Comparison Vertical vs. Horizontal Scaling

| Feature         | ⬆️ Vertical Scaling (Scale Up)                | ➡️➡️ Horizontal Scaling (Scale Out)              |
| :-------------- | :--------------------------------------------- | :--------------------------------------------- |
| **Concept** | Adds more resources to a **single server**.    | Adds **more servers/instances**.               |
| **Method** | Upgrade CPU, RAM, Disk of existing machine.    | Add new machines; often needs a Load Balancer. |
| **Limits** | **Finite** hardware limits.                    | **Virtually limitless** (add more machines).   |
| **Cost** | Higher cost per unit of power; expensive high-end machines. | Often more cost-effective (commodity hardware). |
| **Complexity** | **Simpler** to manage initially.               | **Higher operational complexity** (distributed system challenges). |
| **Resilience** | **Single Point of Failure** (SPOF).            | **Higher availability** (distributes risk).    |
| **Best For** | Small-to-medium scale apps; non-distributed needs. | Large-scale, distributed, high-traffic systems. |

[Read More →](https://www.geeksforgeeks.org/system-design/system-design-horizontal-and-vertical-scaling/)

## ⚖️ Load Balancers

**Load Balancers** are essential components in distributed systems that help distribute incoming traffic across multiple servers to ensure **scalability**, **reliability**, and **high availability**.

### 🧬 Key Characteristics

- 🧱 **Scalability** – enables horizontal scaling and acts as single point of contact with client.  
- ⚖️ **Load Distribution** – distributes load among servers based on configured algorithm.
- 💥 **Fault Tolerance** – routes traffic away from unhealthy nodes  
- 🔐 **Security** – can help obscure internal infrastructure and manage TLS  
- 🚀 **Performance** – reduces latency by using geographically closer nodes (in global load balancing)


### 🧠 Key Algorithms

| Algorithm              | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| **Round Robin**        | Cycles through servers in order – simple and stateless                      |
| **Least Connections**  | Chooses the server with the fewest active connections                       |
| **IP Hash**            | Maps clients to servers using a hash of the client IP – ensures stickiness  |
| **Weighted Round Robin** | Like Round Robin, but gives preference to more powerful servers            |


[Read More →](https://www.geeksforgeeks.org/system-design/what-is-load-balancer-system-design/)

---

# 🛶 Consistency, Availability, Partitioning (CAP)

## 🚂 Consistency (C)

Consistency in a distributed system means that every client always reads the most recent, successfully written data. After a successful write operation, any subsequent read operation, regardless of which node it hits, will return that latest, updated value. All replicas of the data across different nodes are synchronized.

### ✈️ Types of Consistency

**Strong Consistency** - The strictest form. A write operation is not considered complete until all (or a quorum of) replicas confirm they have the updated data. Reads are guaranteed to return the latest data.

**Eventual Consistency** - A weaker form. After a write, reads might temporarily return stale data from other replicas. However, given enough time (and no new writes to the same data item), all replicas will eventually converge to the same value.


## 🏖️ Availability (A)

Availability means that the system is always operational and responsive to client requests, returning a non-error response for every query. This implies that the system can still function and serve requests even if some individual nodes within the distributed system fail.


## 🌐 Partition Tolerance (P) 

Partition Tolerance means that the system continues to operate effectively and correctly despite network partitions. A network partition occurs when a communication breakdown (e.g., network outage, router failure, cable cut) isolates parts of the distributed system from each other. Nodes in one isolated sub-system cannot communicate with nodes in another.

## ⚖️ CAP Theorem - The Inevitable Trade-Off 

The CAP Theorem (Consistency, Availability, Partition Tolerance) states that it's impossible for a distributed data store to simultaneously provide more than two out of the three guarantees when a network partition occurs.

Since Partition Tolerance (P) is almost always a mandatory requirement for any true distributed system (because networks will fail), in practice, the CAP theorem often boils down to a fundamental choice between Consistency (C) and Availability (A) during a network partition.

### ✅🌐 CP System - Consistency + Partition Tolerance 
Prioritizes **Consistency** over Availability during a network partition.

If a partition occurs, the system will block writes to the affected part of the system or return an error for reads/writes to ensure that data remains consistent. Some nodes might become temporarily unavailable.


### 🟢🌐 AP System - Availability + Partition Tolerance 
Prioritizes **Availability** over Consistency during a network partition.

The system will continue to process requests and remain fully available to all clients, even if it means different nodes might temporarily have divergent (inconsistent) data. Reads might return stale data until the partition is resolved.


### ✅🟢CA System - Consistency + Availability (Less Realistic in Practice)
This configuration implies a system that cannot tolerate network partitions.

Behavior: It can provide both strong Consistency and high Availability only if the network never experiences a partition. If a partition does occur, such a system would become unavailable or inconsistent.

In any truly distributed system spread across networks, the assumption of "no partitions" is unrealistic. Therefore, CA systems are typically found in highly localized, non-distributed, or single-node database environments.

[Read More →](https://www.geeksforgeeks.org/system-design/cap-theorem-in-system-design/)

---

# 🔐 Security & Authentication


Security is a paramount concern in any system design, ensuring data integrity, confidentiality, and availability. 

It involves several distinct, yet interconnected, mechanisms to control access and manage behavior.

## 🆔 Authentication (AuthN)

**Authentication** is the process of **verifying the identity of a user, service, or application**. It answers the question "Who are you?"

### 🧸 Common Mechanisms

- **Passwords & Hashing** - Users provide credentials, which are compared against stored (hashed and salted) versions.
- **Multi-Factor Authentication (MFA)** - Requires two or more verification methods (e.g., password + OTP from app, fingerprint). Greatly enhances security.
    - **🔑 OAuth 2.0 / OpenID Connect (OIDC)**
        -  **OAuth:** A delegated authorization framework, allowing a user to grant a third-party application limited access to their resources on another service without sharing credentials.
        - **OIDC:** An identity layer built on top of OAuth 2.0, specifically for authentication, providing user identity claims (used for Single Sign-On - SSO).
    * **🎫 JSON Web Tokens (JWT)** Compact, URL-safe means of representing claims (e.g., user identity, permissions) between two parties. Often used for stateless authentication and authorization after initial login. The server issues a token, and subsequent requests include this token for verification without repeated database lookups.


## 🔒 Authorization (AuthZ)

**Authorization** is the process of **determining what an authenticated entity is permitted to do** within the system. It answers the question: "What are you allowed to do?"

To enforce access control policies, ensuring users can only perform actions and access resources they have been granted permission for. It always follows successful authentication.

### 🧸 Common Mechanisms
    
-  **🎭 Role-Based Access Control (RBAC)** - Permissions are assigned to roles (e.g., 'Admin', 'Editor', 'Viewer'), and users are assigned to roles. Simplifies management for large user bases.
- **✨ Attribute-Based Access Control (ABAC)** - Access decisions are based on attributes (characteristics) of the user, resource, action, and environment (e.g., "User `X` can edit `Document Y` if `X` is in department `Z` and `Y` is a draft"). More fine-grained and flexible than RBAC.
- **📝 Access Control Lists (ACLs)** - Directly maps permissions to individual users or groups for specific resources (e.g., "User Alice has read access to File A"). Can become cumbersome for many users/resources.

## ⏳ Rate Limiting / Throttling

**Rate Limiting** is a strategy for **controlling the rate at which an API or service accepts requests** from a user, IP address, or application over a defined time window.

### 🫧 Key Benifits
- **Prevent Abuse** - Mitigate brute-force attacks, DoS/DDoS attacks by malicious clients.
- **Ensure Fair Usage** - Prevent a single user or client from monopolizing system resources.
- **Protect Downstream Services** - Shield backend services from being overwhelmed.
 
      
### 🧳 Common Algorithms
- **🪟 Fixed Window Counter** - Simple; counts requests in a fixed time window (e.g., 100 requests per minute). Prone to "bursty" traffic at window edges.
- **🏠 Sliding Window Log** - Tracks timestamps of each request. Most accurate but resource-intensive.
- **🏢 Sliding Window Counter** - Hybrid; combines fixed windows but uses previous window's rate to smooth out bursts.
- **🪙 Token Bucket** - A "bucket" of tokens is refilled at a fixed rate. Each request consumes a token. Allows for bursts up to bucket capacity.
- **💧 Leaky Bucket** - Requests enter a queue (the "bucket") and are processed at a constant rate. Excess requests overflow/are dropped. Smooths out bursts.

> 🧠 Note - Typically implemented at the API Gateway, Load Balancer, or specific service level.


[Read More on Security →](https://www.geeksforgeeks.org/system-design/essential-security-measures-in-system-design/)

[Read More on Rate Limiting →](https://www.geeksforgeeks.org/system-design/rate-limiting-in-system-design/)


---


# ⛺ Fault Tolerance & Resiliency

In any complex system, failures are not a matter of "if," but "when."

**Fault Tolerance** and **Resiliency** are about designing systems that can continue to operate correctly even when parts of them fail. While often used interchangeably, they have subtle distinctions:

- **🕹️ Fault Tolerance** - The ability of a system to **continue operating without interruption** when one or more of its components fail. It's about designing redundancy and mechanisms to mask failures.

- **✨ Resiliency** - The ability of a system to **recover gracefully from failures** and maintain an acceptable level of service. It's a broader concept that includes fault tolerance, but also emphasizes recovery, adaptability, and degradation.


## ♟️ Most Common Strategies

## 🧬 Data Redundancy

Data Redundancy is the intentional duplication of data to improve **reliability**, **availability**, and **disaster resilience** in distributed systems.

### 🔁 Replication

Storing the same data across multiple nodes or regions.

**Types of Replication** 

**🟢 Synchronous Replication** 
- Strongly Consistent  
- Higher latency due to coordination
  
**⚡ Asynchronous Replication**   
- Eventual Consistent
- Faster writes  


### 🗃️ Backups
Periodic copies of entire datasets stored separately.

**Characteristics**
Usually offline or cold storage

Useful for long-term recovery

**Best Practices**
- Automate regular snapshots
- Use incremental backups to save space
- Store offsite or on cloud


### 🌪️ Disaster Recovery 
A plan for recovering system functionality and data in the event of a major catastrophic failure (e.g., entire data center outage, natural disaster).

Multi-region deployments, regular backups, data replication to remote locations.


## 🌍 Advantages of Data Redundancy
- High availability & fault tolerance
- Faster recovery from failures
- Protection against accidental data loss or corruption

> ⚠️ **Trade-off**: Redundancy increases storage cost and requires careful consistency management.


## ⏳🔄 Timeouts & Retries

**Timeouts** - Limiting the amount of time a service will wait for a response from another service. Prevents indefinite waits and resource exhaustion.

**Retries** - Attempting a failed operation again.
- **With Exponential Backoff** - Waiting for progressively longer periods between retries to avoid overwhelming a struggling service.
- **Idempotency (Crucial for Retries)** - Designing operations so that performing them multiple times has the same effect as performing them once. This makes retries safe.


## ⚡️ Circuit Breaker


A **Circuit Breaker** is a resilience pattern used to prevent **cascading failures** in distributed systems by **detecting failure conditions** and **short-circuiting requests** before they cause wider system impact.

### ⚙️ What It Does

- 🚧 Monitors calls to remote services or components
- 🛑 "Breaks the circuit" if failures cross a threshold (e.g., timeouts, errors)
- 🔁 Automatically retries after a **cool-down period**
- ✅ Allows systems to **fail fast** and **recover gracefully**
- 🎸 Can skips calls to a components and go with some default behaviour (if use case allows)


### 🔄 States of a Circuit Breaker

| State        | Description                                                                  |
|--------------|------------------------------------------------------------------------------|
| **Closed**   | Normal operation – requests flow through and failures are monitored         |
| **Open**     | Circuit is "tripped" – all requests are immediately failed/skipped          |
| **Half-Open**| Limited requests are allowed to test if service has recovered               |


### 🎸 Key Advantages

- 🧯 **Prevents cascading failures**
- 🚀 **Improves system stability and fault tolerance**
- 📉 **Reduces unnecessary load on degraded services**

[Read More →](https://www.geeksforgeeks.org/system-design/what-is-circuit-breaker-pattern-in-microservices/)

## 🧭  Auto-Recovery from failures - Leader Election 

**Leader Election** is a coordination strategy where a single node is chosen as the **primary coordinator** among a group of distributed nodes. It's critical for **auto-recovery**, **failover**, and high **system availabilty**.



### 👑 What is Leader Election?
A **leader node** handles critical tasks like
- Health check Worker Nodes
- Spinning new Worker Nodes and terminating Unhealthy Nodes
  
If the leader fails, a new one is **automatically elected** using Leader Election Algorithm.

### 🔄 Auto-Recovery Flow
- 🛑 **Leader fails** 
- 🔍 **Election triggered** among worker/follower nodes
- 👑 **New leader elected and Promoted as Leader**
- ✅ **System resumes operations** smoothly


### ⚙️ Common Algorithms
- **📶Bully Algorithm**
  - Highest-ID node becomes leader  
  - Simple, but slower in large clusters
- **🚤 Raft Consensus** 
  - Robust leader election with log replication  
  - Used in systems like etcd, Consul

### 🌟 Key Advantages of Leader Election 
- 🚫 No single point of failure
- 🔄 Seamless auto-failover
- 📶 High system availability


[Read More →](https://www.geeksforgeeks.org/system-design/leader-election-in-system-design/)

---

# 🔬 Observability & Monitoring

In complex distributed systems, it's not enough to just build robust services; you need to understand their internal state, performance, and health at all times. This is the domain of Observability and Monitoring.

**🔬 Observability** - The act of **collecting and analyzing predefined metrics and logs** to understand the health and performance of your system.


## 🎡 The Three Pillars of Observability

### 📈 Metrics

Aggregated, numeric data points measured over time. They quantify behavior and resource utilization.

Most commonly used metrics - CPU usage, memory consumption, network I/O, requests per second (RPS), error rates, database query latency.

### Logs

Discrete, timestamped records of events that occur within an application or system. They provide granular detail about what happened and when.

Most commonly used logs - Application Logs, Request Logs

### 🗺️ Traces

A representation of the end-to-end flow of a single request or transaction as it propagates through multiple services in a distributed system. A trace links together operations (spans) from different services.
It is crucial for understanding latency bottlenecks, identifying which service in a complex microservices architecture is causing a slowdown, and debugging distributed issues.

**Key Concepts:**
- **Span** - A single operation within a trace (e.g., an RPC call, a database query). Each span has a start/end time.
- **Trace ID** - A unique identifier linking all spans belonging to the same request.
- **Context Propagation** - Passing trace IDs and other context across service boundaries (e.g., via HTTP headers).


## 📟 Essential Practices for Observability

- **🚨 Alerting** - Proactive notifications (email, SMS, PagerDuty, tickets) when predefined thresholds are breached or anomalies are detected in metrics or logs.
- **📈 Dashboards** - Visual representations of metrics and logs, providing real-time insights into system health, performance trends, and business KPIs.
- **📖 Runbooks/SOPs** - Documented procedures for responding to specific alerts or common operational issues, enabling faster incident resolution.

[Read More →](https://www.geeksforgeeks.org/what-is-observability)


---

# 🆚 Trade Offs & Design Decisions

Building any system, especially a distributed one, is fundamentally about making choices. Every architectural decision involves weighing competing priorities and understanding the inherent trade-offs. There's no one-size-fits-all solution; the "best" design depends entirely on your specific use cases, non-functional requirements (NFRs), and business goals.

Here are some of the most common and critical trade-offs encountered in system design

## 🤹 Availability vs. Consistency (CAP Theorem) 

As we've extensively discussed, in a distributed system experiencing a network partition (an inevitable reality), you must choose between always being responsive (**Availability**) or always returning the most up-to-date, synchronized data (**Consistency**).

Prioritizing **Consistency** (CP systems) means you might experience temporary service unavailability or blocking to prevent data inconsistencies. 

Prioritizing **Availability** (AP systems) means your system will always respond, but might serve slightly stale data during a partition.

🤔 What's more critical for your application? Financial transactions demand C. Social media feeds tolerate A.

## 🚀 Latency vs. Throughput

Optimizing for one can sometimes come at the expense of the other.

- **Low Latency** - Focus on minimizing the time for a single request to complete (e.g., instant search results). Often involves fewer steps, direct paths.
- **High Throughput** - Focus on maximizing the number of requests processed per unit of time (e.g., processing millions of sensor readings per second). Might involve batching, queues, or other techniques that add individual request latency.

🤔 Is your primary goal a snappy user experience for individual actions, or processing a massive volume of work efficiently?

## 🎯 Latency vs. Accuracy

 Providing a very fast, approximate answer versus a slow, perfectly precise one.

- **Low Latency (Sacrifice Accuracy)** - Returning results quickly from caches, eventual consistency models, or approximate algorithms. The answer might be slightly outdated or statistically derived.
- **High Accuracy (Sacrifice Latency)** - Querying the authoritative source, performing complex computations, ensuring strong consistency. This takes more time.

🤔 For user search suggestions or trending topics, speed beats perfect accuracy. For financial reports or crucial data analytics, accuracy is paramount.

## 💰 Cost vs. Performance/Scalability 

Investing more money into hardware, infrastructure, and specialized services can significantly improve performance and scalability, but budget is always a constraint.

Running more servers, using premium cloud services, or having highly optimized (and expensive) database solutions all add to operational costs. Conversely, trying to be too frugal can lead to performance bottlenecks and scaling limitations.

🤔 What's the acceptable balance between operational expenditure (OpEx) and the desired level of service and future growth capacity?

[Read More →](https://sumitnarangin.medium.com/tradeoffs-in-design-fb11b999753c)

---

## 📚 Recommended Books & Courses

- **Designing Data-Intensive Applications** by Martin Kleppmann
- **System Design Interview** – Alex Xu (Vol 1 & 2)
- **Building Microservices** – Sam Newman


---
