## Compute as a Service (AWS)

Compute as a Service on AWS provides the processing power needed to run applications in the cloud. AWS offers **three main compute models**, each suited to different workloads:

### 1. Virtual Machines (Amazon EC2)

Virtual machines emulate traditional physical servers and are the most familiar compute option for users with on-premises experience.

**Amazon EC2 (Elastic Compute Cloud)**

* Provides secure, resizable compute capacity in the cloud.
* Virtual servers are called **EC2 instances**.
* AWS manages the physical hardware, hypervisor, and underlying infrastructure.
* Supports workloads such as web hosting, applications, databases, and authentication services.
* Resources are elastic, disposable, and can be provisioned in seconds.

**Key EC2 Concepts**

* **Amazon Machine Image (AMI):**
  A template used to launch EC2 instances. Includes the OS, application server, applications, launch permissions, and block device mappings.
  AMIs can be:

  * AWS-provided
  * From AWS Marketplace
  * Custom-built manually or using EC2 Image Builder

* **Instance Types & Families:**
  EC2 offers hundreds of instance types with varying CPU, memory, storage, and networking capabilities. Instance families include:

  * General purpose
  * Compute optimized
  * Memory optimized
  * Accelerated computing
  * Storage optimized
  * High Performance Computing (HPC)

* **AWS Compute Optimizer:**
  Uses machine learning and CloudWatch metrics to recommend optimal compute configurations for better performance and lower cost.

* **Key Pairs:**
  Used for secure access to EC2 instances. AWS stores the public key; the user stores the private key.

* **Tenancy Options:**

  * Shared tenancy
  * Dedicated instances
  * Dedicated hosts (fully isolated physical servers, higher cost)

* **Placement Groups:**
  Control how instances are placed on underlying hardware:

  * **Cluster:** Low latency and high throughput (HPC workloads)
  * **Spread:** Critical instances separated for high availability
  * **Partition:** Large distributed workloads to reduce correlated failures

* **User Data:**
  Scripts or cloud-init instructions that run at instance launch to automate setup tasks such as patching, installing software, or configuring services.

---

### 2. Container Services

Containers package an application and its dependencies into a standardized, portable unit that runs consistently across environments.

**Containers vs Virtual Machines**

* Containers share the host OS and kernel.
* More lightweight than VMs.
* Start almost instantly.
* Ideal for applications that need fast scaling.
* VMs provide stronger OS isolation and more control.

**Amazon Elastic Container Service (ECS)**

* AWS-native container orchestration service.
* Containers are defined using **task definitions** (JSON blueprints).
* Tasks can run:

  * On **EC2 instances** (customer-managed)
  * On **AWS Fargate** (serverless)
* EC2 instances running the ECS agent are called **container instances**.
* Supports scaling, scheduling, permissions, and availability management.

**Amazon Elastic Kubernetes Service (EKS)**

* Managed Kubernetes service on AWS.
* Runs Kubernetes control plane without user management overhead.
* Uses Kubernetes concepts:

  * **Pods** instead of ECS tasks
  * **Worker nodes** instead of container instances
* Suitable for teams already using Kubernetes or needing advanced orchestration and fine-grained control.

---

### 3. Serverless Compute

Serverless allows applications to run without provisioning or managing servers.

**Core Characteristics of Serverless**

* No servers to manage
* Automatic scaling
* Pay only for usage (no idle cost)
* Built-in availability and fault tolerance

**AWS Fargate**

* Serverless compute engine for containers.
* Works with both Amazon ECS and Amazon EKS.
* Eliminates the need to manage EC2 instances or cluster capacity.
* Provides workload isolation and enhanced security.

**AWS Lambda**

* Runs code without managing servers or containers.
* Supports event-driven workloads and backend services.
* Automatically scales with demand.
* High availability by default.
* Charged per execution with sub-second billing.

---

### Summary Comparison

| Compute Model                   | Best Use Case                                             |
| ------------------------------- | --------------------------------------------------------- |
| **EC2 (VMs)**                   | Full control over OS, legacy apps, predictable workloads  |
| **Containers (ECS/EKS)**        | Portable, scalable apps with faster deployment            |
| **Serverless (Lambda/Fargate)** | Event-driven, microservices, no infrastructure management |

