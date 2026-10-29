## IaaS

----

### Infrastructure-as-a-Service

> On-demand virtualized compute, storage, and networking building blocks

* Direct replacement for physical datacenters with full OS-level control
* Enables rapid provisioning and **Lift-and-Shift** migrations
* You manage the OS, middleware, runtime, data, and applications

----

### Scalability

* **Vertical Scaling (Scale Up / Down)**
  * Increase the size of an existing machine (`CPU`, `RAM`, `Storage`)
  * Simple, but hits hardware limits and often requires a reboot
* **Horizontal Scaling (Scale Out / In)**
  * Add or remove server instances working in parallel behind a load balancer
  * Enabled by stateless design, sharding, microservices, or partitioning

----

### Elasticity

> The ability to dynamically and automatically grow or shrink infrastructure resources to match real-time demand

* Avoids both **over-provisioning** (wasted money during off-peak hours) and **under-provisioning** (outages during traffic spikes)

----

### Auto-Scaling

> Automatically maintaining the desired fleet capacity and availability based on real-time signals

* Continuously monitors health checks, `CPU`, `RAM`, queue depth, or custom request metrics
* Automatically replaces unhealthy instances and scales the fleet up or down

----

### On-Demand Self-Service

> Provision or destroy cloud resources in seconds via Web Console, CLI, or API

* No procurement delays, hardware shipping, or manual IT tickets required
* Empowers engineering teams to iterate and experiment rapidly

----

### Global Cloud Regions

<img src="img/cloud-regions.svg" alt="Global Cloud Regions across Americas, EMEA, and Asia-Pacific" />

----

### Global Backbone Network & Edge CDN

<img src="img/cloud-global-network.svg" alt="Hyperscaler Global Fiber Network and Edge CDN Points of Presence" />

Note:
* Hyperscalers invest billions in private transoceanic subsea fiber cables and 200+ Edge PoPs worldwide.
* With Cold-Potato Routing, user traffic enters the provider's private fiber backbone at the nearest city Edge PoP (< 10 ms) rather than bouncing across congested public internet hops.

----

### Availability Zones (AZ)

<img src="img/availability-zones.svg" alt="Cloud Region composed of 3 isolated Availability Zones" />

Note:
* Question for the audience: How many servers are inside a hyperscale datacenter complex (like Dublin or Virginia)?
* Hundreds of thousands to over 1 million servers across a region.
* Each Availability Zone is one or more discrete datacenters with redundant power, cooling, and networking, isolated from disasters in other AZs.

----

### Virtual Machines

> Decoupling compute (`vCPU`, `RAM`) from persistent network storage and physical hardware

* Powered by hardware-offloaded hypervisors (`AWS Nitro`, `Google Titanium`, `Azure Boost`)
* Custom hyperscaler ARM silicon (`AWS Graviton4`, `Google Axion`, `Azure Cobalt 100`) alongside `Intel Xeon` & `AMD EPYC`
* Hundreds of specialized machine families (General Purpose, Compute/Memory-Optimized, `NVIDIA Blackwell` / `TPU` AI Accelerated)

----

### Instance Sizing Templates

| Instance Type | vCPU | Memory (GiB) | Storage | Network Bandwidth |
|---|---|---|---|---|
| `m7i.large` | 2 | 8 GiB | EBS (NVMe) | Up to 12.5 Gbps |
| `m7i.xlarge` | 4 | 16 GiB | EBS (NVMe) | Up to 12.5 Gbps |
| `m7i.2xlarge` | 8 | 32 GiB | EBS (NVMe) | Up to 15 Gbps |
| `m7i.4xlarge` | 16 | 64 GiB | EBS (NVMe) | Up to 20 Gbps |
| `m7i.12xlarge` | 48 | 192 GiB | EBS (NVMe) | 22.5 Gbps |

Note:
* What is the largest VM available in the cloud today?
* Up to 896–1,920 vCPUs and 24–32 TiB of RAM (`GCP X4` / `AWS u7i-32tb.224xlarge` for SAP HANA in-memory databases)!
* Block storage (`AWS EBS`, `Azure Managed Disks`, `GCP Hyperdisk`) is network-attached and persists independently of the VM lifecycle.

----

### Virtual Machines by Availability Zone

<img src="img/vm-by-az.svg" alt="Comparison of available CPU platforms, machine families, and GPUs across Availability Zones" />

Note:
* Not all Regions and Availability Zones have identical underlying hardware!
* Latest CPU generations (`Intel Granite Rapids C4/N4`, `AMD Genoa/Turin C3D/C4D`, `Google Axion ARM C4A`), AI accelerators (`NVIDIA Blackwell B200` / `H200`, `TPU v6e Trillium`), and `32 TB X4 UltraMem` instances roll out selectively per zone.
* Always verify that your required machine SKU is available across at least 2 or 3 AZs before designing a High Availability deployment.

----

### Cloud Storage Taxonomy: Block, File & Object

<img src="img/cloud-storage-types.svg" alt="Comparison of Cloud Block Storage, File Storage, Object Storage, and Lifecycle Tiers" />

Note:
* Block Storage (SAN): Raw volumes attached to a single VM via NVMe/SCSI (< 1 ms latency) — ideal for boot disks and relational databases.
* File Storage (NAS): Shared POSIX/NFS/SMB file system mounted concurrently across multiple VMs or containers.
* Object Storage (S3 / GCS / Azure Blob): Flat REST API namespace, virtually infinite scale, 99.999999999% (11 nines) durability, with automated lifecycle policies transitioning aging data from Standard (Hot) to Nearline, Coldline, and Archive tiers.

----

### Software-Defined Networking

* Configure the entire network topology via software and APIs
* Isolate environments using Virtual Private Clouds (`VPC` / `VNet`) and private subnets
* Enforce fine-grained security with Stateful Firewalls, Security Groups (`NSG`), and Web Application Firewalls (`WAF`)

----

### Pets vs Cattle

<img src="img/pets-vs-cattle.svg" alt="Comparison between Pets (manually managed servers) and Cattle (automated fleet)" />

Note:
* Stop treating servers as unique, irreplaceable individuals.
* If an instance acts up, don't spend days debugging it via SSH — terminate it and let the Auto Scaling Group spin up a fresh replacement.

----

### Immutable Infrastructure: The Problem

<img src="img/mutable-infra.svg" alt="Configuration drift on mutable Phoenix servers" />

----

### Immutable Infrastructure: The Solution

<img src="img/immutable-infra.svg" alt="Immutable infrastructure lifecycle replacing servers with new versioned images" />

----

### Immutable Infrastructure: Tools

* Bake golden images containing OS hardening, security patches, and dependencies
* Package application releases into versioned machine or container images (`Packer`, `Docker`)
* Trigger image rebuilds automatically via `Git` and CI/CD pipelines

----

### Infrastructure as Code (IaC)

```hcl
resource "azurerm_linux_virtual_machine" "web" {
  name                = "vm-web-prod-01"
  resource_group_name = azurerm_resource_group.main.name
  location            = "West Europe"
  size                = "Standard_D4s_v6"
  admin_username      = "azureuser"

  admin_ssh_key {
    username   = "azureuser"
    public_key = file("~/.ssh/id_ed25519.pub")
  }

  source_image_reference {
    publisher = "Canonical"
    offer     = "ubuntu-24_04-lts"
    sku       = "server"
    version   = "latest"
  }
}
```

----

### Zero-Downtime Rolling Deployment

<img src="img/rolling-update.svg" alt="Rolling update replacing instances one by one with zero downtime" />

----

### Blue/Green Deployment

<img src="img/blue-green.svg" alt="Blue/Green deployment switching 100% traffic between two identical environments" />

----

### Canary Release

<img src="img/canary-release.svg" alt="Canary deployment routing 5% of traffic to the new version" />

----

### A/B Testing

<img src="img/ab-testing.svg" alt="A/B testing splitting user cohorts to measure business conversion" />

----

### SLA & "The Table of Nines"

> **Service Level Agreement (SLA)**: Contractual uptime commitment backed by financial credits

| Availability (SLA) | Max Downtime / Year | Max Downtime / Month | Typical Cloud Tier |
|---|---|---|---|
| `99%` ("Two Nines") | **3.65 days** | 7h 18m | Non-critical batch / Dev |
| `99.9%` ("Three Nines") | **8h 45m** | 43m 50s | Single-Instance VM (Premium SSD) |
| `99.95%` | **4h 22m** | 21m 55s | Multi-AZ Regional Managed DB |
| `99.99%` ("Four Nines") | **52m 36s** | 4m 23s | Multi-AZ VMs + Load Balancer |
| `99.999%` ("Five Nines") | **5m 15s** | 26s | Global Multi-Region Active-Active |

----

### Composite SLA Math: Serial vs. Parallel

<img src="img/composite-sla.svg" alt="Composite SLA calculation comparing serial dependencies against parallel Multi-AZ redundancy" />

Note:
* Serial dependencies multiply down: 99.95% × 99.9% × 99.9% = 99.75% (~22 hours of downtime/year).
* Parallel Multi-AZ redundancy multiplies the failure probability: two independent zones at 99.9% each have a 0.1% (0.001) failure chance, so the probability both fail simultaneously is 0.001 × 0.001 = 0.000001 → 99.9999% availability!

----

### Backup & Restore

> Moving to IaaS does **not** eliminate the need for backups

* Under the Shared Responsibility Model, **protecting your data is your responsibility**
* Always configure automated snapshots, cross-region replication, and regular restore tests

Note:
* Question: What is the uptime SLA of a single standalone VM without redundant disks or availability zones?
* Often limited or requires multi-AZ deployment — it is up to the cloud architect to design for resilience and automated backups.

----

### DRP (Disaster Recovery Plan)

> A documented, tested set of automated procedures to recover and restore IT infrastructure after a major outage or disaster

* Moving to the cloud does not replace a DRP — it makes executing and testing your DRP faster, cheaper, and programmable

----

### RTO & RPO Objectives

* **RTO (Recovery Time Objective)**: Maximum acceptable duration of service downtime after an incident before business impact becomes critical
* **RPO (Recovery Point Objective)**: Maximum acceptable age of data that can be lost due to an incident (determines backup/replication frequency)

----

### RTO / RPO Timeline

<img src="img/rto-rpo.svg" alt="RPO and RTO timeline diagram around an outage" />

----

### Chaos Engineering

<img src="img/chaos-engineering.svg" alt="Chaos Engineering blast radius levels: Chaos Monkey, Chaos Gorilla, Chaos Kong" />

Note:
* Pioneered by Netflix during their migration to AWS.
* Instead of waiting for failures to happen at 3 AM on a Sunday, proactively inject controlled failures during business hours to verify that systems auto-heal.

----

### The Netflix Simian Army

* **Chaos Monkey**: Randomly terminates production instances to ensure services survive server failures
* **Chaos Gorilla**: Simulates an entire Availability Zone outage to verify multi-AZ failover
* **Chaos Kong**: Simulates a complete Cloud Region outage to validate cross-region resilience

----

### Simian Army & Modern Chaos Tooling

* **Latency & Doctor Monkeys**: Inject network delays/packet loss to test circuit breakers, and auto-replace unhealthy instances
* **Janitor & Security Monkeys**: Reclaim unused cloud waste (FinOps) and terminate non-compliant resources (now **CSPM / CNAPP**)
* **Managed Cloud Chaos Services**: `AWS Fault Injection Service (FIS)`, `Azure Chaos Studio`, `Gremlin`
* **Cloud-Native Chaos Platforms**: `Chaos Mesh` and `LitmusChaos` (CNCF) for automated fault injection in CI/CD pipelines

----

### IaaS Reference Architecture

<img src="img/iaas-architecture.svg" alt="Multi-AZ High Availability IaaS Architecture in a VPC" />
