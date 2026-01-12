## Cloud Storage (AWS)

AWS cloud storage services are designed to store data reliably, securely, and at scale. There are **three primary storage types** in AWS, each optimized for different use cases:

* **Block storage**
* **File storage**
* **Object storage**

---

## 1. Block Storage

Block storage stores data in fixed-size blocks and is typically used with compute services like EC2.

### Amazon EC2 Instance Store

* Temporary **block-level storage** physically attached to the EC2 host.
* **Ephemeral**: data is lost when the instance is stopped or terminated.
* Tied directly to the lifecycle of the EC2 instance.
* Best suited for:

  * Buffers and caches
  * Scratch data
  * Temporary data
  * Distributed workloads that replicate data (e.g., Hadoop clusters)
* Offers very high performance due to local attachment.

-----

### Amazon Elastic Block Store (Amazon EBS)

Amazon EBS provides **persistent block storage** that can be attached to EC2 instances.

**Key Characteristics**

* **Detachable**: Volumes can be detached and reattached to another EC2 instance in the same Availability Zone.
* **Persistent**: Data remains even if the EC2 instance is stopped or terminated.
* **Size-limited**: Volumes have a maximum size.
* **One-to-one attachment**: Most EBS volumes attach to a single EC2 instance.
* **Multi-Attach**: Supported for io1 and io2 volumes (same AZ, limited instance types).

---

### EBS Volume Types

#### SSD Volumes (Transactional workloads)

* Designed for frequent read/write operations and low latency.

**Types**

* **gp3 / gp2** – General purpose, balanced performance and cost
* **io1 / io2 Block Express** – High-performance, latency-sensitive workloads
* Supports provisioned IOPS
* Multi-attach supported only on io1/io2

-----

#### HDD Volumes (Throughput workloads)

* Optimized for large, sequential workloads.

**Types**

* **st1** – Throughput Optimized HDD (frequently accessed data)
* **sc1** – Cold HDD (infrequently accessed data)
* Lower cost, higher throughput, lower IOPS

-----

### Amazon EBS Benefits

* Automatically replicated within an Availability Zone
* Data persists independently of EC2 lifecycle
* Supports encryption at rest
* Volumes can be modified without stopping instances
* Supports backups through snapshots

---

### Amazon EBS Snapshots

* Used to back up EBS volumes.
* **Incremental backups**: only changed blocks are saved.
* Stored in Amazon S3.
* Reduce storage costs and improve backup efficiency.

--------

## 2. File Storage

File storage allows multiple systems to access shared files using a hierarchical file system.

### Amazon Elastic File System (Amazon EFS)

* Fully managed, elastic file system.
* Automatically scales up and down as files are added or removed.
* Supports thousands of concurrent connections.
* Accessible from AWS and on-premises environments.
* Pay only for storage used.

**Storage Classes**

* **EFS Standard / Standard-IA** – Multi-AZ, high durability and availability
* **EFS One Zone / One Zone-IA** – Single AZ, lower cost

---

### Amazon FSx

Fully managed, high-performance file systems for specific workloads.

**FSx Options**

* **FSx for NetApp ONTAP**

  * Enterprise-grade features
  * Drop-in replacement for on-prem NetApp systems
  * Supports Linux, Windows, macOS

* **FSx for OpenZFS**

  * Designed for Linux-based and ZFS workloads
  * High performance for small-file and latency-sensitive workloads
  * Built-in snapshots and cloning

* **FSx for Windows File Server**

  * Fully managed Windows-native file system
  * Accessible via SMB
  * Ideal for Windows-based applications

* **FSx for Lustre**

  * High-performance file system for compute-intensive workloads
  * Extremely high throughput and IOPS
  * Integrates with Amazon S3 for data processing

---

## 3. Object Storage

### Amazon Simple Storage Service (Amazon S3)

Amazon S3 is a **standalone object storage service** not tied to compute.

**Core Concepts**

* Data stored as **objects** (data + metadata)
* Objects stored in **buckets**
* Flat storage structure
* Each object uniquely identified by:

  * Bucket name
  * Object key
  * Version ID
* Buckets are region-specific

---

### Amazon S3 Use Cases

* Backup and recovery
* Media hosting (images, videos, music)
* Software distribution
* Data lakes
* Static website hosting
* Static content storage

---

### Amazon S3 Storage Classes

* **S3 Standard**

  * General-purpose storage
  * High durability and availability

* **S3 Intelligent-Tiering**

  * Automatically moves data between tiers based on access patterns
  * Ideal for unknown or changing access patterns

* **S3 Standard-IA**

  * Infrequently accessed data with rapid retrieval
  * Lower storage cost, retrieval fee applies

* **S3 One Zone-IA**

  * Stored in a single Availability Zone
  * Lower cost, reduced resilience

* **S3 Express One Zone**

  * Low-latency, high-performance workloads in a single AZ

* **S3 Glacier Instant Retrieval**

  * Archive data with millisecond access
  * Lower cost than Standard-IA

* **S3 Glacier Flexible Retrieval**

  * Archive data accessed 1–2 times per year
  * Retrieval in minutes to hours

* **S3 Glacier Deep Archive**

  * Lowest-cost storage
  * Long-term retention (7–10+ years)
  * Default retrieval time ~12 hours
  * Ideal for compliance and regulatory data

---

### Storage Type Summary

| Storage Type | AWS Services        | Best For                                   |
| ------------ | ------------------- | ------------------------------------------ |
| Block        | EBS, Instance Store | Databases, OS disks, low-latency workloads |
| File         | EFS, FSx            | Shared file systems, enterprise workloads  |
| Object       | S3                  | Backups, media, data lakes, static content |

---

