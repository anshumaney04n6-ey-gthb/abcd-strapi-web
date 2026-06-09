# Quote Buy Fallback CMS Requirements

---

**Date:** 2026-04-19
**Purpose:** Sync UAT Strapi with LOCAL configuration for Quote Buy fallback journey content

## Table of Contents

1. [Overview](#1-quote-buy-page-overview)
2. [Content Keys (Buy Flow)](#content-keys-buy-flow)
3. [Pages (Phase 1)](#pages-phase-1)
   - [Page - Quote Plan Details](#page---quote-plan-details)
4. [Sample API Response](#sample-api-response)


---

## 1. Quote Buy Page Overview

**Content Type:** `insurance-journey-page`
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys (Buy Flow)

| Page Name | CMS Key |  Content Type |
|-----------|---------|-----------|
| Quote Plan Details | `quotePlanDetails`  | page |

---

## Pages (Phase 1)


---

### Page - Quote Plan Details

**CMS Key:** `quotePlanDetails`
**Fallback Constant:** `DEFAULT_QUOTE_PLAN_DETAILS_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── policyYear (String)
    ├── logoSrc (String)
    ├── logoAlt (String)
    ├── quotePlanDetailsIcons (Object)
    │   ├── networkGarages (String)
    │   ├── claimRatio (String)
    │   ├── roadsideAssistanceIcon (String)
    │   ├── creditScorePromoIconSrc (String)
    │   ├── creditScorePromoIconAlt (String)
    │   ├── creditScoreChevronIconSrc (String)
    │   ├── availabilityIcon (String)
    │   ├── availabilityIconAlt (String)
    │   ├── unlockIcon (String)
    │   ├── infoIcon (String)
    │   ├── creditScoreUnlockIconSrc (String)
    │   └── creditScoreUnlockIconAlt (String)
    └── upsellAddons (Array)
        ├── id (String)
        ├── name (String)
        ├── label (String)
        ├── checked (Boolean)
        ├── logo (String)
        ├── description (String)
        └── minAmount (Number, Optional)

```

---

#### Sample JSON Data
```json
{
  "quotePlanDetails": {
    "enabled": true,
    "content": {
      "title": "Select Plan",
      "policyYear": "1-yr plan",
      "logoSrc": "${ASSETS_BASE}/dashboard/icic.webp",
      "logoAlt": "ICICI Lombard",
      "quotePlanDetailsIcons": {
        "networkGarages": "${ASSETS_BASE}/motor/Icon.webp",
        "claimRatio": "${ASSETS_BASE}/motor/check-circle.webp",
        "roadsideAssistanceIcon": "${ASSETS_BASE}/motor/tow-truck.webp",
        "creditScorePromoIconSrc": "${ASSETS_BASE}/motor/percent.webp",
        "creditScorePromoIconAlt": "Credit Score",
        "creditScoreChevronIconSrc": "${ASSETS_BASE}/motor/chevron-right-circle.webp",
        "availabilityIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
        "availabilityIconAlt": "Information",
        "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
        "infoIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
        "creditScoreUnlockIconSrc": "${ASSETS_BASE}/motor/percentage.webp",
        "creditScoreUnlockIconAlt": "Unlock savings"
      },
      "upsellAddons": [
        {
          "id": "4",
          "name": "Zero Depreciation",
          "label": "Zero dep",
          "checked": false,
          "logo": "",
          "description": "Zero depreciation cover"
        },
        {
          "id": "1",
          "name": "Personal Accident Cover",
          "label": "PA cover",
          "checked": false,
          "logo": "",
          "description": "Personal accident cover",
          "minAmount": 1500000
        }
      ]
    }
  }
}
```

---

## Sample API Response

```json
{
  "data": [
    {
      
      "quotePlanDetails": {
        "enabled": true,
        "content": {
          "title": "Select Plan",
          "policyYear": "1-yr plan",
          "logoSrc": "${ASSETS_BASE}/dashboard/icic.webp",
          "logoAlt": "ICICI Lombard",
          "quotePlanDetailsIcons": {
            "networkGarages": "${ASSETS_BASE}/motor/Icon.webp",
            "claimRatio": "${ASSETS_BASE}/motor/check-circle.webp",
            "roadsideAssistanceIcon": "${ASSETS_BASE}/motor/tow-truck.webp",
            "creditScorePromoIconSrc": "${ASSETS_BASE}/motor/percent.webp",
            "creditScorePromoIconAlt": "Credit Score",
            "creditScoreChevronIconSrc": "${ASSETS_BASE}/motor/chevron-right-circle.webp",
            "availabilityIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
            "availabilityIconAlt": "Information",
            "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
            "infoIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
            "creditScoreUnlockIconSrc": "${ASSETS_BASE}/motor/percentage.webp",
            "creditScoreUnlockIconAlt": "Unlock savings"
          },
          "upsellAddons": [
            {
              "id": "4",
              "name": "Zero Depreciation",
              "label": "Zero dep",
              "checked": false,
              "logo": "",
              "description": "Zero depreciation cover"
            },
            {
              "id": "1",
              "name": "Personal Accident Cover",
              "label": "PA cover",
              "checked": false,
              "logo": "",
              "description": "Personal accident cover",
              "minAmount": 1500000
            }
          ]
        }
      },
     
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 1,
      "total": 1
    }
  }
}
```

---

