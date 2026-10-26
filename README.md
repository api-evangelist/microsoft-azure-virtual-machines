# Azure Virtual Machines (microsoft-azure-virtual-machines)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Azure Virtual Machines (VMs) is one of several types of on-demand, scalable computing resources that Azure offers. VMs give you the flexibility of virtualization without having to buy and maintain physical hardware.

**APIs.json:** [https://azure.microsoft.com/en-us/services/virtual-machines/](https://azure.microsoft.com/en-us/services/virtual-machines/)

## Tags

- Cloud Computing
- Compute
- IaaS
- Infrastructure
- Virtual Machines

## Timestamps

- **Created:** 2024-01-20
- **Modified:** 2026-05-19

## APIs

### Azure Virtual Machines REST API

REST API for creating and managing Azure Virtual Machines. Provides operations for provisioning, starting, stopping, deallocating, restarting, reimaging, capturing, and deleting virtual machines, as well as managing data disks, extensions, patching, and run commands.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/](https://learn.microsoft.com/en-us/azure/virtual-machines/)
- **Base URL:** `https://management.azure.com`

#### Tags

- Compute
- REST API
- Virtual Machines

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machines)
- [OpenAPI](https://raw.githubusercontent.com/Azure/azure-rest-api-specs/main/specification/compute/resource-manager/Microsoft.Compute/ComputeRP/stable/2023-09-01/virtualMachines.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Swagger](https://raw.githubusercontent.com/Azure/azure-rest-api-specs/main/specification/compute/resource-manager/Microsoft.Compute/ComputeRP/stable/2023-09-01/virtualMachines.json)
- [Pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/)
- [S L A](https://azure.microsoft.com/en-us/support/legal/sla/virtual-machines/)
- [Getting Started](https://learn.microsoft.com/en-us/azure/virtual-machines/overview)
- [Tutorials](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-manage-vm)
- [S D Ks](https://azure.microsoft.com/en-us/downloads/)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machines?view=rest-compute-2025-04-01)
- [Authentication](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-managed-identities-work-vm)
- [Quickstart](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-cli)
- [Rate Limits](https://learn.microsoft.com/en-us/azure/virtual-machines/quotas)
- [S D K -  Python](https://learn.microsoft.com/en-us/python/api/overview/azure/compute)
- [S D K - . N E T](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute)
- [S D K -  Java Script](https://www.npmjs.com/package/@azure/arm-compute)
- [S D K -  Go](https://pkg.go.dev/github.com/Azure/azure-sdk-for-go/arm/compute)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Virtual Machine Scale Sets REST API

REST API for creating and managing Azure Virtual Machine Scale Sets (VMSS). Enables deployment and management of groups of identical, load-balanced VMs that can automatically scale in response to demand or a defined schedule.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/)
- **Base URL:** `https://management.azure.com`

#### Tags

- Autoscaling
- Load Balancing
- Virtual Machine Scale Sets

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-scale-sets)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-scale-sets?view=rest-compute-2025-04-01)
- [Getting Started](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-portal)
- [Pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machine-scale-sets/)
- [F A Q](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-faq)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Virtual Machine Extensions REST API

REST API for managing Virtual Machine Extensions, which provide post-deployment configuration and automation tasks on Azure VMs. Extensions can install software, run scripts, configure diagnostics, and integrate with monitoring and security tools.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/overview](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/overview)
- **Base URL:** `https://management.azure.com`

#### Tags

- Automation
- Configuration
- Extensions

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-extensions)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-extensions?view=rest-compute-2025-04-01)
- [Getting Started](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/overview)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Virtual Machine Images REST API

REST API for listing and querying available virtual machine images in Azure, including platform images, marketplace images, and custom images. Provides operations for listing publishers, offers, SKUs, and image versions by region.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/linux/cli-ps-findimage](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/cli-ps-findimage)
- **Base URL:** `https://management.azure.com`

#### Tags

- Images
- Marketplace
- VM Images

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-images)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-images?view=rest-compute-2025-04-01)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Virtual Machine Sizes REST API

REST API for listing available virtual machine sizes in a given Azure region. Returns the complete catalog of VM sizes with their resource specifications including number of vCPUs, memory, and disk capacity.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/overview](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/overview)
- **Base URL:** `https://management.azure.com`

#### Tags

- Capacity
- SKUs
- VM Sizes

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-sizes)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-sizes/list?view=rest-compute-2025-04-01)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Virtual Machine Run Commands REST API

REST API for executing scripts and commands on Azure Virtual Machines without requiring direct network connectivity. Useful for troubleshooting, running diagnostics, and performing administrative tasks remotely via the Azure management plane.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/run-command-overview](https://learn.microsoft.com/en-us/azure/virtual-machines/run-command-overview)
- **Base URL:** `https://management.azure.com`

#### Tags

- Diagnostics
- Run Commands
- Scripting

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-run-commands)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/virtual-machine-run-commands/list-by-virtual-machine?view=rest-compute-2025-04-01)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Availability Sets REST API

REST API for creating and managing Availability Sets, which are logical groupings of VMs that distribute them across fault domains and update domains to provide high availability and resilience during planned and unplanned maintenance events.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/availability-set-overview](https://learn.microsoft.com/en-us/azure/virtual-machines/availability-set-overview)
- **Base URL:** `https://management.azure.com`

#### Tags

- Availability Sets
- Fault Domains
- High Availability

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/availability-sets)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/availability-sets?view=rest-compute-2024-07-01)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Proximity Placement Groups REST API

REST API for creating and managing Proximity Placement Groups, which co-locate Azure resources within the same datacenter to achieve low network latency between virtual machines, scale sets, and other compute resources.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/co-location](https://learn.microsoft.com/en-us/azure/virtual-machines/co-location)
- **Base URL:** `https://management.azure.com`

#### Tags

- Co-Location
- Low Latency
- Proximity Placement Groups

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/proximity-placement-groups)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/proximity-placement-groups/list-by-subscription?view=rest-compute-2025-02-01)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Dedicated Hosts REST API

REST API for creating and managing Azure Dedicated Hosts, which provide physical servers dedicated to a single Azure subscription. Dedicated hosts give visibility and control over server-level infrastructure to help address compliance and regulatory requirements.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/dedicated-hosts](https://learn.microsoft.com/en-us/azure/virtual-machines/dedicated-hosts)
- **Base URL:** `https://management.azure.com`

#### Tags

- Compliance
- Dedicated Hosts
- Isolation

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/rest/api/compute/dedicated-host-groups)
- [Reference](https://learn.microsoft.com/en-us/rest/api/compute/dedicated-host-groups/list-by-resource-group?view=rest-compute-2024-11-04)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Azure Capacity Reservations REST API

REST API for creating and managing Capacity Reservations, which allow you to reserve compute capacity in an Azure region or availability zone. Ensures that allocated capacity is available when you need to deploy virtual machines without relying on spot or on-demand availability.

- **Human URL:** [https://learn.microsoft.com/en-us/azure/virtual-machines/capacity-reservation-overview](https://learn.microsoft.com/en-us/azure/virtual-machines/capacity-reservation-overview)
- **Base URL:** `https://management.azure.com`

#### Tags

- Capacity Reservations
- Planning
- Reserved Capacity

#### Properties

- [Documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/capacity-reservation-overview)
- [Reference](https://learn.microsoft.com/en-us/azure/virtual-machines/capacity-reservation-group-share)
- [Postman Collection](collections/azure-virtual-machines.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/azure-virtual-machines.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://portal.azure.com)
- [Authentication](https://learn.microsoft.com/en-us/azure/active-directory/develop/authentication-scenarios)
- [Status Page](https://status.azure.com/)
- [Blog](https://azure.microsoft.com/en-us/blog/)
- [Support](https://azure.microsoft.com/en-us/support/options/)
- [Terms of Service](https://azure.microsoft.com/en-us/support/legal/)
- [Privacy Policy](https://privacy.microsoft.com/en-us/privacystatement)
- [Contact](https://azure.microsoft.com/en-us/contact/)
- [Documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/)
- [Getting Started](https://learn.microsoft.com/en-us/azure/virtual-machines/overview)
- [Pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/)
- [Website](https://azure.microsoft.com/en-us/products/virtual-machines)
- [Sign Up](https://azure.microsoft.com/en-us/free)
- [Login](https://portal.azure.com)
- [S D Ks](https://azure.microsoft.com/en-us/downloads/)
- [C L I  Tools](https://learn.microsoft.com/en-us/cli/azure/vm)
- [Rate Limits](https://learn.microsoft.com/en-us/azure/virtual-machines/quotas)
- [Changelog](https://azure.microsoft.com/en-us/updates/?product=virtual-machines)
- [Community](https://learn.microsoft.com/en-us/answers/tags/94/azure-virtual-machines)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/azure-virtual-machines)
- [GitHub Organization](https://github.com/Azure)
- [Git Hub  R E S T  A P I  Specs](https://github.com/Azure/azure-rest-api-specs/tree/main/specification/compute/resource-manager)
- [Training](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-virtual-machines/)
- [F A Q](https://learn.microsoft.com/en-us/azure/virtual-machines/faq-for-disks)
- [YouTube](https://www.youtube.com/c/MicrosoftAzure)
- [S L A](https://azure.microsoft.com/en-us/support/legal/sla/virtual-machines/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
