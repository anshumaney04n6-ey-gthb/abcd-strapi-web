# Investment Dashboard v6 - Field Removals

## Overview

This document outlines fields to be **removed** from the Strapi schema across three sections:

1. `fdGenie` — Dashboard page component
2. `bookFD` — Dashboard page component
3. `investments-bank-detail` — Bank detail collection type

---

## API Endpoints

### Dashboard Page

```
/api/investments-dashboard-pages
```

| Method | Endpoint                               | Description               |
| ------ | -------------------------------------- | ------------------------- |
| GET    | `/api/investments-dashboard-pages`     | List all dashboard pages  |
| GET    | `/api/investments-dashboard-pages/:id` | Get single dashboard page |
| PUT    | `/api/investments-dashboard-pages/:id` | Update dashboard page     |

### Bank Detail

```
/api/investments-bank-details
```

| Method | Endpoint                            | Description            |
| ------ | ----------------------------------- | ---------------------- |
| GET    | `/api/investments-bank-details`     | List all bank details  |
| GET    | `/api/investments-bank-details/:id` | Get single bank detail |
| PUT    | `/api/investments-bank-details/:id` | Update bank detail     |

---

## Field Change Mapping (With Arrows)

| Change Type | Mapping                                  |
| ----------- | ---------------------------------------- |
| REMOVE      | `fdGenie.heading` -> removed             |
| REMOVE      | `fdGenie.depositRange.min` -> removed    |
| REMOVE      | `fdGenie.depositRange.max` -> removed    |
| REMOVE      | `fdGenie.seniorCitizenLabel` -> removed  |
| REMOVE      | `fdGenie.womanLabel` -> removed          |
| REMOVE      | `fdGenie.ctaLabel` -> removed            |
| REMOVE      | `bookFD.stopLineIconSrc` -> removed      |
| REMOVE      | `bankDetail.rateTableColumns` -> removed |
| REMOVE      | `bankDetail.rateTableRows` -> removed    |

---

## Fields To Remove

### Section 1: `fdGenie` (Dashboard Page)

| Parent Section         | Field                | Type   | Reason                                                       |
| ---------------------- | -------------------- | ------ | ------------------------------------------------------------ |
| `fdGenie`              | `heading`            | string | Heading is hardcoded in the frontend, not CMS-configurable   |
| `fdGenie.depositRange` | `min`                | number | Deposit range min is handled by frontend logic               |
| `fdGenie.depositRange` | `max`                | number | Deposit range max is handled by frontend logic               |
| `fdGenie`              | `seniorCitizenLabel` | string | Label is hardcoded in the frontend, not CMS-configurable     |
| `fdGenie`              | `womanLabel`         | string | Label is hardcoded in the frontend, not CMS-configurable     |
| `fdGenie`              | `ctaLabel`           | string | CTA label is hardcoded in the frontend, not CMS-configurable |

> **Note:** After removing `min` and `max`, if `depositRange` has no remaining fields, the entire `depositRange` sub-component can be removed.

### Section 2: `bookFD` (Dashboard Page)

| Parent Section | Field             | Type         | Reason                                                   |
| -------------- | ----------------- | ------------ | -------------------------------------------------------- |
| `bookFD`       | `stopLineIconSrc` | media/string | Icon is handled by frontend assets, not CMS-configurable |

### Section 3: `investments-bank-detail` (Bank Detail Collection)

| Parent Section            | Field              | Type        | Reason                                                            |
| ------------------------- | ------------------ | ----------- | ----------------------------------------------------------------- |
| `investments-bank-detail` | `rateTableColumns` | component[] | Rate table columns are now derived from `fdGenieRates` at runtime |
| `investments-bank-detail` | `rateTableRows`    | component[] | Rate table rows are now derived from `fdGenieRates` at runtime    |

---

## Before vs After JSON Structure

### `fdGenie` — Before (Current)

```json
"fdGenie": {
  "heading": "Find the FD that fits you",
  "depositRange": {
    "min": 1000,
    "max": 10000000
  },
  "tenureChips": [
    {
      "label": "1Y to 2Y",
      "minMonths": 12,
      "maxMonths": 24
    }
  ],
  "seniorCitizenLabel": "Senior citizen",
  "womanLabel": "Woman",
  "ctaLabel": "Get my Best FD Options"
}
```

### `fdGenie` — After (v6)

```json
"fdGenie": {
  "tenureChips": [
    {
      "label": "1Y to 2Y",
      "minMonths": 12,
      "maxMonths": 24
    }
  ]
}
```

### `bookFD` — Before (Current)

```json
"bookFD": {
  "title": "Book an FD in 5 easy steps",
  "highlightedText": "5 easy steps",
  "rectangleLineIconSrc": "media_or_url",
  "stopLineIconSrc": "media_or_url",
  "checkmarkIconSrc": "media_or_url",
  "steps": [...],
  "requiredDocuments": [...]
}
```

### `bookFD` — After (v6)

```json
"bookFD": {
  "title": "Book an FD in 5 easy steps",
  "highlightedText": "5 easy steps",
  "rectangleLineIconSrc": "media_or_url",
  "checkmarkIconSrc": "media_or_url",
  "steps": [...],
  "requiredDocuments": [...]
}
```

### `investments-bank-detail` — Before (Current)

```json
{
  "fsiCode": "UTKSIN",
  "bankCode": "UTKSIN",
  "bankName": "Shivalik SF Bank",
  "bankLogo": { "media_object" },
  "bankLogoUrl": "https://cdn.example.com/logos/shivalik.svg",
  "interestRate": "7%",
  "interestRateUnit": "%",
  "interestLabel": "Interest now",
  "fdDeepLink": "...",
  "rdDeepLink": "...",
  "providerAlias": ["Shivalik", "Shivalik SF Bank"],
  "rateTableColumns": [
    { "key": "tenure", "label": "Tenure", "align": "left" },
    { "key": "general", "label": "General", "align": "center" },
    { "key": "seniorCitizen", "label": "Senior Citizen", "align": "center" }
  ],
  "rateTableRows": [
    {
      "id": "row-1",
      "values": {
        "tenure": "1 Year",
        "general": "7.00%",
        "seniorCitizen": "7.50%"
      }
    }
  ],
  "actionSheetProps": {...},
  "featureListProps": {...},
  "infoItems": [...],
  "highlightCardProps": {...}
}
```

### `investments-bank-detail` — After (v6)

```json
{
  "fsiCode": "UTKSIN",
  "bankCode": "UTKSIN",
  "bankName": "Shivalik SF Bank",
  "bankLogo": { "media_object" },
  "bankLogoUrl": "https://cdn.example.com/logos/shivalik.svg",
  "interestRate": "7%",
  "interestRateUnit": "%",
  "interestLabel": "Interest now",
  "fdDeepLink": "...",
  "rdDeepLink": "...",
  "providerAlias": ["Shivalik", "Shivalik SF Bank"],
  "actionSheetProps": {...},
  "featureListProps": {...},
  "infoItems": [...],
  "highlightCardProps": {...}
}
```

---

## Removed Sub-Components (Can Be Deleted from Strapi)

After removing the fields, the following sub-components are no longer referenced and can be safely deleted:

| Sub-Component                                  | Was Used By                       |
| ---------------------------------------------- | --------------------------------- |
| `investments-dashboard.fd-genie-deposit-range` | `fdGenie.depositRange` (if empty) |
| `investments-bank-detail.rate-table-column`    | `rateTableColumns`                |
| `investments-bank-detail.rate-table-row`       | `rateTableRows`                   |

