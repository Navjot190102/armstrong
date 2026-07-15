## Qumulo.Storage/fileSystems@2026-04-16 - Error

### Description

I found an error when creating this resource:

```bash


  with azapi_resource.qumuloFileSystem,
  on main.tf line 85, in resource "azapi_resource" "qumuloFileSystem":
  85: resource "azapi_resource" "qumuloFileSystem" {

creating/updating Resource: (ResourceId
"/subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourceGroups/acctest0001/providers/Qumulo.Storage/fileSystems/acctest0001"
/ Api Version "2026-04-16"): PUT
https://management.azure.com/subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourceGroups/acctest0001/providers/Qumulo.Storage/fileSystems/acctest0001
--------------------------------------------------------------------------------
RESPONSE 400: 400 Bad Request
ERROR CODE: ResourceCreationValidateFailed
--------------------------------------------------------------------------------
{
  "error": {
    "code": "ResourceCreationValidateFailed",
    "message": "MarketplaceValidation, MarketplaceValidation, SaaS Purchase Payment Check Failed as validationResponse was {\"isEligible\":false,\"errorMessage\":\"This subscription is internal or sandbox. Only $0.00 products or test products can be purchased. Please select a different subscription to purchase paid, non-test offers\"}, failed for resoruce id /subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourcegroups/acctest0001/providers/Qumulo.Storage/fileSystems/acctest0001, resource name acctest0001 "
  }
}
--------------------------------------------------------------------------
```

### Details

1. ARM Fully-Qualified Resource Type
```
Qumulo.Storage/fileSystems
```

2. API Version
```
2026-04-16
```

3. Swagger issue type
```
Other
```

4. OperationId
```
TODO
```

5. Swagger GitHub permalink
```
TODO, 
e.g., https://github.com/Azure/azure-rest-api-specs/blob/60723d13309c8f8060d020a7f3dd9d6e380f0bbd
/specification/compute/resource-manager/Microsoft.Compute/stable/2020-06-01/compute.json#L9065-L9101
```

6. Error code
```
TODO
```

7. Request traces
```
GET /subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourceGroups/acctest0001/providers/Qumulo.Storage/fileSystems/acctest0001?api-version=2026-04-16
Status Code: 404
------------ Request ------------
User-Agent: HashiCorp Terraform/1.15.8 (+https://www.terraform.io) terraform-provider-azapi/v2.10.0 pid-222c6c49-1b0a-5959-a213-6608f9eb8820
X-Ms-Correlation-Request-Id: c01b9114-dca7-2f45-ebfa-5fc467506193
Accept: application/json
Authorization: REDACTED

---


------------ Response ------------
X-Ms-Routing-Request-Id: WESTEUROPE:20260715T161434Z:6f84cd2e-b781-4737-8f75-e94696e01ee0
X-Cache: CONFIG_NOCACHE
X-Content-Type-Options: nosniff
X-Ms-Failure-Cause: gateway
X-Ms-Request-Id: 6f84cd2e-b781-4737-8f75-e94696e01ee0
X-Msedge-Ref: Ref A: F45D3FD1A5C042659D5D9F564015FC9B Ref B: PNQ241100406036 Ref C: 2026-07-15T16:14:34Z
Content-Type: application/json; charset=utf-8
Date: Wed, 15 Jul 2026 16:14:33 GMT
X-Ms-Correlation-Request-Id: c01b9114-dca7-2f45-ebfa-5fc467506193
Cache-Control: no-cache
Content-Length: 221
Strict-Transport-Security: max-age=31536000; includeSubDomains
Expires: -1
Pragma: no-cache
------
{
  "error": {
    "code": "ResourceNotFound",
    "message": "The Resource 'Qumulo.Storage/fileSystems/acctest0001' under resource group 'acctest0001' was not found. For more details please go to https://aka.ms/ARMResourceNotFoundFix"
  }
}




PUT /subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourceGroups/acctest0001/providers/Qumulo.Storage/fileSystems/acctest0001?api-version=2026-04-16
Status Code: 400
------------ Request ------------
Content-Type: application/json
User-Agent: HashiCorp Terraform/1.15.8 (+https://www.terraform.io) terraform-provider-azapi/v2.10.0 pid-222c6c49-1b0a-5959-a213-6608f9eb8820
X-Ms-Correlation-Request-Id: c01b9114-dca7-2f45-ebfa-5fc467506193
Accept: application/json
Authorization: REDACTED
Content-Length: 527

---
{
  "location": "westeurope",
  "properties": {
    "adminPassword": ")^X#ZX#JRyIY}t9",
    "availabilityZone": "1",
    "delegatedSubnetId": "/subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourceGroups/acctest0001/providers/Microsoft.Network/virtualNetworks/acctest0001/subnets/acctest0001",
    "marketplaceDetails": {
      "offerId": "qumulo-saas-mpp",
      "planId": "azure-native-qumulo-v3",
      "publisherId": "qumulo1584033880660"
    },
    "storageSku": "Cold_LRS",
    "userDetails": {
      "email": "test@test.com"
    }
  },
  "tags": {
    "environment": "terraform-acctests",
    "some_key": "some-value"
  }
}

------------ Response ------------
Expires: -1
X-Cache: CONFIG_NOCACHE
X-Ms-Request-Id: d6dd7021-6669-4eea-8248-9fa49f9fc208
X-Msedge-Ref: Ref A: 56FC6B18C6B9480AB646BB3F497042A0 Ref B: PNQ241100406036 Ref C: 2026-07-15T16:14:20Z
Content-Length: 564
Pragma: no-cache
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Ms-Correlation-Request-Id: c01b9114-dca7-2f45-ebfa-5fc467506193
X-Ms-Failure-Cause: gateway
X-Ms-Operation-Identifier: tenantId=bb6a35d6-b9d5-4b6b-b760-976103233061,objectId=ef936602-3e0b-4758-b10e-026ec6a686bb/westeurope/dfb4d539-7674-484b-be51-767b6221f214
X-Ms-Providerhub-Traffic: True
Cache-Control: no-cache
Content-Type: application/json
Mise-Correlation-Id: 29f38b32-af25-4afe-bf5a-d7d9a217549c
X-Envoy-Upstream-Service-Time: 11455
X-Ms-Ratelimit-Remaining-Subscription-Global-Writes: 2999
X-Ms-Ratelimit-Remaining-Subscription-Writes: 199
Date: Wed, 15 Jul 2026 16:14:33 GMT
X-Content-Type-Options: nosniff
X-Ms-Routing-Request-Id: WESTEUROPE:20260715T161434Z:0d275d8f-68f9-4645-bf59-a8153d447a47
------
{
  "error": {
    "code": "ResourceCreationValidateFailed",
    "message": "MarketplaceValidation, MarketplaceValidation, SaaS Purchase Payment Check Failed as validationResponse was {\"isEligible\":false,\"errorMessage\":\"This subscription is internal or sandbox. Only $0.00 products or test products can be purchased. Please select a different subscription to purchase paid, non-test offers\"}, failed for resoruce id /subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourcegroups/acctest0001/providers/Qumulo.Storage/fileSystems/acctest0001, resource name acctest0001 "
  }
}




GET /subscriptions/a8b81ef0-9c6a-4ff2-b675-081212bab47b/resourceGroups/acctest0001/providers/Qumulo.Storage/fileSystems/acctest0001?api-version=2026-04-16
Status Code: 404
------------ Request ------------
User-Agent: HashiCorp Terraform/1.15.8 (+https://www.terraform.io) terraform-provider-azapi/v2.10.0 pid-222c6c49-1b0a-5959-a213-6608f9eb8820
X-Ms-Correlation-Request-Id: c01b9114-dca7-2f45-ebfa-5fc467506193
Accept: application/json
Authorization: REDACTED

---


------------ Response ------------
Date: Wed, 15 Jul 2026 16:14:20 GMT
Expires: -1
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Ms-Correlation-Request-Id: c01b9114-dca7-2f45-ebfa-5fc467506193
X-Ms-Request-Id: 95f27265-9888-4a59-83c1-0d4c0af007f9
Content-Length: 221
Pragma: no-cache
X-Cache: CONFIG_NOCACHE
X-Content-Type-Options: nosniff
X-Ms-Failure-Cause: gateway
X-Ms-Routing-Request-Id: WESTEUROPE:20260715T161420Z:95f27265-9888-4a59-83c1-0d4c0af007f9
Content-Type: application/json; charset=utf-8
X-Msedge-Ref: Ref A: B200FB321BAD4451AFF637737E8AE64B Ref B: PNQ241100406036 Ref C: 2026-07-15T16:14:20Z
Cache-Control: no-cache
------
{
  "error": {
    "code": "ResourceNotFound",
    "message": "The Resource 'Qumulo.Storage/fileSystems/acctest0001' under resource group 'acctest0001' was not found. For more details please go to https://aka.ms/ARMResourceNotFoundFix"
  }
}





```

### Links
1. [Semantic and Model Violations Reference](https://github.com/Azure/azure-rest-api-specs/blob/main/documentation/Semantic-and-Model-Violations-Reference.md)
2. [S360 action item generator for Swagger issues](https://aka.ms/swaggers360)