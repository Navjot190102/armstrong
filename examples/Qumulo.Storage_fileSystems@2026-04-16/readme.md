# Qumulo.Storage/fileSystems@2026-04-16 — Armstrong test artifacts

Terraform configuration and Armstrong reports for the **`Qumulo.Storage/fileSystems@2026-04-16`**
ARM API (new stable version).

- **Swagger source:** [Azure/azure-rest-api-specs#43746](https://github.com/Azure/azure-rest-api-specs/pull/43746)
  (`specification/liftrqumulo/resource-manager/Qumulo.Storage/stable/2026-04-16/Qumulo.Storage.json`)
- **Armstrong:** built from source, v0.16.1

## What's new in 2026-04-16 (vs 2024-06-19)

Additional `properties` on the file system resource:

| Property | Notes |
|----------|-------|
| `performanceTier` | new, optional |
| `clusterLoginUrl` | new, optional |
| `privateIPs` | new, optional (array) |
| `marketplaceDetails.termUnit` | new, optional |
| `marketplaceDetails.marketplaceSubscriptionStatus` | new, read-only |

Required create properties (unchanged): `marketplaceDetails` (`planId`, `offerId`),
`storageSku`, `userDetails`, `delegatedSubnetId`, `adminPassword`.

## Contents

| File | Description |
|------|-------------|
| `main.tf` | azapi config: resource group, vnet, delegated subnet, and the `Qumulo.Storage/fileSystems@2026-04-16` testing resource. |
| `Swagger_Create_Example.json` | The `FileSystems_CreateOrUpdate_MaximumSet_Gen` example from the 2026-04-16 spec. |
| `reports/Onboard Terraform - partial_passed_report.md` | `armstrong test` result. |
| `reports/Error - Qumulo.Storage_fileSystems@2026-04-16_qumuloFileSystem.md` | API error report (with HTTP traces). |
| `reports/Onboard Terraform - cleanup_all_passed_report.md` | `armstrong cleanup` result. |

## Steps performed

1. **Install Armstrong** — built from source, v0.16.1.
2. **Generate** — `armstrong generate -path <2026-04-16 FileSystems_CreateOrUpdate example>`.
   The auto-generated `testing.tf` was not directly usable because the `MaximumSet_Gen`
   example carries placeholder values (fake resource `id`), so the resource type / parent
   could not be resolved. `main.tf` was authored from the known-good dependency graph
   (resource group + vnet + delegated subnet) with the resource type bumped to
   `@2026-04-16`.
3. **Validate** — `armstrong validate` → `Plan: 4 to add, 0 to change, 0 to destroy`.
4. **Test** — `armstrong test` (live). Result: **3 resources passed** (resource group, vnet,
   subnet), **1 error** on the Qumulo file system.
5. **Cleanup** — `armstrong cleanup` → all 3 live resources destroyed (all-passed cleanup report).

## Test result / findings

The dependency chain provisioned successfully and ARM **accepted** the 2026-04-16 request
(marketplace validation ran), confirming the new API version and request body shape are valid.

The Qumulo file system create returned:

```
RESPONSE 400: ResourceCreationValidateFailed
MarketplaceValidation ... SaaS Purchase Payment Check Failed
{"isEligible":false,"errorMessage":"This subscription is internal or sandbox.
 Only $0.00 products or test products can be purchased. Please select a different
 subscription to purchase paid, non-test offers"}
```

This is an **environment/marketplace limitation**, not an API or swagger defect — the
internal/sandbox test subscription (`a8b81ef0-…`) cannot purchase the paid Qumulo
marketplace offer. To obtain an `all_passed` test report, re-run `armstrong test` on a
purchase-enabled subscription (or with a `$0.00` test marketplace plan).
