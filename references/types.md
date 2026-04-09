# Platform Types

The Platform Notation uses specific functional types to describe resources, boundaries, and authorization concepts without getting bogged down in cloud-specific terminology.

When using functional notation (e.g., `CloudPrimitive(Sector, Tier)`), always use positional inference for parameters (see `notation.md` for formatting rules).

## 1. Authorization Types

These types are used to define identity and access management.

*   **`Role(Name)`**: Defines a specific set of capabilities.
    *   `Role("operator")`: Non-human CI/CD and automation.
    *   `Role("admin")`: Human break-glass/emergency access.
    *   `Role("contributor")`: Human active development/troubleshooting access.
    *   `Role("reader")`: Human default read-only access.
*   **`Group(Tenant, Tier, Role)`**: The container that assigns members to a role in a specific context.
    *   Example: `Group("payments", "live", "contributor")`

## 2. Abstract Types

Generic infrastructure boundaries that could be implemented on any cloud. Use these to describe architectures before committing to a specific vendor.

*   **`Space(Sector, Tier, Region, Tenant)`**: The fully resolved execution environment for a tenant.
*   **`CloudPrimitive(Sector, Tier)`**: The hardest administrative boundary (e.g., a cloud account).
*   **`Network(Sector, Tier, Region)`**: The network boundary (e.g., a VPC).
*   **`Spoke(Sector, Tier, Region)`**: An isolated network segment connected to a central Hub.
*   **`Database(Sector, Tier, Region, Tenant)`**: A database resource.
*   **`VirtualMachine(Sector, Tier, Region, Tenant)`**: A virtual machine compute resource.

## 3. Specific Types

Concrete cloud provider resources that implement the abstract types.

**Amazon Web Services (AWS)**
*   `AWSOrganizationalUnit(Sector)`
*   `AWSAccount(Sector, Tier, Tenant)` or `AWSAccount(Sector, Tier)`
*   `AWSVPC(Sector, Tier, Region, Tenant)` or `AWSVPC(Sector, Tier, Region)`
*   `AWSTransitGateway(Region)`

**Microsoft Azure**
*   `AzureManagementGroup(Sector)`
*   `AzureSubscription(Sector, Tier)`
*   `AzureResourceGroup(Sector, Tier, Region, Tenant)`
*   `AzureVNet(Sector, Tier, Region)`

**Google Cloud Platform (GCP)**
*   `GCPFolder(Sector)`
*   `GCPProject(Sector, Tier, Tenant)`
*   `GCPVPC(Sector, Tier, Region)`

**Kubernetes**
*   `Cluster(Sector, Tier, Region)`
*   `Namespace(Sector, Tier, Region, Tenant)`
