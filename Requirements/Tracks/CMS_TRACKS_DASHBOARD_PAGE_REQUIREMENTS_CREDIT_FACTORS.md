# Tracks CMS Dashboard Page Requirements for Credit Factors, Bank Logos, and Tips

**Date:** 2026-04-23  
**Purpose:** Sync Strapi configuration for Tracks Dashboard Page with the current `abcd-tracks-web` implementation for `creditFactors`, `bankLogos`, and `tips`

---

## Table of Contents
- [1. Dashboard Page Overview](#1-dashboard-page-overview)
- [2. Component Requirements](#2-component-requirements)
  - [2.1 New Components](#21-new-components)
  - [2.2 Update Fields](#22-update-fields)
  - [2.3 Fixed App Rules](#23-fixed-app-rules)
- [3. Sample Values](#3-sample-values)
- [4. Expected API Response](#4-expected-api-response)
- [5. Implementation Notes](#5-implementation-notes)
- [6. Summary](#6-summary)

---

## 1. Dashboard Page Overview

**Content Type:** `tracks-dashboard-pages`  
**API Endpoint:** `GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*`

### Scope Covered in This Document

This document covers only the dashboard CMS fields needed for:

- `creditFactors`
- `bankLogos`
- `tips`

This is for the Credit Track dashboard flow in `abcd-tracks-web`.

### Current App Usage

The app currently reads:

- `creditFactors.dashboardTooltip`
- `creditFactors.repaymentBanner`
- `creditFactors.creditUtilizationBanner`
- `creditFactors.creditMixBanner`
- `bankLogos[]`
- `tips.title`

These fields are transformed in the dashboard CMS layer and then consumed by:

- Dashboard tooltip section
- Factor details page banners
- Factor details account card bank logos
- Tips section title

---

## 2. Component Requirements

### 2.1 New Components

| Component Name | Type | Description |
|----------------|------|-------------|
| `creditFactors` | Component | Dashboard-level config for factor tooltip and factor detail banners |
| `credit-factor-banner-content` | Component | Reusable banner block for repayment, utilization, and mix |
| `bankLogos` | Repeatable component | Top-level lender logo mapping used by factor account cards |
| `tips` | Component | Dashboard-level config for tips section |

#### creditFactors (Component Structure)

```text
creditFactors
├── dashboardTooltip (Text)
├── repaymentBanner (Component: credit-factor-banner-content)
├── creditUtilizationBanner (Component: credit-factor-banner-content)
└── creditMixBanner (Component: credit-factor-banner-content)
```

#### credit-factor-banner-content (Component Structure)

```text
credit-factor-banner-content
├── title (String)
├── description (Text)
├── ctaLabel (String)
├── ctaUrl (String, optional)
└── enabled (Boolean)
```

#### bankLogos (Repeatable Component Structure)

```text
bankLogos[]
├── bankId (String)
├── bankName (String)
└── bankLogo (Media)
```

#### tips (Component Structure)

```text
tips
└── title (String)
```

### 2.2 Update Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `tips.title` | String | Title shown in the dashboard Tips section |

### 2.3 Fixed App Rules

These rules are fixed in the app and should not be made configurable in Strapi:

| Item | Rule |
|------|------|
| `repaymentBanner` | CTA action is fixed in app as download app flow |
| `creditUtilizationBanner` | CTA uses `ctaUrl` from CMS |
| `creditMixBanner` | CTA uses `ctaUrl` from CMS |
| `bankLogos` | Stored at top level of `tracks-dashboard-pages`, not inside `creditFactors` |
| `bankLogos` matching | App matches account `lenderName` with `bankName` |
| `creditAge` | Not handled through CMS |
| `creditEnquiries` | Not handled through CMS |
| `ctaAction` | Not needed in Strapi for this scope |
| `factorType` | Not needed in Strapi because banner ownership is defined by field name |

---

## 3. Sample Values

### creditFactors

```json
{
  "creditFactors": {
    "dashboardTooltip": "It takes up to 2 months for your latest credit activity to reflect in your credit report.",
    "repaymentBanner": {
      "title": "Repay your pending bills",
      "description": "Delayed payments lower your credit score",
      "ctaLabel": "Pay now",
      "enabled": true
    },
    "creditUtilizationBanner": {
      "title": "Apply for a personal loan",
      "description": "Consolidate your credit utilisation with a loan",
      "ctaLabel": "Apply now",
      "ctaUrl": "",
      "enabled": true
    },
    "creditMixBanner": {
      "title": "Apply for a personal loan",
      "description": "A more balanced credit mix improves your credit score",
      "ctaLabel": "Apply now",
      "ctaUrl": "",
      "enabled": true
    }
  }
}
```

### bankLogos

```json
{
  "bankLogos": [
    {
      "bankId": "hdfc-bank",
      "bankName": "HDFC Bank Ltd",
      "bankLogo": "/logos/banks/hdfc.svg"
    },
    {
      "bankId": "icici-bank",
      "bankName": "ICICI Bank Ltd",
      "bankLogo": "/logos/banks/icic.svg"
    },
    {
      "bankId": "sbi-bank",
      "bankName": "State Bank of India",
      "bankLogo": "/logos/banks/sbi.svg"
    }
  ]
}
```

### tips

```json
{
  "tips": {
    "title": "Tips for you"
  }
}
```

---

## 4. Expected API Response

```json
{
  "data": [
    {
      "id": 1,
      "subProduct": "credit",
      "partner": "default",
      "bankLogos": [
        {
          "bankId": "hdfc-bank",
          "bankName": "HDFC Bank Ltd",
          "bankLogo": {
            "url": "/uploads/hdfc_bank_logo.svg"
          }
        },
        {
          "bankId": "icici-bank",
          "bankName": "ICICI Bank Ltd",
          "bankLogo": {
            "url": "/uploads/icici_bank_logo.svg"
          }
        },
        {
          "bankId": "sbi-bank",
          "bankName": "State Bank of India",
          "bankLogo": {
            "url": "/uploads/sbi_bank_logo.svg"
          }
        }
      ],
      "tips": {
        "title": "Tips for you"
      },
      "creditFactors": {
        "dashboardTooltip": "It takes up to 2 months for your latest credit activity to reflect in your credit report.",
        "repaymentBanner": {
          "title": "Repay your pending bills",
          "description": "Delayed payments lower your credit score",
          "ctaLabel": "Pay now",
          "enabled": true
        },
        "creditUtilizationBanner": {
          "title": "Apply for a personal loan",
          "description": "Consolidate your credit utilisation with a loan",
          "ctaLabel": "Apply now",
          "ctaUrl": "",
          "enabled": true
        },
        "creditMixBanner": {
          "title": "Apply for a personal loan",
          "description": "A more balanced credit mix improves your credit score",
          "ctaLabel": "Apply now",
          "ctaUrl": "",
          "enabled": true
        }
      }
    }
  ]
}
```

---

## 5. Implementation Notes

### Required Strapi Setup

Strapi team should ensure the following configuration exists inside `tracks-dashboard-pages`:

1. `subProduct` field
2. `partner` field
3. `tips` component field
4. `creditFactors` component field
5. `bankLogos` repeatable component field at top level
6. Nested banner component fields inside `creditFactors`

### Required creditFactors Fields

| Path | Required | Notes |
|------|----------|-------|
| `creditFactors.dashboardTooltip` | Yes | Used on dashboard Important Factors tooltip |
| `creditFactors.repaymentBanner.title` | Yes | Banner heading |
| `creditFactors.repaymentBanner.description` | Yes | Banner description |
| `creditFactors.repaymentBanner.ctaLabel` | Yes | CTA label |
| `creditFactors.repaymentBanner.ctaUrl` | No | Not used by current app flow |
| `creditFactors.repaymentBanner.enabled` | Yes | Controls show or hide |
| `creditFactors.creditUtilizationBanner.title` | Yes | Banner heading |
| `creditFactors.creditUtilizationBanner.description` | Yes | Banner description |
| `creditFactors.creditUtilizationBanner.ctaLabel` | Yes | CTA label |
| `creditFactors.creditUtilizationBanner.ctaUrl` | Yes | Used for navigation |
| `creditFactors.creditUtilizationBanner.enabled` | Yes | Controls show or hide |
| `creditFactors.creditMixBanner.title` | Yes | Banner heading |
| `creditFactors.creditMixBanner.description` | Yes | Banner description |
| `creditFactors.creditMixBanner.ctaLabel` | Yes | CTA label |
| `creditFactors.creditMixBanner.ctaUrl` | Yes | Used for navigation |
| `creditFactors.creditMixBanner.enabled` | Yes | Controls show or hide |

### Required bankLogos Fields

| Path | Required | Notes |
|------|----------|-------|
| `bankLogos[].bankId` | Yes | Stable admin key for the lender logo entry |
| `bankLogos[].bankName` | Yes | Runtime lookup key used against account `lenderName` |
| `bankLogos[].bankLogo` | Yes | Strapi media field resolved by the app |

### Required tips Fields

| Path | Required | Notes |
|------|----------|-------|
| `tips.title` | Yes | Used as the dashboard tips section title |


---

## 6. Summary

| Category | Count |
|----------|-------|
| New Components | 4 |
| Updated Fields | 1 |
| Sample Values | 3 |
| API Response | 1 |

---

**Contact:** Credit Track Dashboard Team  
**Environment:** UAT / QA Strapi  
**Content Type Owner:** Tracks Dashboard CMS