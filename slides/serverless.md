## Serverless

----

### What is Serverless?

> An architectural model where servers are completely abstracted away and billing is strictly tied to execution

* Not just a single product, but a **cloud-native architectural paradigm**
* Maximize focus on delivering business value rapidly and continuously

----

### Core Characteristics

* **Ephemeral Compute**: Functions spin up on demand when triggered and exist only for the duration of the request
* **Dynamic Auto-Scaling**: Instantaneous scaling from zero to thousands of concurrent executions, with built-in resilience
* **Fine-Grained Billing**: True **pay-per-invocation** (billed per millisecond of compute and request count)
* **Event-Driven**: Reacts natively to HTTP requests, queue messages, file uploads, database changes, or schedules

----

### Architectural Trade-offs

> Key constraints to keep in mind when designing Serverless systems

* **Stateless Execution**: No local state persists between invocations; state must live in external managed stores
* **Cold Starts**: Initial latency spike when spinning up a new execution environment from zero
* **Execution Limits**: Bounded execution duration (e.g., up to 15 minutes on `AWS Lambda`)
* **Vendor Lock-in**: Tight coupling with provider-specific triggers, IAM, and BaaS ecosystems

----

### Traditional vs Serverless Architecture

<img src="img/serverless-vs-traditional.svg" alt="Comparison between Traditional Always-On 3-Tier Architecture and Serverless Architecture" />

----

### Function-as-a-Service (FaaS)

> Deploying individual functions as the smallest unit of compute and business value

* **Ephemeral**: Lifecycle scoped to the request or event
* **Elastic**: Concurrency and fault tolerance handled transparently by the platform
* **Fine-Grained**: Pay only for actual compute time consumed (`AWS Lambda`, `Cloud Run Functions`, `Azure Functions`)

----

### Function-as-a-Service (FaaS)

<img src="img/faas.svg" alt="Function-as-a-Service platform routing requests from API Gateway to ephemeral function instances" />

----

### Backend-as-a-Service (BaaS)

> Turnkey managed APIs and cloud services that replace custom backend components

* Consume authentication (`Auth0`, `Cognito`, `Firebase Auth`), databases (`DynamoDB`, `Firestore`), and object storage (`S3`) directly via SDKs
* Built-in scalability, global replication, and managed security out of the box

----

### Backend-as-a-Service (BaaS)

<img src="img/baas.svg" alt="Backend-as-a-Service connecting client applications to managed Authentication, Object Storage, and Databases" />

----

### Event-Driven Auto-Scaling

> Unlike IaaS or traditional PaaS, scaling is instantaneous and driven directly by incoming events

* No need to pre-warm VM pools or tune CPU threshold rules — each event automatically triggers the required compute capacity

----

### Scale to Zero

> When there is no traffic, resource consumption drops to zero — and **so does your bill**

* Ideal for spiky workloads, dev/test environments, and new products finding product-market fit

----

### From IaaS to FaaS

* **IaaS** gives maximum control and flexibility (ideal for Lift-and-Shift or custom kernels), but requires managing all the infrastructure plumbing
* **FaaS / Serverless** maximizes developer velocity and **Time-to-Market**, trading low-level control for operational simplicity

----

### Agility & DevOps Synergy

* Serverless unlocks the full potential of **DevOps** and **Agile** delivery
* Leverages native cloud superpowers: event-driven auto-scaling, elasticity, and fine-grained pay-per-use cost models
* Naturally aligns with modern software engineering practices (`12-Factor App`, microservices, CI/CD)

----

### Operational Challenges

* **Stateless Design**: Requires rethinking data access, caching, and connection pooling
* **Application-Level Security**: Shift from perimeter firewall security to fine-grained zero-trust IAM per function
* **Testing Strategy**: Local emulation is harder; relies heavily on unit testing (`TDD`/`BDD`) and ephemeral cloud test environments
* **Distributed Observability**: Requires distributed tracing, structured logging, and FinOps cost monitoring

----

### Common Use Cases

* **REST / GraphQL APIs & Microservices**
* **Real-Time Stream & Event Processing**
* **IoT Ingestion & Event-Driven Workflows**
* **Scheduled Cron Jobs & Batch Tasks**
* **Burst Parallel Compute (Image/Video/Document Processing)**

----

### Serverless Reference Architecture

<img src="img/serverless-architecture.svg" alt="Event-Driven Serverless Reference Architecture" />
