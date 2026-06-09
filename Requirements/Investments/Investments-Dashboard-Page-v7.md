# Investment Dashboard v7 - Field Changes

## Overview

This document outlines field changes across two sections:
1. `fdGenieRates` — Add new `maxInterestRate` field at the bank level
2. `explore.fdMasterTable` — Remove `value` from `interestRate` sub-component

---

## API Endpoints

### Base URL

```
/api/investments-dashboard-pages
```

### Endpoints

| Method | Endpoint                               | Description               |
| ------ | -------------------------------------- | ------------------------- |
| GET    | `/api/investments-dashboard-pages`     | List all dashboard pages  |
| GET    | `/api/investments-dashboard-pages/:id` | Get single dashboard page |
| PUT    | `/api/investments-dashboard-pages/:id` | Update dashboard page     |

### Query Parameters

```
?populate=*
?populate[fdGenieRates][populate][rates]=*
?filters[subProduct][$eq]=fixed-deposits
?filters[partner][$eq]=default
```

---

## Field Change Mapping (With Arrows)

| Change Type | Mapping                                              |
| ----------- | ---------------------------------------------------- |
| ADD         | `fdGenieRates[].maxInterestRate` -> added            |
| REMOVE      | `explore.fdMasterTable[].interestRate.value` -> removed |

---

## Fields To Add

### Section 1: `fdGenieRates` (Dashboard Page — Grouped Format)

| Parent Section      | Field              | Type            | Required | Default | Description                                                        |
| ------------------- | ------------------ | --------------- | -------- | ------- | ------------------------------------------------------------------ |
| `fdGenieRates[]`    | `maxInterestRate`  | number (decimal)| No       | -       | Maximum interest rate offered by the bank across all tenure/category combinations |

> **Note:** `maxInterestRate` is a top-level bank field (same level as `bankCode`, `providerName`, `bankLogo`, `rbiRegulated`). It is NOT inside the nested `rates[]` array.

---

## Fields To Remove

### Section 2: `explore.fdMasterTable[].interestRate` (Dashboard Page)

| Parent Section                            | Field   | Type           | Reason                                                                      |
| ----------------------------------------- | ------- | -------------- | --------------------------------------------------------------------------- |
| `explore.fdMasterTable[].interestRate`    | `value` | number/string  | Interest rate value is now derived from `fdGenieRates` at runtime using `maxInterestRate` or computed from rates data |

---

## Before vs After JSON Structure

### `fdGenieRates` — Before (Current)

```json
"fdGenieRates": [
  {
    "bankCode": "UTKSIN",
    "providerName": "Shivalik SF Bank",
    "bankLogo": "media",
    "rbiRegulated": true,
    "rates": [
      {
        "tenureMonths": 12,
        "regularRate": 8.75,
        "seniorCitizenRate": 9.0,
        "womanRate": 8.85,
        "compoundingType": "Quarterly",
        "compoundingValue": 4
      },
      {
        "tenureMonths": 24,
        "regularRate": 8.9,
        "seniorCitizenRate": 9.1,
        "womanRate": 8.95,
        "compoundingType": "Quarterly",
        "compoundingValue": 4
      }
    ]
  }
]
```

### `fdGenieRates` — After (v7)

```json
"fdGenieRates": [
  {
    "bankCode": "UTKSIN",
    "providerName": "Shivalik SF Bank",
    "bankLogo": "media",
    "rbiRegulated": true,
    "maxInterestRate": 9.33,
    "rates": [
      {
        "tenureMonths": 12,
        "regularRate": 8.75,
        "seniorCitizenRate": 9.0,
        "womanRate": 8.85,
        "compoundingType": "Quarterly",
        "compoundingValue": 4
      },
      {
        "tenureMonths": 24,
        "regularRate": 8.9,
        "seniorCitizenRate": 9.1,
        "womanRate": 8.95,
        "compoundingType": "Quarterly",
        "compoundingValue": 4
      }
    ]
  }
]
```

---

### `explore.fdMasterTable[].interestRate` — Before (Current)

```json
"fdMasterTable": [
  {
    "fdMasterTableItemId": "suryoday",
    "bankCode": "SMCBIN",
    "bankName": "Suryoday SF Bank",
    "logo": "media_or_url",
    "isBank": true,
    "isNBFC": false,
    "isTaxSaver": false,
    "highlightBadge": {
      "label": "High Returns",
      "theme": "yellow"
    },
    "subBadge": {
      "label": "optional",
      "theme": "optional"
    },
    "features": ["feature text"],
    "interestRate": {
      "prefix": "up to",
      "value": 8.05,
      "unit": "p.a"
    },
    "cta": {
      "label": "Book FD",
      "action": "BOOK_FD"
    }
  }
]
```

### `explore.fdMasterTable[].interestRate` — After (v7)

```json
"fdMasterTable": [
  {
    "fdMasterTableItemId": "suryoday",
    "bankCode": "SMCBIN",
    "bankName": "Suryoday SF Bank",
    "logo": "media_or_url",
    "isBank": true,
    "isNBFC": false,
    "isTaxSaver": false,
    "highlightBadge": {
      "label": "High Returns",
      "theme": "yellow"
    },
    "subBadge": {
      "label": "optional",
      "theme": "optional"
    },
    "features": ["feature text"],
    "interestRate": {
      "prefix": "up to",
      "unit": "p.a"
    },
    "cta": {
      "label": "Book FD",
      "action": "BOOK_FD"
    }
  }
]
```

---

## Updated Component Schemas

### `investments-dashboard.fd-genie-rate` (Updated)

| Field              | Type            | Required | Default | Description                                                                    |
| ------------------ | --------------- | -------- | ------- | ------------------------------------------------------------------------------ |
| `bankCode`         | string          | Yes      | -       | Unique bank identifier (e.g., `UTKSIN`, `SMCBIN`) matching `BANK_MAPPING` keys |
| `providerName`     | string          | Yes      | -       | Human-readable bank name for display and sort                                  |
| `bankLogo`         | media/string    | No       | -       | Bank logo asset URL                                                            |
| `rbiRegulated`     | boolean         | No       | `true`  | Whether the bank is RBI regulated                                              |
| `maxInterestRate`  | number (decimal)| No       | -       | **NEW** — Maximum interest rate offered by the bank (%)                        |
| `rates`            | component[]     | Yes      | -       | Array of tenure-specific rate entries                                          |

### `investments-dashboard.explore-interest-rate` (Updated)

| Field    | Type   | Required | Default   | Description                                     |
| -------- | ------ | -------- | --------- | ----------------------------------------------- |
| `prefix` | string | No       | `"up to"` | Text prefix before rate display                 |
| ~~`value`~~ | ~~number/string~~ | ~~Yes~~ | ~~-~~ | ~~Interest rate value~~ — **REMOVED** |
| `unit`   | string | No       | `"p.a"`   | Unit suffix after rate display                  |

