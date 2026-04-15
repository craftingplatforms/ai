# Platform Notation

When generating configurations, architectures, or communicating about the internal developer platform, you MUST strictly adhere to the following structural notation and naming conventions. This ensures consistency across all AI skills, platform components, and documentation.

## The Coordinate System

Every resource in the platform is assigned a specific tuple called its **coordinate**, consisting of four dimensions: `(Sector, Tier, Region, Tenant)`.

1.  **Sector**: The highest-level boundary separating internal management from business logic.
    *   Examples: `"platform"`, `"ecommerce"`, `"finance"`.
2.  **Tier**: The criticality and data classification boundary.
    *   Examples: `"sandbox"`, `"live"`.
3.  **Region**: The physical location of the workloads.
    *   Examples: `"eu01"`, `"us01"`.
4.  **Tenant**: The specific team or product owning the workload.
    *   Examples: `"payments"`, `"recommendations"`.

**Coordinate Rules:**
*   **Lowercase Values**: All dimension values MUST be lowercase strings (e.g., `"ecommerce"`, NOT `"ECommerce"` or `"Ecommerce"`).
*   **Positional Tuples**: Use clean coordinates like `("ecommerce", "live", "eu01", "payments")` for fully resolved paths. Use an underscore `_` for ignored dimensions, e.g., `("platform", "live", _, _)`.

## Associations

To express relationships between resources, use the following simple operators:

1.  **Hierarchy (`in`)**: Membership or containment.
    *   Example: `Identity in Group("payments", "live", "reader")`
2.  **Structural Mapping (`=>`)**: Implementation or realization (abstract to concrete).
    *   Example: `Space("payments", "live", ...) => AzureResourceGroup(...)`
3.  **Logical Connectivity (`<->`)**: Bidirectional link or communication path.
    *   Example: `Spoke("ecommerce", "live", "eu01") <-> Hub("platform", "live", "eu01")`

## Formatting and Textual Usage

When referencing these concepts in text or markdown, you must follow these strict formatting rules:

1.  **Positional Inference**: In functional notation, use clean strings for parameters. **Do not nest type wrappers**.
    *   ✅ **DO**: `Group("payments", "live", "operator")`
    *   ❌ **DON'T**: `Group(Tenant("payments"), Tier("live"), Role("operator"))`
2.  **Standalone Dimension Wrapping**: Wrap dimension values in their type ONLY when they appear alone in the text to provide architectural context.
    *   ✅ **DO**: "Deploying to `Tier("live")` requires approval."
    *   ❌ **DON'T**: "Deploying to live requires approval."
3.  **No Redundant Descriptive Words**: The type annotation replaces the need for the descriptive noun.
    *   ✅ **DO**: "Inside `Tier("sandbox")`..."
    *   ❌ **DON'T**: "Inside the `Tier("sandbox")` tier..."
    *   ✅ **DO**: "If `Tenant("payments")` requests..."
    *   ❌ **DON'T**: "If the `Tenant("payments")` team requests..."
4.  **No Bold for Inline Code**: **NEVER** use bold formatting for inline code.
    *   ✅ **DO**: `` `Role("operator")` ``
    *   ❌ **DON'T**: `` **`Role("operator")`** ``
