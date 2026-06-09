# FD Genie Rate Table - Schema Refactoring Requirements

## Overview

This document outlines the restructuring of the `fdGenieRates` component from a flat array to a **grouped-by-bank** structure. The goal is to:

1. Add a new `bankCode` field as a unique bank identifier (for lookups against `BANK_MAPPING`)
2. Keep `providerName` for display and sort purposes
3. Globalize `bankCode`, `providerName`, `bankLogo`, and `rbiRegulated` as top-level bank fields
4. Move tenure-specific rate data into a nested `rates` array per bank

---

## Structure

**Component:** `investments-dashboard.fd-genie-rate`

A grouped array where each entry represents a **bank** with its global properties, containing a nested `rates` array for tenure-specific data.

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
        "compoundingType": "Quarterly",s
        "compoundingValue": 4
      }
    ]
  },
  {
    "bankCode": "SMCBIN",
    "providerName": "Unity SF Bank",
    "bankLogo": "media_or_url",
    "rbiRegulated": true,
    "rates": [
      {
        "tenureMonths": 12,
        "regularRate": 8.05,
        "seniorCitizenRate": 8.3,
        "womanRate": 8.15,
        "compoundingType": "Monthly",
        "compoundingValue": 12
      }
    ]
  }
]
```

---

## Component Schema Detail

### Parent Component: `investments-dashboard.fd-genie-rate` (refactored)

| Field          | Type         | Required | Default | Description                                                                    |
| -------------- | ------------ | -------- | ------- | ------------------------------------------------------------------------------ |
| `bankCode`     | string       | Yes      | -       | Unique bank identifier (e.g., `UTKSIN`, `SMCBIN`) matching `BANK_MAPPING` keys |
| `providerName` | string       | Yes      | -       | Human-readable bank name for display and sort (e.g., "Shivalik SF Bank")       |
| `bankLogo`     | media/string | No       | -       | Bank logo asset URL                                                            |
| `rbiRegulated` | boolean      | No       | `true`  | Whether the bank is RBI regulated                                              |
| `rates`        | component[]  | Yes      | -       | Array of tenure-specific rate entries                                          |

---

### Sub-Component: `investments-dashboard.fd-genie-rate-entry`

| Field               | Type   | Required | Default | Description                                                            |
| ------------------- | ------ | -------- | ------- | ---------------------------------------------------------------------- |
| `tenureMonths`      | number | Yes      | -       | FD tenure in months                                                    |
| `regularRate`       | number | Yes      | -       | Interest rate for regular customers (%)                                |
| `seniorCitizenRate` | number | Yes      | -       | Interest rate for senior citizens (%)                                  |
| `womanRate`         | number | Yes      | -       | Interest rate for women (%)                                            |
| `compoundingType`   | string | No       | -       | Compounding frequency label (e.g., "Quarterly", "Monthly")             |
| `compoundingValue`  | number | Yes      | -       | Compounding frequency per year (e.g., 4 for quarterly, 12 for monthly) |

---

## Field Mapping Reference

| Old Field           | New Field                   | Location                                                                             |
| ------------------- | --------------------------- | ------------------------------------------------------------------------------------ |
| `providerName`      | `providerName`              | Moved to parent level (no longer duplicated per tenure); retained for display & sort |
| _(new)_             | `bankCode`                  | New field at parent level; unique identifier matching `BANK_MAPPING` keys            |
| `bankLogo`          | `bankLogo`                  | Moved to parent level (no longer duplicated per tenure)                              |
| `rbiRegulated`      | `rbiRegulated`              | Moved to parent level (no longer duplicated per tenure)                              |
| `tenureMonths`      | `rates[].tenureMonths`      | Moved into nested `rates` array                                                      |
| `regularRate`       | `rates[].regularRate`       | Moved into nested `rates` array                                                      |
| `seniorCitizenRate` | `rates[].seniorCitizenRate` | Moved into nested `rates` array                                                      |
| `womanRate`         | `rates[].womanRate`         | Moved into nested `rates` array                                                      |
| `compoundingType`   | `rates[].compoundingType`   | Moved into nested `rates` array                                                      |
| `compoundingValue`  | `rates[].compoundingValue`  | Moved into nested `rates` array                                                      |

## API Endpoints

### Base URL

```
/api/investments-dashboard-pages
```

### Endpoints

| Method | Endpoint                               | Description                                        |
| ------ | -------------------------------------- | -------------------------------------------------- |
| GET    | `/api/investments-dashboard-pages`     | List all dashboard pages (includes `fdGenieRates`) |
| GET    | `/api/investments-dashboard-pages/:id` | Get single dashboard page with rates               |
| PUT    | `/api/investments-dashboard-pages/:id` | Update dashboard page (including `fdGenieRates`)   |

### Query Parameters

```
?populate[fdGenieRates][populate]=*
?populate[fdGenieRates][populate][rates]=*
?filters[subProduct][$eq]=fixed-deposits
?filters[partner][$eq]=default
```

### Sample API Response (New Structure)

```json
{
  "data": {
    "id": 1,
    "attributes": {
      "subProduct": "fixed-deposits",
      "partner": "default",
      "fdGenieRates": [
        {
          "bankCode": "UTKSIN",
          "providerName": "Shivalik SF Bank",
          "bankLogo": {
            "id": 101,
            "url": "https://storage.example.com/logos/banks/shivalik.svg",
            "alternativeText": "Shivalik SF Bank"
          },
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
        },
        {
          "bankCode": "SMCBIN",
          "providerName": "Unity SF Bank",
          "bankLogo": {
            "id": 102,
            "url": "https://storage.example.com/logos/banks/suryoday.svg",
            "alternativeText": "Unity SF Bank"
          },
          "rbiRegulated": true,
          "rates": [
            {
              "tenureMonths": 12,
              "regularRate": 8.05,
              "seniorCitizenRate": 8.3,
              "womanRate": 8.15,
              "compoundingType": "Monthly",
              "compoundingValue": 12
            }
          ]
        }
      ]
    }
  }
}
```

### Sample PUT Request Body (Creating/Updating Rates)

```json
{
  "data": {
    "fdGenieRates": [
      {
        "bankCode": "UTKSIN",
        "providerName": "Shivalik SF Bank",
        "bankLogo": 101,
        "rbiRegulated": true,
        "rates": [
          {
            "tenureMonths": 12,
            "regularRate": 8.75,
            "seniorCitizenRate": 9.0,
            "womanRate": 8.85,
            "compoundingType": "Quarterly",
            "compoundingValue": 4
          }
        ]
      }
    ]
  }
}
```

---
### Create Components

1. **`investments-dashboard.fd-genie-rate`** (new grouped component)
   - `bankCode` — Short text, required, unique
   - `providerName` — Short text, required
   - `bankLogo` — Media (single), optional
   - `rbiRegulated` — Boolean, default `true`
   - `rates` — Component (repeatable) → `investments-dashboard.fd-genie-rate-entry`

2. **`investments-dashboard.fd-genie-rate-entry`** (new sub-component)
   - `tenureMonths` — Number (integer), required
   - `regularRate` — Number (decimal), required
   - `seniorCitizenRate` — Number (decimal), required
   - `womanRate` — Number (decimal), required
   - `compoundingType` — Short text, optional
   - `compoundingValue` — Number (integer), required

---



