# Cloud in a Nutshell

An interactive presentation on **Cloud Computing (`SaaS`, `IaaS`, `PaaS`, `Serverless`), Cloud Migration, and Enterprise Cloud Architectures**, powered by [Reveal.js 6.0.2](https://revealjs.com/).

* **Live Presentation:** [https://devops-cloud-courses.github.io/cloud](https://devops-cloud-courses.github.io/cloud)
* **PDF Export View:** [https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false](https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false)

---

## Course Curriculum

1. **Overview & History of the Cloud** (`slides/cloud.md`)
   * Computing history: Mainframes (1950s–1970s) → Physical x86 Servers → Hypervisors & Virtual Machines → Cloud Computing
   * Essential Cloud Characteristics (`NIST`) & economic shift (`CapEx` vs. `OpEx`)
   * The Shared Responsibility Model across On-Premises, `IaaS`, `PaaS`, `FaaS / Serverless`, and `SaaS`
2. **Software-as-a-Service (`SaaS`)** (`slides/saas.md`)
   * Turnkey cloud software consumption & popular enterprise/consumer SaaS ecosystems
3. **Infrastructure-as-a-Service (`IaaS`)** (`slides/iaas.md`)
   * **Elasticity & Scale**: Vertical vs. Horizontal Scaling, Elasticity, Auto-Scaling, and On-Demand Self-Service
   * **Global Infrastructure**: Cloud Regions, Hyperscaler Private Subsea Fiber Backbone & Edge CDN PoPs (Cold-Potato Routing), and Availability Zones (`AZ`)
   * **Compute, Storage & Networking**: Hardware-offloaded hypervisors (`AWS Nitro`, `Google Titanium`, `Azure Boost`), custom ARM silicon (`Graviton4`, `Axion`, `Cobalt 100`), GPU/TPU AI accelerators (`NVIDIA Blackwell B200` / `H200`, `TPU v6e`), Regional/Zonal SKU availability, Cloud Storage Taxonomy (`Block`, `File`, `Object` & Lifecycle Tiers), and Software-Defined Networking (`VPC` / `VNet`, `NSG`, `WAF`)
   * **Cloud-Native Operations & Delivery**: Pets vs. Cattle, Mutable vs. Immutable Infrastructure (`Packer`, `Docker`), Infrastructure as Code (`Terraform` / `OpenTofu`), Zero-Downtime Rolling Updates, Blue/Green, Canary Releases, and A/B Testing
   * **Reliability & Resilience Engineering**: SLA & "The Table of Nines", Composite SLA Math (Serial vs. Parallel Multi-AZ Redundancy), Backups, Disaster Recovery Plans (`DRP`), `RTO` & `RPO` Timelines, Chaos Engineering & the Netflix Simian Army + Modern Chaos Tooling (`AWS FIS`, `Azure Chaos Studio`, `Gremlin`, `Chaos Mesh`, `LitmusChaos`), and Multi-AZ IaaS Reference Architecture
4. **Platform-as-a-Service (`PaaS`)** (`slides/paas.md`)
   * Evolution from First-Gen PaaS (`Heroku`, `App Engine`, `Cloud Foundry`) to Modern Managed Cloud PaaS (`Cloud Run`, `Azure App Service` / `Container Apps`, `AWS App Runner`)
   * Managed Services, Turnkey Multi-Region Geo-Replication (`AlloyDB`, `Cloud Spanner`, `Cosmos DB`, `Aurora`), Automated PITR Backups & DR, API-Driven Design, Private & Hybrid PaaS (`OpenShift`, `Azure Arc`, `Google Distributed Cloud`), and Lakehouse/GenAI PaaS Reference Architecture (`BigQuery`, `Microsoft Fabric`, `Vertex AI`, `AWS Bedrock`)
5. **Serverless (`FaaS` & `BaaS`)** (`slides/serverless.md`)
   * Core Serverless characteristics, Architectural Trade-offs, and Traditional 3-Tier vs. Serverless Architecture
   * Function-as-a-Service (`AWS Lambda`, `Google Cloud Run Functions`, `Azure Functions`) & Backend-as-a-Service (`Auth0`, `Firebase`, `Supabase`, `DynamoDB`, `Firestore`)
   * Event-Driven Auto-Scaling, Scale to Zero, Operational Challenges (Cold Starts, Distributed Tracing), and Serverless Reference Architecture
6. **Cloud Migration (`The "R"s`)** (`slides/advanced.md`)
   * Cloud Migration Decision Tree & Pathways: **Retain**, **Retire**, **Relocate**, **Rehost** (Lift & Shift), **Replatform** (Lift & Reshape), **Repurchase** (Move to SaaS), and **Refactor** (Re-architect to Cloud-Native)
7. **Enterprise Cloud Architectures & Governance** (`slides/architecture.md`)
   * **Hybrid & Multi-VPC Networking**: Point-to-Site VPN, Site-to-Site IPsec VPN, Dedicated Private Interconnect (`ExpressRoute` / `Direct Connect` / `Cloud Interconnect`), `VPC` / `VNet` Peering, and Hub & Spoke Topology
   * **Governance, Identity & Compliance**: Multi-Account Cloud Landing Zones, Cloud IAM & Zero-Trust Security (`RBAC`, `ABAC`, Workload Identity Federation / `OIDC`), Data Sovereignty, Customer-Managed Encryption (`KMS` / `HSM`), and Regulatory Compliance (`GDPR`, `DORA`, `NIS2`, `HIPAA`, `ISO 27001`, `SOC 2`, `SecNumCloud`, `EU AI Act`)
   * **Cloud Services Landscape**: 360° taxonomy across Compute, Storage, Managed Databases (`Aurora`, `AlloyDB`, `Valkey`), Networking, Data/AI (`BigQuery`, `Fabric`, `Vertex AI`, `Bedrock`), Security (`CNAPP` / `CSPM`), and DevOps/FinOps/GreenOps (`OpenTelemetry`, `Terraform` / `OpenTofu`)
8. **Well-Architected Framework & Conclusion** (`slides/conclusion.md`)
   * The **6 Pillars of the Cloud Well-Architected Framework** (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization / FinOps, Sustainability / GreenOps) & Further Reading

---

## Repository Structure

```text
.
├── index.html          # Reveal.js 6.0.2 entrypoint (jsDelivr CDN, zero-build setup)
├── css/
│   └── custom.css      # Custom light theme, typography (Inter & JetBrains Mono), and responsive layout
├── img/                # Custom vector SVG architecture diagrams & author avatars
└── slides/             # Modular Markdown slide decks loaded dynamically by Reveal.js
```

---

## Running Locally

Because Reveal.js loads external Markdown files (`slides/*.md`) via `fetch`, serve the repository over a local HTTP server rather than opening `index.html` via `file://`:

### Option 1: Python (built-in)
```bash
python3 -m http.server 8000
```
Then open [http://localhost:8000](http://localhost:8000).

### Option 2: Node.js (`npx`)
```bash
npx serve .
```

### Option 3: Docker (`nginx`)
```bash
docker run --rm -p 8080:80 -v "$PWD":/usr/share/nginx/html:ro nginx:alpine
```
Then open [http://localhost:8080](http://localhost:8080).

---

## Exporting to PDF (Chrome / Chromium)

1. Open [https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false](https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false)
2. Press `Cmd + P` (macOS) or `Ctrl + P` (Windows/Linux)
3. Configure the print dialog settings:

| Setting | Value |
|---|---|
| **Destination** | Save as PDF |
| **Pages** | All |
| **Margins** | None / Default |
| **Options** | Enable **Background graphics** |

---

## Authors

* **Laurent Grangeau** — Cloud Solution Architect @ Google ([@laurentgrangeau](https://twitter.com/laurentgrangeau) | [github.com/laurentgrangeau](https://github.com/laurentgrangeau))
* **Arthur Mauvezin** — DevOps Engineer @ Ouidou Consulting ([@arthurmauvezin](https://twitter.com/arthurmauvezin) | [github.com/arthurmauvezin](https://github.com/arthurmauvezin))
