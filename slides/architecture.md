## Cloud Architectures

----

### Hybrid Connectivity: Site-to-Site VPN

<img src="img/vpn-site-to-site.svg" alt="Site-to-Site IPsec VPN connecting On-Premises Datacenter to Cloud VNet" />

----

### Network Peering: VNet-to-VNet / VPC Peering

<img src="img/vnet-peering.svg" alt="VNet-to-VNet Peering across the private Cloud Backbone" />

----

### Remote Access: Point-to-Site VPN

<img src="img/vpn-point-to-site.svg" alt="Point-to-Site VPN connecting individual remote developer machines to a Cloud VNet" />

----

### Dedicated Interconnect: ExpressRoute / Direct Connect

<img src="img/expressroute.svg" alt="Dedicated private fiber connection via Azure ExpressRoute or AWS Direct Connect" />

----

### Cloud Landing Zones

> A pre-provisioned, secure, multi-account cloud foundation with built-in governance, networking, and identity guardrails

* Scales cloud adoption across dozens of teams without sacrificing security or cost control

----

### Landing Zone Architecture

<img src="img/landing-zone.svg" alt="Enterprise Cloud Landing Zone pillars and workload subscriptions" />

----

### Hub & Spoke Network Topology

<img src="img/hub-and-spoke.svg" alt="Hub and Spoke network topology centralizing firewall, hybrid connectivity, and shared services" />

----

### Cloud IAM & Zero-Trust Security

<img src="img/cloud-iam.svg" alt="Cloud Identity and Access Management (IAM): Who, What, and Where across the Resource Hierarchy" />

Note:
* In the Cloud, Identity is the new security perimeter.
* Every API call is authenticated and authorized using WHO (Principal) + WHAT (Role/Permissions) + WHERE (Resource Hierarchy).
* Never hardcode or commit static Service Account JSON keys or AWS Access Keys in Git! Use Workload Identity Federation / OIDC short-lived tokens.

----

### Data Sovereignty, Encryption & Compliance

> Controlling **where** your data lives, **who** holds the encryption keys, and **which jurisdiction** applies

* **Encryption Everywhere**: TLS 1.3 in transit + `AES-256` at rest by default (`Cloud KMS`, `Customer-Managed Encryption Keys — CMEK`, or Hardware Security Modules `Cloud HSM` / `BYOK`)
* **Regulatory Frameworks**: `GDPR` (EU data protection), `HIPAA` (Healthcare), `PCI-DSS` (Payments), `ISO 27001` & `SOC 2`
* **Sovereign Cloud & Extraterritorial Laws**: Addressing `US CLOUD Act` exposure via EU Data Boundary, `ANSSI SecNumCloud` (e.g., *S3NS*, *Bleu*), and Sovereign Controls

----

### Cloud Services Landscape

<img src="img/cloud-services-map.svg" alt="Overview of Cloud Services across Compute, Containers, Storage, Databases, Networking, AI, Security, and DevOps" />
