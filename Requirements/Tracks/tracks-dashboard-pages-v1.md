# Tracks CMS Dashboard Page Requirements v1

**Date:** 2026-04-17  
**Purpose:** Sync Strapi with local configuration for the Tracks Dashboard Page cross-sell banners section

---

## Table of Contents
- [1. Dashboard Page Overview](#1-dashboard-page-overview)
- [2. Component Requirements](#2-component-requirements)
  - [2.1 New Components](#21-new-components)
  - [2.2 Collection Component Structure](#22-collection-component-structure)
- [3. Sample Values](#3-sample-values)
- [4. Expected API Response](#4-expected-api-response)
- [5. Authoring Notes](#5-authoring-notes)
- [6. Summary](#6-summary)

---

## 1. Dashboard Page Overview

**Content Type:** `tracks-dashboard-page`  
**API Endpoint:** `GET /api/tracks-dashboard-pages?populate=*`

This dashboard page includes a new component named `crossSellBanners`.

Note: add this crossSellBanner as new key in the previous response.

The `crossSellBanners` component stores the full configuration for the cross-sell recommendation section shown on the Tracks customer dashboard.

---

## 2. Component Requirements

### 2.1 New Components

| Component Name | Type | Description |
|----------------|------|-------------|
| `crossSellBanners` | Component | Stores cross-sell section configuration for the Tracks dashboard |

#### crossSellBanners (Component Structure)

```txt
crossSellBanners
├── enabled (Boolean)
├── sectionTitle (String)
├── scoreThreshold (Number)
└── banners (Repeatable component - crossSellBanners)
```

### 2.2 Collection Component Structure

The `crossSellBanners` component uses a repeatable component collection named `banners`.

#### banners (Repeatable Component Structure)

```txt
banners
├── order (Integer)
├── id (String)
├── segment (Enumeration: high, low)
├── title (String)
├── highlightedText (String, optional)
├── subtitle (Text)
├── ctaText (String)
├── ctaUrl (String)
├── icon (Media, single)
└── iconAlt (String)
```

Field notes:

- `segment` must be restricted to `high` or `low`.
- `id` should remain stable for analytics and tracking.
- `ctaUrl` is required for navigation.
- `iconAlt` is required for accessibility.
- `order` is optional and lower values should appear first.

---

## 3. Sample Values

### crossSellBanners

```json
{
  "crossSellBanners": {
    "enabled": true,
    "sectionTitle": "Products recommended for you",
    "scoreThreshold": 700,
    "banners": [
      {
        "order": 1,
        "id": "bl-banner",
        "segment": "high",
        "title": "Buy Now Pay Later",
        "highlightedText": null,
        "subtitle": "Shop now and pay in easy installments",
        "ctaText": "Explore options",
        "ctaUrl": "/bnpl",
        "icon": "",
        "iconAlt": "BNPL"
      },
      {
        "order": 2,
        "id": "pl-banner",
        "segment": "high",
        "title": "Get instant loans up to Rs 15 Lakh",
        "highlightedText": "Rs 15 Lakh",
        "subtitle": "Apply for a personal loan in minutes",
        "ctaText": "Apply now",
        "ctaUrl": "https://www.abcd.com/personal-loan",
        "icon": "",
        "iconAlt": "Personal Loan"
      },
      {
        "order": 3,
        "id": "cc-banner",
        "segment": "low",
        "title": "FD Backed Credit Card",
        "highlightedText": null,
        "subtitle": "Get a credit card with FD as collateral",
        "ctaText": "Apply now",
        "ctaUrl": "/credit-card",
        "icon": "",
        "iconAlt": "Credit Card"
      }
    ]
  }
}
```

---

## 4. Expected API Response

```json
{
    "crossSellBanners": {
      "enabled": true,
      "sectionTitle": "Products recommended for you",
      "scoreThreshold": 700,
      "banners": [
        {
          "order": 1,
          "id": "bl-banner",
          "segment": "high",
          "title": "Buy Now Pay Later",
          "highlightedText": null,
          "subtitle": "Shop now and pay in easy installments",
          "ctaText": "Explore options",
          "ctaUrl": "/bnpl",
          "icon": "",
          "iconAlt": "BNPL"
        },
        {
          "order": 2,
          "id": "pl-banner",
          "segment": "high",
          "title": "Get instant loans up to Rs 15 Lakh",
          "highlightedText": "Rs 15 Lakh",
          "subtitle": "Apply for a personal loan in minutes",
          "ctaText": "Apply now",
          "ctaUrl": "https://www.abcd.com/personal-loan",
          "icon": "",
          "iconAlt": "Personal Loan"
        },
        {
          "order": 3,
          "id": "cc-banner",
          "segment": "low",
          "title": "FD Backed Credit Card",
          "highlightedText": null,
          "subtitle": "Get a credit card with FD as collateral",
          "ctaText": "Apply now",
          "ctaUrl": "/credit-card",
          "icon": "",
          "iconAlt": "Credit Card"
        }
      ]
    }
}
```

## 6. Summary

| Category | Count |
|----------|-------|
| New Components | 1 |
| Collection Components | 1 |
| Sample Values | 1 |
| API Response | 1 |

---

**Contact:** Tracks Dashboard Team  
**Environment:** Strapi