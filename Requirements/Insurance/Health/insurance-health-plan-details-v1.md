# Health Insurance Plan Details - Complete Schema Documentation

## Content-Type: Insurance Health Plan Details (HIPlanDetails)

**Collection Name:** `health-insurance-plan-details`  
**Singular Name:** `health-insurance-plan-detail`  
**Plural Name:** `health-insurance-plan-details`  
**Draft & Publish:** Enabled

> **Changelog:**
> - **v1** (2026-06-04): Initial schema with `plans` and `comparisonFields`.

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `partner` | string | No | `default` | - | Optional partner-specific variant |
| `plans` | component (repeatable) | Yes | fallback | - | Health plan cards, details, policy docs, and comparison values |
| `comparisonFields` | component (repeatable) | Yes | fallback | - | Grouped metadata for comparison field title and helper text |

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/health-insurance-plan-details
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health-insurance-plan-details` | List plan details pages |
| GET | `/api/health-insurance-plan-details/:id` | Get single plan details entry by ID |
| POST | `/api/health-insurance-plan-details` | Create plan details entry |
| PUT | `/api/health-insurance-plan-details/:id` | Update plan details entry |
| DELETE | `/api/health-insurance-plan-details/:id` | Delete plan details entry |

### Query Parameters

**Filtering by Partner:**
```
?filters[partner][$eq]=default
?populate=deep
```

**Full Plan Details Query:**
```
GET /api/health-insurance-plan-details?
  filters[partner][$eq]=default&
  populate=deep
```

---

## Complete JSON Structure

> **Note:** Keep this structure aligned with health quote plan selection, compare modal, and plan details rendering.

```json
{
  "data": {
    "partner": "default",
    "plans": [
      {
        "planId": "20",
        "planName": "ABHI Activ One MAX Economy",
        "logoUrl": "/assets/health-insurance/active-one-max.webp", // media
        "ctaText": "Buy now",
        "benefits": [
          "HealthReturnsTM Upto 100%",
          "Claim Protect (Non-Medical Expense Waiver)",
          "Super Reload",
          "Super Credit"
        ],
        "showDetailsLink": true,
        "detailsLinkText": "View more details",
        "planBadge": {
          "text": "Popular",
          "backgroundColor": "purple",
          "textcolor": "white"
        },
        "planBenefits": {
          "chips": [
            {
              "chipId": "top-benefits",
              "label": "Top benefits",
              "benefits": [
                {
                  "title": "HealthReturns up to 100%",
                  "description": "Earn premium returns by maintaining healthy activity goals."
                },
                {
                  "title": "Customize your plan",
                  "description": "Adjust benefits with optional add-ons based on your family needs."
                },
                {
                  "title": "Home health care",
                  "description": "Access selected healthcare services at home under policy terms."
                }
              ]
            },
            {
              "chipId": "covered",
              "label": "What's Covered?",
              "benefits": [
                {
                  "title": "In-patient hospitalization",
                  "description": "Covers hospitalization expenses for covered illnesses and procedures."
                },
                {
                  "title": "Day care procedures",
                  "description": "Includes eligible same-day treatments that do not require 24-hour admission."
                },
                {
                  "title": "Cashless treatment",
                  "description": "Cashless access at network hospitals subject to policy terms and conditions."
                }
              ]
            },
            {
              "chipId": "Eligibility Criteria",
              "label": "Eligibility Criteria",
              "benefits": [
                {
                  "title": "Minimum/Maximum entry age (Adult)",
                  "description": [
                    "Minimum 18 years, Maximum - No capping"
                  ]
                },
                {
                  "title": "Minimum/Maximum entry age (Child)",
                  "description": [
                    "Depending Child (Floater / Multi Individual), Maximum - 91 days to 25 years",
                    "Individual - minimum age of entry - 5 years"
                  ]
                }
              ]
            },
            {
              "chipId": "waiting-period",
              "label": "Waiting period",
              "timeline": [
                {
                  "period": "30 days after activation",
                  "description": [
                    "Accidental Cover"
                  ]
                },
                {
                  "period": "2 years after activation",
                  "description": [
                    "Accidental Cover",
                    "Specific Illnesses Cover"
                  ]
                },
                {
                  "period": "3 years after activation",
                  "description": [
                    "Accidental Cover",
                    "Specific Illnesses Cover",
                    "Maternity and Newborn Cover"
                  ]
                }
              ]
            }
          ],
          "defaultChipId": "top-benefits",
          "benefitsInfo": "Optional covers are available at additional cost"
        },
        "policyDocs": {
          "docsLinkText": "Policy docs",
          "docList": [
            {
              "title": "Product brochure",
              "docUrl": "document_url_here"
            },
            {
              "title": "Product brochure",
              "docUrl": "document_url_here"
            }
          ]
        },
        "comparison": [
          {
            "fieldId": "in-patient-hospitalization",
            "value": "Available"
          },
          {
            "fieldId": "in-patient-hospitalization-2",
            "value": "Available"
          },
          {
            "fieldId": "pre-patient-hospitalization-2",
            "value": "30 days"
          },
          {
            "fieldId": "post-patient-hospitalization-2",
            "value": "60 days"
          },
          {
            "fieldId": "day-care-treatment",
            "value": "For SI up to 4L, home treatment means receiving medical care at home instead of being admitted to a hospital. This applies when a doctor confirms that hospitalisation is not required, but treatment is still necessary. It may include doctor consultations, prescribed medicines, nursing care, and basic medical equipment used at home. This option allows you to recover comfortably while still receiving appropriate medical care."
          },
          {
            "fieldId": "road-ambulance-cover-2",
            "value": [
              "Network provider - actuals",
              "Non-Network provider - upto INR 3000 per event"
            ]
          }
        ]
      }
    ],
    "comparisonFields": [
      {
        "typeId": "additional-benefits",
        "title": "Additional Benefits",
        "fields": [
          {
            "fieldId": "in-patient-hospitalization-2",
            "title": "In-patient Hospitalization",
            "helperText": "Covers treatments for which the insured has to stay in the hospital for more than 24 hours."
          }
        ]
      },
      {
        "typeId": "base-cover",
        "title": "Base Cover",
        "fields": [
          {
            "fieldId": "pre-patient-hospitalization-2",
            "title": "Pre-hospitalization Medical Expenses",
            "helperText": "Costs incurred before your hospitalisation will be covered where the hospitalisation claim is accepted by the company."
          }
        ]
      }
    ]
  }
}
```

---

## Components Detail

### 1. insurance-plan-details.plan

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `planId` | string | Yes | - |
| `planName` | string | Yes | - |
| `logoUrl` | media | No | - |
| `ctaText` | string | Yes | `Buy now` |
| `benefits` | string[] | No | [] |
| `showDetailsLink` | boolean | No | `true` |
| `detailsLinkText` | string | No | `View more details` |
| `planBadge` | component (`insurance-plan-details.plan-badge`) | No | - |
| `planBenefits` | component (`insurance-plan-details.plan-benefits`) | No | - |
| `policyDocs` | component (`insurance-plan-details.policy-docs`) | No | - |
| `comparison` | component repeatable (`insurance-plan-details.comparison-item`) | No | [] |

### 2. insurance-plan-details.plan-badge

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `text` | string | Yes | - |
| `backgroundColor` | string | No | - |
| `textcolor` | string | No | - |

### 3. insurance-plan-details.plan-benefits

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `chips` | component repeatable (`insurance-plan-details.plan-benefit-chip`) | No | [] |
| `defaultChipId` | string | No | - |
| `benefitsInfo` | string | No | - |

### 4. insurance-plan-details.plan-benefit-chip

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `chipId` | string | Yes | - |
| `label` | string | Yes | - |
| `benefits` | component repeatable (`insurance-plan-details.plan-benefit-item`) | No | [] |
| `timeline` | component repeatable (`insurance-plan-details.plan-benefit-timeline-item`) | No | [] |

### 5. insurance-plan-details.plan-benefit-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `description` | string or string[] | No | - |

### 6. insurance-plan-details.plan-benefit-timeline-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `period` | string | Yes | - |
| `description` | string[] | No | [] |

### 7. insurance-plan-details.policy-docs

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `docsLinkText` | string | No | `Policy docs` |
| `docList` | component repeatable (`insurance-plan-details.policy-doc-item`) | No | [] |

### 8. insurance-plan-details.policy-doc-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `docUrl` | string | Yes | - |

### 9. insurance-plan-details.comparison-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `fieldId` | string | Yes | - |
| `value` | string or string[] | Yes | - |

### 10. insurance-plan-details.comparison-field-group

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `typeId` | string | Yes | - |
| `title` | string | Yes | - |
| `fields` | component repeatable (`insurance-plan-details.comparison-field`) | Yes | [] |

### 11. insurance-plan-details.comparison-field

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `fieldId` | string | Yes | - |
| `title` | string | Yes | - |
| `helperText` | string | No | - |

## Populate Query for Full Response

```
GET /api/health-insurance-plan-details?
filters[partner][$eq]=default&
populate=deep
```

---

## Notes

- Replace `data[0].plans.logoUrl` string paths with Strapi media relation.
- `data[0].plans.comparison.value` supports both scalar and list types to support compare table rows with multiline values.
