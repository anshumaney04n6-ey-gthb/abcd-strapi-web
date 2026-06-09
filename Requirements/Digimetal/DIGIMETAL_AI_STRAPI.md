# Digimetal AI Insights Strapi Reference

**Date:** 2026-05-08
**Purpose:** Reference document for Strapi configuration of `aiInsights` consumed in `abcd-digimetal-web`

---

## 1. Overview

**Content Type:** `digimetal-dashboard-pages`

**API Endpoints:**

```http
GET /api/digimetal-dashboard-pages?filters[subProduct][$eq]=gold&filters[partner][$eq]=default&populate=*
GET /api/digimetal-dashboard-pages?filters[subProduct][$eq]=silver&filters[partner][$eq]=default&populate=*
```

This document is intended for the Strapi team and covers the `aiInsights` CMS fields that should remain available for both DigiGold and DigiSilver dashboard flows.

The `aiInsights` block is consumed in the CMS transformation layer and then used by the UI as the single source of truth to control:

- Global AI Insights enablement
- Banner header and CTA labels
- Mascot image asset
- Screen-level visibility toggles
- Dashboard, Buy, SIP, Summary, and Success banner display

---

## 2. In Scope

This document covers the following dashboard CMS area:

- `aiInsights`

The same `aiInsights` schema should be maintained for both supported products:

- `gold`
- `silver`

These fields are used by the app for the following screen mappings:

- `dashboard` -> customer dashboard banner
- `buy` -> buy collect transaction details page
- `buy-summary` -> buy transaction summary page
- `sip-details` -> SIP collect details page
- `sip-summary` -> SIP transaction summary page
- `success` -> buy thank you and SIP thank you pages

---

## 3. Required Components

### 3.1 `aiInsights`

Reusable content block for the Ask AI banner.

```text
aiInsights
├── enabled (Boolean)
├── header (String)
├── mascotImage (Media)
├── ctaLabel (String)
└── screenConfig (Object)
```

### 3.2 `aiInsights.screenConfig`

Nested screen-level visibility configuration.

```text
aiInsights.screenConfig
├── dashboard
│   └── enabled (Boolean)
├── buy
│   └── enabled (Boolean)
├── buy-summary
│   └── enabled (Boolean)
├── sip-details
│   └── enabled (Boolean)
├── sip-summary
│   └── enabled (Boolean)
└── success
    └── enabled (Boolean)
```

Important:

- `aiInsights` should remain available wherever the app currently reads it
- `screenConfig` should continue to expose all six supported screen keys
- `mascotImage` should be configured as a Strapi media field
- The app can read a direct string URL for `mascotImage`, but Strapi media is the preferred format
- `success` is shared by both Buy and SIP thank-you flows
- The same field structure should be present for both `gold` and `silver` dashboard CMS entries

---

## 4. Fields To Keep In Strapi

### 4.1 Required Top-Level Fields

| Field | Type | Required | Notes |
|------|------|----------|------|
| `aiInsights` | Component or Object | Yes | AI Insights configuration block for all supported screens |

### 4.2 Required `aiInsights` Fields

| Path | Required | Notes |
|------|----------|------|
| `aiInsights.enabled` | Yes | Master switch for the entire AI Insights banner |
| `aiInsights.header` | Yes | Header text shown in the banner |
| `aiInsights.mascotImage` | Yes | Mascot or bot image shown in the banner |
| `aiInsights.ctaLabel` | Yes | CTA label used when the screen supports CTA display |
| `aiInsights.screenConfig` | Yes | Per-screen visibility configuration |

### 4.3 Required `aiInsights.screenConfig` Fields

| Path | Required | Notes |
|------|----------|------|
| `aiInsights.screenConfig.dashboard.enabled` | Yes | Controls dashboard banner visibility |
| `aiInsights.screenConfig.buy.enabled` | Yes | Controls buy details page banner visibility |
| `aiInsights.screenConfig.buy-summary.enabled` | Yes | Controls buy summary page banner visibility |
| `aiInsights.screenConfig.sip-details.enabled` | Yes | Controls SIP details page banner visibility |
| `aiInsights.screenConfig.sip-summary.enabled` | Yes | Controls SIP summary page banner visibility |
| `aiInsights.screenConfig.success.enabled` | Yes | Controls buy and SIP thank-you page banner visibility |

---

## 6. Sample Values

### 6.1 `aiInsights`

```json
{
  "aiInsights": {
    "enabled": true,
    "header": "Insight For You",
    "mascotImage": "/uploads/insight_bot.png",
    "ctaLabel": "Ask AI",
    "screenConfig": {
      "dashboard": {
        "enabled": true
      },
      "buy": {
        "enabled": true
      },
      "buy-summary": {
        "enabled": true
      },
      "sip-details": {
        "enabled": true
      },
      "sip-summary": {
        "enabled": true
      },
      "success": {
        "enabled": true
      }
    }
  }
}
```

## 7. Expected API Response

Example responses below show the same `aiInsights` structure for both supported products.

### 7.1 Gold Response

```json
{
  "data": [
    {
      "subProduct": "gold",
      "aiInsights": {
        "enabled": true,
        "header": "Insight For You",
        "mascotImage": {
          "url": "/uploads/insight_bot.png"
        },
        "ctaLabel": "Ask AI",
        "screenConfig": {
          "dashboard": {
            "enabled": true
          },
          "buy": {
            "enabled": true
          },
          "buy-summary": {
            "enabled": true
          },
          "sip-details": {
            "enabled": true
          },
          "sip-summary": {
            "enabled": true
          },
          "success": {
            "enabled": true
          }
        }
      }
    }
  ]
}
```

### 7.2 Silver Response

```json
{
  "data": [
    {
      "subProduct": "silver",
      "aiInsights": {
        "enabled": true,
        "header": "Insight For You",
        "mascotImage": {
          "url": "/uploads/insight_bot.png"
        },
        "ctaLabel": "Ask AI",
        "screenConfig": {
          "dashboard": {
            "enabled": true
          },
          "buy": {
            "enabled": true
          },
          "buy-summary": {
            "enabled": true
          },
          "sip-details": {
            "enabled": true
          },
          "sip-summary": {
            "enabled": true
          },
          "success": {
            "enabled": true
          }
        }
      }
    }
  ]
}
```

## 8. Summary

| Category | Count |
|----------|-------|
| Content types in scope | 1 |
| Supported products | 2 |
| AI Insights root fields | 5 |
| Supported screen keys | 6 |
| Primary API endpoints | 2 |

---

**Owner:** DigiMetal CMS
**Environment:** UAT / QA Strapi
**Reference App:** `abcd-digimetal-web`