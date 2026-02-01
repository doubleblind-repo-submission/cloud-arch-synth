# Cloud Service Equivalence Master Map (AWS ↔ Azure ↔ GCP ↔ OSS)

## Overview
This repository includes a curated **cross-cloud equivalence master map** that links AWS services to **alternatives** in:
- **Microsoft Azure**
- **Google Cloud (GCP)**
- **Open Source (OSS)**

The purpose of this map is to support **cross-cloud analysis**, **portability discussions**, and **architecture reasoning** (e.g., when comparing patterns across providers or explaining what “equivalent” could mean in practice).

✅ This map focuses on **practical alternatives**, not perfect clones.  
❌ It does **not** claim that every row has a strict 1:1 “twin” across clouds.

---

## File: `MasterMap_NOTES_ES_EN.csv`
**Rows:** 141 (excluding header)  
**Columns (7):**
1. `Servicio AWS` *(primary key / lookup key)*
2. `Azure`
3. `GCP`
4. `Open Source`
5. `Quality`
6. `Notes_ES`
7. `Notes_EN`

---

## What each row represents
Each row is a **mapping record** keyed by `Servicio AWS`.

### A) Cloud-service rows (most rows)
The AWS entry is a real cloud service (e.g., `S3`, `EKS`, `Lambda`).  
The row provides the closest alternatives in Azure/GCP/OSS, plus a `Quality` label and explanatory Notes.

### B) Special / non-cloud rows (some rows)
Some entries are **not cloud services**, but **actors/endpoints/placeholders** used in architecture descriptions.
For example: `UserCompany*` and `UserConsumer*`.

These represent **end-user roles or endpoints** (personas, devices, client apps, channels), so they should **not** be mapped to cloud services.
Such rows should typically be interpreted as:
- `Quality = NA`
- Mapping columns may be `-`
- Notes explain why mapping is not applicable

---

## How to read the mapping columns (`Azure`, `GCP`, `Open Source`)
Each of these columns contains the best alternative(s) known for the AWS key.

### Common conventions
- **Single value**
  - The most suitable alternative for the same role/pattern.
- **`A / B`**
  - Either option may satisfy the same role depending on the scenario.
  - Example: `RabbitMQ / ActiveMQ` means you may choose one depending on protocol/operations.
- **`A + B`**
  - A combination is typically required to approximate the AWS behavior/pattern.
  - Example: one service provides the API gateway, another provides auth, another provides eventing, etc.
- **`-`**
  - Intentionally not mapped / not applicable / no meaningful equivalent in that category.
  - Common for end-user actors (UserCompany/UserConsumer) or where OSS does not match the managed nature of the service.
- **Empty cell**
  - Mapping not provided (unknown/not defined). Treat as incomplete.

> Important: cloud providers differ in how they split products. A single AWS service can correspond to multiple services elsewhere, or vice versa.

---

## `Quality` column (EXACT / CLOSE / APPROX / NA)
`Quality` indicates how strong the equivalence is **from an architectural and operational standpoint**.

### EXACT
**Near 1:1 equivalence**
- Same category and pattern
- Comparable expectations
- Similar operational behavior

**Interpretation:** “I can replace this with minimal design changes.”

### CLOSE
**Same category/pattern, but meaningful differences exist**
- Differences in features, integration, semantics, or operational model
- Equivalent works, but you must account for important deltas

**Interpretation:** “Equivalent in practice, but not identical.”

### APPROX
**Equivalent by intent/function, but not a direct twin**
- Often requires combining services or changing the architecture pattern
- Tradeoffs are expected (features, semantics, ops, managed vs DIY)

**Interpretation:** “Works as an alternative, but requires redesign or composition.”

### NA (Not Applicable)
**Not meant to be mapped as a cloud service**
- End-user actors/endpoints (UserCompany/UserConsumer)
- Placeholders, or entries outside cloud-service scope
- Items where mapping is intentionally not meaningful

**Interpretation:** “Do not map this entry to Azure/GCP/OSS services.”

---

## `Notes_ES` and `Notes_EN` (what are Notes?)
The Notes are the **justification and context** behind the mapping. They explain:

- **Why** the alternative was selected (pattern/functionality)
- **Key differences** that prevent strict 1:1 mapping
- Whether equivalence depends on **design choices**
  - Managed vs self-hosted
  - IAM / policies model
  - Eventing semantics
  - Quotas, regions, HA patterns
  - Operational responsibility differences
- How to interpret OSS options
  - OSS sometimes provides only the core component; you may need extra tooling for production-grade parity.

`Notes_ES` and `Notes_EN` express the same idea in Spanish and English.

---

## Special Case: `UserCompany*` / `UserConsumer*`
Entries like:
- `UserCompanyDeveloper`
- `UserCompanyAPI`
- `UserConsumerMobile`
- `UserConsumerWeb`
- `UserConsumerAlexaGoogleHome`

are **not cloud services**.

They represent **end-user actors, roles, channels, or endpoints** (personas/devices/client apps).  
They should not be replaced by Azure/GCP/OSS services.

Recommended interpretation:
- `Quality = NA`
- Mapping fields (`Azure`, `GCP`, `Open Source`) set to `-`
- Notes explain that the entry is an actor/end-user element

---

## How to use the map
### 1) Manual lookup (CSV)
Search `Servicio AWS` and read across the row:
- Suggested alternatives in Azure/GCP/OSS
- `Quality` tells you how close the match is
- `Notes_EN` (or `Notes_ES`) tells you the *why* and the *tradeoffs*

### 2) Programmatic lookup (Notebook)
Use the notebook:
- `MappingEquivalencies.ipynb`

It supports:
- One or more services as input (comma-separated)
- Returns Azure/GCP/OSS/Quality/Notes_EN
- Exports results to a CSV in the same folder as the master map

---

## Interpretation examples
### Example 1: straightforward service mapping
If AWS service is a well-defined category (e.g., object storage),
you often get:
- One alternative per provider
- `Quality = CLOSE` or `EXACT`
- Notes explain differences (API, auth, lifecycle, eventing, etc.)

### Example 2: “approximate” mapping (composition)
If the AWS service bundles several capabilities (e.g., managed workflows + eventing + permissions),
you may see:
- A composed mapping (`A + B`) in other clouds
- `Quality = APPROX`
- Notes explain required building blocks and deltas

### Example 3: end-user actor rows
For `UserCompanyDeveloper`, the “equivalent” is **not a cloud service**:
- `Quality = NA`
- Notes: “this is an end-user actor/endpoint, do not map”

---

## Limitations and scope
- This map provides **architectural alternatives**, not official vendor guarantees.
- Features, pricing, quotas, and product boundaries change over time.
- Some services have no true equivalent due to provider-specific semantics.
- OSS alternatives may require additional components (auth, HA, monitoring, persistence) to be production-ready.

---

## Contributing / extending the map
If you add or modify entries:
1. Keep `Servicio AWS` unique and stable
2. Use `Quality` consistently based on the rubric above
3. Use Notes to justify:
   - what the alternative covers
   - what it does NOT cover
   - whether composition is required (`A + B`)
4. For non-cloud actor rows, use:
   - `Quality = NA`
   - Mapping fields as `-`
   - Notes stating: actor/end-user endpoint, not a cloud service

---

## Disclaimer and Maintenance (Instructor-Editable)

The equivalences and notes in this master map are **intentionally instructor-editable**.  
They are **subject to change** over time due to:

- updates in cloud providers (new services, deprecations, feature changes),
- different architectural interpretations or course focus,
- and **suggestions/modifications made by the instructor** running the activity.

Therefore, the map should be treated as a **living document**: the recommended alternatives and their explanations may be refined, corrected, or expanded as part of the teaching process.

This is **correct, viable, and expected** for the activity: the goal is not to enforce a fixed “official truth”, but to provide a practical, well-justified baseline that can evolve with instructor feedback and course needs.
