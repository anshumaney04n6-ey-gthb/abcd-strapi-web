# Quote Buy Fallback CMS Requirements

---

**Date:** 2026-04-19
**Purpose:** Sync UAT Strapi with LOCAL configuration for Quote Buy fallback journey content

## Table of Contents

1. [Overview](#1-quote-buy-page-overview)
2. [Content Keys (Buy Flow)](#content-keys-buy-flow)
3. [Pages (Phase 1)](#pages-phase-1)
   - [Page - Revised Premium](#page---revised-premium)
4. [Sample API Response](#sample-api-response)


---

## 1. Quote Buy Page Overview

**Content Type:** `insurance-journey-page`
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys (Buy Flow)

| Page Name | CMS Key | Fallback Constant | Content Type |
|-----------|---------|-------------------|-----------|
| Revised Premium | `revisedPremium` | `DEFAULT_REVISED_PREMIUM_CONTENT` | page |


---

## Pages (Phase 1)

---

### Page - Revised Premium

**CMS Key:** `revisedPremium`
**Fallback Constant:** `DEFAULT_REVISED_PREMIUM_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── heading (String)
    ├── previousPremium (String)
    ├── revisedPremium (String)
    ├── vehicleIconSrc (Media)
    ├── vehicleModelName (String)
    ├── policyYear (String)
    ├── vehicleRegistrationNumber (String)
    ├── planBadgeText (String)
    └── logoSrc (Media)
```

---

#### Sample JSON Data
```json
{
  "revisedPremium": {
    "enabled": true,
    "content": {
      "title": "Car insurance",
      "submitButtonText": "Continue",
      "heading": "Your premium has been revised",
      "previousPremium": "₹13,102",
      "revisedPremium": "₹14,025",
      "vehicleIconSrc": "${ASSETS_BASE}/landing/motor/motorbike.webp",
      "vehicleModelName": "Hyundai Fluidic Verna",
      "policyYear": "1-yr plan",
      "vehicleRegistrationNumber": "MH01AB1234",
      "planBadgeText": "Comprehensive plan",
      "logoSrc": "${ASSETS_BASE}/ICICILogo.webp"
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
        "revisedPremium": {
          "enabled": true,
          "content": {
            "title": "Car insurance",
            "submitButtonText": "Continue",
            "heading": "Your premium has been revised",
            "previousPremium": "₹13,102",
            "revisedPremium": "₹14,025",
            "vehicleIconSrc": "${ASSETS_BASE}/landing/motor/motorbike.webp",
            "vehicleModelName": "Hyundai Fluidic Verna",
            "policyYear": "1-yr plan",
            "vehicleRegistrationNumber": "MH01AB1234",
            "planBadgeText": "Comprehensive plan",
            "logoSrc": "${ASSETS_BASE}/ICICILogo.webp"
          }
        }
      }
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

