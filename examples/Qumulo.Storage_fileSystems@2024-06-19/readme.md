# Qumulo.Storage/fileSystems@2024-06-19 — Armstrong test artifacts

This directory contains the Terraform configuration and Armstrong reports produced
while testing the `Qumulo.Storage/fileSystems@2024-06-19` ARM API with
[Armstrong](https://github.com/Azure/armstrong).

## Contents

| File | Description |
|------|-------------|
| `main.tf` | azapi Terraform configuration: resource group, virtual network, delegated subnet, and the `Qumulo.Storage/fileSystems@2024-06-19` testing resource. |
| `reports/validate_plan.txt` | Output of `armstrong validate` (`terraform init` + `plan`). |
| `reports/cleanup_report.txt` | Output of `armstrong cleanup` (`terraform destroy`). |

## Steps performed

1. **Install Armstrong** — built from source (`go build -o armstrong.exe .`), version `0.16.1`.
2. **Generate / prepare** the Terraform file for the resource under test (`main.tf`).
3. **Validate** — `armstrong validate -working-dir .`
   Result: `Plan: 4 to add, 0 to change, 0 to destroy` (resource group, vnet, subnet, Qumulo file system).
4. **Cleanup** — `armstrong cleanup -working-dir .` (produces the cleanup report).

> Note: `armstrong test` (which provisions live Azure resources) was not run here; the
> paid Qumulo marketplace offer is not purchasable on the internal test subscription.
> Re-run `armstrong test` on a purchase-enabled subscription to generate the
> `all_passed`/`partial_passed` test reports.
