## Database Services (AWS)

AWS provides a wide range of **purpose-built database services** designed to support different data models and workloads. Choosing the right database improves **availability, scalability, latency, and performance**.

---

## Relational vs Non-Relational Databases

### Relational Databases (SQL)

* Data stored in **tables (rows and columns)** with predefined schemas.
* Enforces strict schema rules and data integrity.
* Data relationships are clearly defined.
* Suitable when:

  * Data structure is well defined
  * Extreme read/write performance is not required
  * Data consistency is critical

**Examples**

* Oracle
* Microsoft SQL Server
* MySQL
* PostgreSQL

---

### Non-Relational Databases (NoSQL)

* Designed for **specific data models** with flexible schemas.
* Highly scalable and optimized for performance.
* Often scale **horizontally**.
* Suitable when:

  * Data does not fit rigid schemas
  * High read/write throughput is required
  * Applications need massive scalability

**Common data models**

* Key-value
* Document
* Graph
* Time-series
* In-memory

---

## Managed vs Unmanaged Databases

When running databases on AWS, you can choose between:

* **Unmanaged**: Install and manage databases yourself on EC2
* **Managed**: AWS handles provisioning, patching, backups, scaling, and availability

Managed services reduce operational overhead and let you focus on application logic.

---

## Amazon Relational Database Service (Amazon RDS)

Amazon RDS is a **fully managed relational database service**.

### Key Benefits

* No need to manage infrastructure
* Automated backups, patching, and recovery
* Built-in scaling and high availability
* Focus on application development instead of database administration

### Supported Engines

* **Commercial**: Oracle, SQL Server
* **Open source**: MySQL, PostgreSQL, MariaDB
* **Cloud-native**: Amazon Aurora

---

### RDS Database Instances

* A **DB instance** is the compute resource running the database engine.
* Built on EC2 infrastructure, but managed through the RDS console.
* Instance class determines CPU and memory.
* One DB instance can host:

  * Multiple databases
  * Multiple tables per database

---

## Purpose-Built Databases on AWS

AWS offers **15+ purpose-built database engines**, allowing architects to select the best database for each workload instead of using a one-size-fits-all approach.

---

### Amazon DynamoDB

* Fully managed **NoSQL key-value and document database**
* Designed for **high-scale and serverless applications**
* Predictable performance at any scale
* Automatically replicated across multiple Availability Zones
* Data stored on SSDs

**Core Components**

* **Tables** – collections of items
* **Items** – individual records
* **Attributes** – key-value data
* **Primary keys** – uniquely identify items
* **Secondary indexes** – enable flexible querying

**Use Cases**

* Internet-scale applications
* Media metadata stores
* Gaming platforms (leaderboards, player data)
* Retail workloads (shopping carts, inventory, customer profiles)

---

### Amazon ElastiCache

* Fully managed **in-memory caching service**
* Supports:

  * Redis
  * Memcached
* Improves application performance by reducing database load
* AWS manages failover, backups, and patching

---

### Amazon MemoryDB for Redis

* Redis-compatible, **durable in-memory database**
* Microsecond read latency, millisecond write latency
* Multi-AZ durability
* Can be used as a **primary database**, not just a cache
* Ideal for microservices architectures

---

### Amazon DocumentDB (MongoDB compatible)

* Fully managed **document database**
* Designed for rich, semi-structured data
* API compatible with MongoDB
* Common use cases:

  * Content management systems
  * User profiles
  * Web and mobile applications

---

### Amazon Keyspaces (for Apache Cassandra)

* Managed, Cassandra-compatible NoSQL database
* Highly scalable and available
* Designed for **high-volume workloads**
* Uses existing Cassandra Query Language (CQL)
* Ideal for straightforward access patterns at scale

---

### Amazon Neptune

* Fully managed **graph database**
* Optimized for highly connected data
* Common use cases:

  * Recommendation engines
  * Fraud detection
  * Knowledge graphs

---

### Amazon Timestream

* Serverless **time-series database**
* Built for IoT and operational data
* Handles trillions of events per day
* Faster and cheaper than relational databases for time-based data
* Used for metrics like:

  * Sensor readings
  * Stock prices
  * System performance data

---

## Database Selection Summary

| Database Type     | AWS Service            | Best Use Case                 |
| ----------------- | ---------------------- | ----------------------------- |
| Relational        | Amazon RDS / Aurora    | Structured data, transactions |
| Key-Value / NoSQL | DynamoDB               | High-scale, serverless apps   |
| In-Memory         | ElastiCache / MemoryDB | Low-latency workloads         |
| Document          | DocumentDB             | Semi-structured data          |
| Graph             | Neptune                | Relationship-heavy data       |
| Time-Series       | Timestream             | IoT and metrics data          |

**exam-style “When to use X vs Y” tables**
