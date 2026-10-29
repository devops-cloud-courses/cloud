# Cloud in a Nutshell

A comprehensive Cloud Computing & Architecture presentation built with **Reveal.js 6.0.2**, custom vector SVG architecture diagrams, and Markdown slides.

* **Live Presentation**: **https://devops-cloud-courses.github.io/cloud**

> This course is open source. Feel free to use, adapt, and share it!

---

## Authors

* **Laurent Grangeau** — Cloud Solution Architect @ Google ([@laurentgrangeau](https://twitter.com/laurentgrangeau) | [github.com/laurentgrangeau](https://github.com/laurentgrangeau))
* **Arthur Mauvezin** — DevOps Engineer @ Ouidou Consulting ([@arthurmauvezin](https://twitter.com/arthurmauvezin) | [github.com/arthurmauvezin](https://github.com/arthurmauvezin))

---

## Course Curriculum & Slide Flow

The presentation is organized into 10 modular Markdown decks under [`slides/`](slides/), structured from foundational concepts and service models to enterprise cloud strategy, architecture, and governance:

1. **Title & Speakers** ([`slides/title.md`](slides/title.md))
   * Course cover & speaker introductions
2. **Introduction & Navigation** ([`slides/introduction.md`](slides/introduction.md))
   * Audience icebreaker & Reveal.js 2D navigation guide
3. **What is the Cloud?** ([`slides/cloud.md`](slides/cloud.md))
   * Computing history: Mainframes (1950s–1970s) → Physical x86 Servers → Hypervisors & Virtual Machines → Cloud Computing
   * Essential Cloud Characteristics (`NIST`) & Economic shift (`CapEx` vs. `OpEx`)
   * The Shared Responsibility Model across On-Premises, `IaaS`, `PaaS`, `FaaS / Serverless`, and `SaaS`
4. **SaaS — Software-as-a-Service** ([`slides/saas.md`](slides/saas.md))
   * Turnkey cloud software consumption & popular enterprise/consumer SaaS ecosystems
5. **IaaS — Infrastructure-as-a-Service** ([`slides/iaas.md`](slides/iaas.md))
   * **Elasticity & Scale**: Vertical vs. Horizontal Scaling, Elasticity, Auto-Scaling, On-Demand Self-Service
   * **Global Infrastructure**: Cloud Regions, Hyperscaler Private Subsea Fiber Backbone & Edge CDN PoPs (Cold-Potato Routing), Availability Zones (`AZ`)
   * **Compute, Storage & Network Primitives**: Hardware-offloaded hypervisors (`AWS Nitro`, `Google Titanium`, `Azure Boost`), custom ARM silicon (`Graviton4`, `Axion`, `Cobalt 100`), GPU/TPU AI accelerators (`NVIDIA Blackwell B200` / `H200`, `TPU v6e`), Regional/Zonal SKU availability, Cloud Storage Taxonomy (`Block`, `File`, `Object` & Lifecycle Tiers), and Software-Defined Networking (`VPC` / `VNet`, `NSG`, `WAF`)
   * **Cloud-Native Operations & Delivery**: Pets vs. Cattle, Mutable vs. Immutable Infrastructure (`Packer`, `Docker`), Infrastructure as Code (`Terraform` / `OpenTofu`), Zero-Downtime Rolling Updates, Blue/Green, Canary Releases, and A/B Testing
   * **Reliability & Resilience Engineering**: SLA & "The Table of Nines", Composite SLA Math (Serial vs. Parallel Multi-AZ Redundancy), Backups, Disaster Recovery Plans (`DRP`), `RTO` & `RPO` Timelines, Chaos Engineering & the Netflix Simian Army + Modern Chaos Tooling (`AWS FIS`, `Azure Chaos Studio`, `Gremlin`, `Chaos Mesh`, `LitmusChaos`), and Multi-AZ IaaS Reference Architecture
6. **PaaS — Platform-as-a-Service** ([`slides/paas.md`](slides/paas.md))
   * Evolution from First-Gen PaaS (`Heroku`, `App Engine`, `Cloud Foundry`) to Modern Managed Cloud PaaS (`Cloud Run`, `Azure App Service` / `Container Apps`, `AWS App Runner`)
   * Managed Services, Turnkey Multi-Region Geo-Replication (`AlloyDB`, `Cloud Spanner`, `Cosmos DB`, `Aurora`), Automated PITR Backups & DR, API-Driven Design, Private & Hybrid PaaS (`OpenShift`, `Azure Arc`, `Google Distributed Cloud`), and Lakehouse/GenAI PaaS Reference Architecture (`BigQuery`, `Microsoft Fabric`, `Vertex AI`, `AWS Bedrock`)
7. **Serverless (`FaaS` & `BaaS`)** ([`slides/serverless.md`](slides/serverless.md))
   * Core Serverless characteristics, Architectural Trade-offs, Traditional 3-Tier vs. Serverless Architecture
   * Function-as-a-Service (`AWS Lambda`, `Google Cloud Run Functions`, `Azure Functions`) & Backend-as-a-Service (`Auth0`, `Firebase`, `Supabase`, `DynamoDB`, `Firestore`)
   * Event-Driven Auto-Scaling, Scale to Zero, Operational Challenges (Cold Starts, Distributed Tracing), and Serverless Reference Architecture
8. **Cloud Migration (`The "R"s`)** ([`slides/advanced.md`](slides/advanced.md))
   * Cloud Migration Decision Tree & Pathways: **Retain**, **Retire**, **Relocate**, **Rehost** (Lift & Shift), **Replatform** (Lift & Reshape), **Repurchase** (Move to SaaS), and **Refactor** (Re-architect to Cloud-Native)
9. **Enterprise Cloud Architectures & Governance** ([`slides/architecture.md`](slides/architecture.md))
   * **Hybrid & Multi-VPC Networking**: Point-to-Site VPN, Site-to-Site IPsec VPN, Dedicated Private Interconnect (`ExpressRoute` / `Direct Connect` / `Cloud Interconnect`), `VPC` / `VNet` Peering, and Hub & Spoke Topology
   * **Governance, Identity & Compliance**: Multi-Account Cloud Landing Zones, Cloud IAM & Zero-Trust Security (`RBAC`, `ABAC`, Workload Identity Federation / `OIDC`), Data Sovereignty, Customer-Managed Encryption (`KMS` / `HSM`), and Regulatory Compliance (`GDPR`, `DORA`, `NIS2`, `HIPAA`, `ISO 27001`, `SOC 2`, `SecNumCloud`, `EU AI Act`)
   * **Cloud Services Landscape**: 360° taxonomy across Compute, Storage, Managed Databases (`Aurora`, `AlloyDB`, `Valkey`), Networking, Data/AI (`BigQuery`, `Fabric`, `Vertex AI`, `Bedrock`), Security (`CNAPP` / `CSPM`), and DevOps/FinOps/GreenOps (`OpenTelemetry`, `Terraform` / `OpenTofu`)
10. **Conclusion & Synthesis** ([`slides/conclusion.md`](slides/conclusion.md))
    * The **6 Pillars of the Cloud Well-Architected Framework** (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization / FinOps, Sustainability / GreenOps) & Further Reading

---

## Repository Structure

```text
.
├── index.html          # Reveal.js 6.0.2 entrypoint and deck configuration
├── css/
│   └── custom.css      # Custom light theme, typography, tables, and responsive layout
├── img/                # 38 custom vector SVG diagrams and speaker avatars
└── slides/             # Modular Markdown slide decks (10 chapters)
```

---

## Keyboard Shortcuts

| Key | Action |
| --- | --- |
| `Space` | Next slide (follows the full vertical & horizontal teaching flow) |
| `←` `→` `↑` `↓` | Navigate horizontally between chapters or vertically within a topic |
| `Esc` / `O` | Toggle 2D slide overview map |
| `S` | Open Speaker Notes view (includes timer, upcoming slide, and speaker notes) |
| `F` | Toggle fullscreen mode |

---

## Run Locally

Because the presentation loads external Markdown files (`slides/*.md`), serve the repository through a local HTTP server:

```bash
python3 -m http.server 8000
```

Then open **http://localhost:8000** in your browser.

---

## Export to PDF (Chrome / Chromium)

1. Open [https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false](https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false) (or `http://localhost:8000/?print-pdf&pdfSeparateFragments=false` locally)
2. Press `Cmd+P` (macOS) or `Ctrl+P` (Windows/Linux)
3. Use the following print settings:

| Setting | Value |
| --- | --- |
| Destination | Save as PDF |
| Pages | All |
| Pages per sheet | 1 |
| Margins | Default |
| Options | Background graphics |

---

## Contributing

Feel free to submit pull requests or open issues!
