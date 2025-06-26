# 🎡 High-Level Design (HLD) Complete Roadmap with Resources

🚀🚀 Welcome to the all-in-one guide to master **High-Level Design (HLD)**.


Whether you're preparing for **system design interviews**, building your next **SaaS or distributed system**, or leading **architecture discussions**, this repo has you covered.

---

# 📘 Table of Contents

1. [🔍 What is HLD?](#-what-is-hld)
2. [🔩 What does HLD comprise?](#-what-does-hld-comprise)
3. [📡 Networking & Communication](#-networking--communication)
4. [🛠 Asynchronous Processing](#-asynchronous-processing)
5. [🏛️ Architectural Paradigms](#-architectural-paradigms)
6. [💰 Caching Techniques](#-caching-techniques)
7. [👒 Databases](#-databases)
8. [🧮 Consistent Hashing](#-consistent-hashing)
9. [⛓️ Consistency, Availability, Partitioning (CAP)](#-consistency-availability-partitioning-cap)
10. [🔐 Security & Authentication](#-security--authentication)
11. [📈 Scalability & Performance](#-scalability--performance)
12. [🔁 Fault Tolerance & Redundancy](#-fault-tolerance--redundancy)
13. [⚖️ Trade-Offs & Design Decisions](#-trade-offs--design-decisions)
14. [📚 Recommended Books](#-recommended-books--courses)

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

## 🏛️ Architectural Paradigms

> TBD

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

## 📈 Scalability & Performance

- Vertical vs Horizontal Scaling
- Auto-scaling groups
- CDN, DB Replication
- Performance testing: LoadRunner, JMeter

📘 Resources:
- [Scalability Patterns](https://github.com/donnemartin/system-design-primer#scalability)

---

## ⛓️ Consistency, Availability, Partitioning (CAP)

- CAP Theorem
- Eventual vs Strong Consistency
- Leader-Follower Replication
- Quorum-based systems

📘 Resources:
- [CAP Theorem Explanation](https://www.youtube.com/watch?v=k-Yaq8AHlFA)

---

## 🔐 Security & Authentication

- OAuth 2.0, JWT, SAML
- TLS/SSL
- API key vs OAuth
- Rate limiting & Abuse Protection

📘 Resources:
- [JWT Guide](https://jwt.io/introduction)

---


## 🔁 Fault Tolerance & Redundancy

- Failover Strategies
- Heartbeats & Health Checks
- Redundancy & Replication
- Circuit Breakers & Retry Logic

📘 Resources:
- [Netflix Hystrix (Archived but Gold)](https://github.com/Netflix/Hystrix)

---

## Rate Limiting and  Throttling 
- Client-side vs server-side rate limiting
- Burst control and fair usage
- Message queues (Kafka, RabbitMQ, SQS)
- Asynchronous processing with background jobs
- Retry and dead-letter queue (DLQ) strategies

---

## 10. 📊 Monitoring and Observability 
- Metrics (latency, throughput, error rate)
- Logs vs traces vs metrics
- Tools: Prometheus, Grafana, ELK, Datadog
- Health checks and alerting
- SLOs, SLAs, SLIs

---

## ⚖️ Trade Offs & Design Decisions

> TBD

---

## 📚 Recommended Books & Courses

- **Designing Data-Intensive Applications** by Martin Kleppmann
- **System Design Interview** – Alex Xu (Vol 1 & 2)
- **Building Microservices** – Sam Newman
- [Grokking System Design Interview – Educative](https://www.educative.io/courses/grokking-the-system-design-interview)
- [High Scalability Blog](http://highscalability.com/)

---
