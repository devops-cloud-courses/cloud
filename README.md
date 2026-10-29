# Cloud in a Nutshell

This repository contains a **Reveal.js 6** presentation about Cloud Computing (`IaaS`, `PaaS`, `SaaS`, `Serverless`, and `Cloud Architectures`).

To view this presentation online, visit: **https://devops-cloud-courses.github.io/cloud**

You can also clone this repository and serve it locally using any static web server.

> This course is open source. Feel free to use and share it!

## Table of Contents

* **Introduction**
* **What is the Cloud?** (History from Mainframes to VMs & Cloud, NIST Characteristics, CapEx vs OpEx, Shared Responsibility Model)
* **SaaS** (Software-as-a-Service, Multi-Tenant Economics, Enterprise Integration & Security)
* **IaaS** (Scalability, Elasticity, Regions & AZs, Global Fiber Backbone, VMs, Block/File/Object Storage, Pets vs Cattle, Immutable Infra, IaC, Deployment Strategies, SLA & Composite SLA Math, DRP, RTO/RPO, Chaos Engineering)
* **PaaS** (Platform-as-a-Service, Managed Services, Geo-Replication, Private & Hybrid PaaS)
* **Serverless** (FaaS, BaaS, Event-Driven Triggers, Scale to Zero, Cold Starts & Trade-offs)
* **Cloud Migration & Strategy** (Cloud Adoption Drivers, The 8 Rs of Cloud Migration, Total Cost of Ownership)
* **Enterprise Cloud Architecture** (Cloud Services Landscape, Hybrid VPNs, Direct Connect/ExpressRoute, Landing Zones, Hub & Spoke, Cloud IAM & Zero-Trust, Data Sovereignty & Compliance, Well-Architected Framework)
* **Conclusion & Key Takeaways**

## Run Locally

Using Python's built-in HTTP server:

```bash
python3 -m http.server 8000
```

Then open **http://localhost:8000** in your browser.

## Export to PDF (Chrome / Chromium)

1. Open [https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false](https://devops-cloud-courses.github.io/cloud/?print-pdf&pdfSeparateFragments=false) (or `http://localhost:8000/?print-pdf&pdfSeparateFragments=false` locally)
2. Press `Cmd+P` / `Ctrl+P`
3. Use the following print settings:

| Setting | Value |
| --- | --- |
| Destination | Save as PDF |
| Pages | All |
| Pages per sheet | 1 |
| Margins | Default |
| Options | Background graphics |

## Contributing

Feel free to submit pull requests or open issues!
