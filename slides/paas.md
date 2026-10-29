## PaaS

----

### Platform-as-a-Service

> A managed platform to build, run, and scale applications without managing the underlying servers, OS, or middleware

* Developers focus on **application code, data, and architecture**
* The Cloud Provider manages OS patching, runtime updates, load balancing, and high availability

----

### Historical & Modern PaaS Platforms

<img src="img/paas-platforms.svg" alt="Evolution of PaaS from Heroku and Google App Engine to Modern Cloud PaaS" />

----

### Key Benefits of PaaS

* **Zero OS Maintenance**: No operating system installation, hardening, or kernel upgrades
* **Automatic Security Patching**: Underlying runtimes and middleware stay patched automatically
* **Built-in High Availability**: Native multi-AZ resilience with contractual SLAs (`> 99.9%` to `99.999%`)
* **Faster Time-to-Market**: Ship features instead of managing infrastructure plumbing

----

### Managed Services

> The Cloud Provider guarantees platform scalability, resilience, and patch levels

* The customer focuses on **selecting and composing the right managed services** to meet business requirements

----

### Turnkey Geo-Replication

> Multi-region data replication and failover are built natively into PaaS offerings

* Replicate databases (`AlloyDB`, `Cloud Spanner`, `Cosmos DB`, `Aurora`) or object storage across continents with a single configuration setting

----

### Automated Backup & Disaster Recovery

> Point-in-time recovery (PITR) and cross-region backups are handled by the Cloud Provider

* Disaster Recovery shifts from a complex engineering project to a **configuration checkbox or single IaC attribute**

----

### API-Driven by Design

> Every PaaS building block is provisioned, configured, and consumed via standard APIs

* Makes composing rich, cloud-native architectures fast, repeatable, and automation-friendly

----

### Private & Hybrid PaaS

> Running a PaaS developer experience on-premises or across hybrid environments

* `Red Hat OpenShift` / `Kubernetes` Internal Developer Platforms
* `Azure Local` / `Azure Arc`
* [`Google Distributed Cloud`](https://cloud.google.com/distributed-cloud)

----

### PaaS Reference Architecture

<img src="img/paas-architecture.svg" alt="Managed PaaS Application and Data Analytics Architecture" />
