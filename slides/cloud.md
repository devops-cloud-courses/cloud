## What is the Cloud?

Note:
Ask the audience for everyday examples of Cloud services they use (e.g., SaaS apps like Gmail, Google Drive, Netflix, Spotify).

----

### A quick look back in time

----

### The Mainframe Era

<img src="img/history-mainframe.svg" alt="Mainframe Architecture with Dumb Terminals" />

----

### Rise of Physical Servers

<img src="img/history-physical.svg" alt="Physical Servers Architecture and Limitations" />

----

### Birth of Virtual Machines

<img src="img/history-vms.svg" alt="Physical Servers vs Virtual Machines with a Hypervisor" />

----

### The Cloud

<img src="img/cloud-overview.svg" alt="Cloud Computing Overview" />

----

### Essential Cloud Characteristics

> Defined by NIST — the 5 core properties of Cloud Computing

* **Pay-as-you-go**: Metered billing based on actual consumption (OpEx vs CapEx)
* **Rapid Elasticity**: Scale resources out and back in dynamically as demand changes
* **Broad Network Access**: Open and accessible from anywhere via standard protocols and APIs
* **Resource Pooling**: Multi-tenant hardware shared securely across customers
* **On-Demand Self-Service**: Provision resources instantaneously without human intervention

Note:
* Elasticity: Think of it like a rubber band — when traffic spikes, you stretch it out; when you let go, it shrinks back automatically so you only pay for what you need.

----

### Cloud Service Models

<img src="img/shared-responsibility.svg" alt="Shared Responsibility Model across On-Premises, IaaS, PaaS, FaaS, and SaaS" />

Note:
* Shared Responsibility Model (SRM): Everything in blue is managed by the CSP (Cloud Service Provider); everything in dark slate is the customer's responsibility.
* Two flavors of PaaS:
  * Application PaaS (Heroku / Cloud Run / App Engine style)
  * Managed infrastructure/data PaaS (Managed Databases, Queues, etc.)
* In PaaS, you don't manage VMs — you consume capability and SLA levels.
