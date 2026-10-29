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

### Virtual Machines by Availability Zone

<img src="img/vm-by-az.svg" alt="Comparison of available CPU platforms, machine families, and GPUs across Availability Zones" />

Note:
* Not all Availability Zones have identical underlying hardware!
* Newer CPU generations (Sapphire Rapids, AMD Genoa), GPU/TPU accelerators, and UltraMem instances (11.5 TB RAM) are rolled out selectively per zone.
* Always verify that your required machine SKU is available across at least 2 or 3 AZs before designing a High Availability deployment.

----

### Virtual Machines

> Decoupling compute (`vCPU`, `RAM`) from persistent network storage and physical hardware

* Powered by modern lightweight hypervisors (`AWS Nitro` / `KVM`, `Azure Hyper-V`, `Google KVM`)
* Hundreds of specialized machine families (General Purpose, Compute-Optimized, Memory-Optimized, GPU/TPU Accelerated)

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
* Up to 448–896 vCPUs and 24–32 TiB of RAM (for in-memory databases like SAP HANA)!
* Block storage (AWS EBS, Azure Managed Disks, GCP Persistent Disk) is network-attached and persists independently of the VM lifecycle.

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

### Software-Defined Networking

* Configure the entire network topology via software and APIs
* Isolate environments using Virtual Private Clouds (`VPC` / `VNet`) and private subnets
* Enforce fine-grained security with Stateful Firewalls, Security Groups (`NSG`), and Web Application Firewalls (`WAF`)

----

### Infrastructure as Code (IaC)

```hcl
resource "azurerm_linux_virtual_machine" "web" {
  name                = "vm-web-prod-01"
  resource_group_name = azurerm_resource_group.main.name
  location            = "West Europe"
  size                = "Standard_D2s_v5"
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

### The Netflix Simian Army (Cont.)

* **Latency Monkey**: Injects artificial network delays or packet loss to test timeout and circuit-breaker resilience
* **Doctor Monkey**: Detects unhealthy instances (`CPU` spikes, memory leaks, failing health checks) and removes them for root-cause analysis
* **Janitor Monkey**: Identifies and deletes unused resources to reduce cloud waste (FinOps)
* **Security & Conformity Monkeys**: Flag or terminate instances that violate security policies or architectural standards

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

### Zero-Downtime Rolling Deployment

<img src="img/rolling-update.svg" alt="Rolling update replacing instances one by one with zero downtime" />

----

### IaaS Reference Architecture

<img src="img/iaas-architecture.svg" alt="Multi-AZ High Availability IaaS Architecture in a VPC" />
