# Tracks AI Insights Strapi Reference

**Date:** 2026-05-18
**Purpose:** Reference document for Strapi configuration of `tracks-dashboard-pages` for the AI Insights section in `abcd-tracks-web`

---

## 1. Overview

**Content Type:** `tracks-dashboard-pages`

**API Endpoint:**

```http
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*
```

This document is intended for the Strapi team and covers the `aiInsights` CMS fields that should remain available for the Credit dashboard flow.

---

## 2. In Scope

This document covers the following dashboard CMS area:

- `aiInsights`

These fields are consumed in the dashboard CMS transformation layer and then used in the UI for:

- AI Insights banner visibility
- AI Insights banner header copy
- AI Insights CTA label
- AI Insights mascot image
- Dashboard screen-level enablement

---

## 3. Required Components

### 3.1 `aiInsights`

Dashboard-level configuration for the AI Insights banner.

```text
aiInsights
├── enabled (Boolean)
├── header (String)
├── mascotImage (Media)
├── ctaLabel (String)
└── screenConfig (Component: ai-insights-screen-config)
```

### 3.2 `ai-insights-screen-config`

Nested component used for screen-level enablement of AI Insights.

```text
ai-insights-screen-config
└── dashboard (Boolean)
```

Important:

- `aiInsights` should remain a top-level component under `tracks-dashboard-pages`
- `mascotImage` should be configured as a Strapi media field
- `screenConfig` should remain a nested component under `aiInsights`
- `screenConfig.dashboard` controls whether the AI Insights banner is rendered on the dashboard
- The app currently tolerates `screenConfig.dashboard` as either a Boolean or an object shape during transformation, but the preferred Strapi shape for Tracks is a direct Boolean field

---

## 4. Fields To Keep In Strapi

### 4.1 Required Top-Level Fields

| Field | Type | Required | Notes |
|------|------|----------|------|
| `subProduct` | String | Yes | Filter key used by the app |
| `partner` | String | Yes | Filter key used by the app |
| `aiInsights` | Component | Yes | AI Insights content block |

### 4.2 Required `aiInsights` Fields

| Path | Required | Notes |
|------|----------|------|
| `aiInsights.enabled` | Yes | Master toggle for the AI Insights banner |
| `aiInsights.header` | Yes | Header text shown in the banner |
| `aiInsights.mascotImage` | Yes | Mascot illustration shown in the banner |
| `aiInsights.ctaLabel` | Yes | CTA label used for the Ask AI action |
| `aiInsights.screenConfig` | Yes | Screen-level visibility configuration |

### 4.3 Required `aiInsights.screenConfig` Fields

| Path | Required | Notes |
|------|----------|------|
| `aiInsights.screenConfig.dashboard` | Yes | Controls AI Insights visibility on dashboard screen |

---

## 5. Transformation Notes

The dashboard CMS transformation layer resolves `aiInsights` with fallback support.

Key behavior:

- If `aiInsights.enabled` is missing, fallback value is used
- If `aiInsights.header` is missing, fallback value is used
- If `aiInsights.ctaLabel` is missing, fallback value is used
- If `aiInsights.mascotImage` is missing or invalid, the internal fallback asset is used
- If `aiInsights.screenConfig.dashboard` is missing, fallback value is used

Current fallback values in the app:

```json
{
  "enabled": true,
  "header": "Insight for you",
  "mascotImage": "/tracks/assets/ai-insights/insight-bot.png",
  "ctaLabel": "Ask AI",
  "screenConfig": {
    "dashboard": true
  }
}
```

---

## 6. UI Behavior

The dashboard banner is shown only when both of the following are true:

- `aiInsights.enabled === true`
- `aiInsights.screenConfig.dashboard === true`

If either flag is false, the AI Insights banner is hidden.

---

## 7. Sample Values

### 7.1 `aiInsights`

```json
{
  "aiInsights": {
    "enabled": true,
    "header": "Insight for you",
    "mascotImage": "/uploads/insight_bot.png",
    "ctaLabel": "Ask AI",
    "screenConfig": {
      "dashboard": true
    }
  }
}
```

---

## 8. Expected API Response

```json
{
  "data": [
    {
      "aiInsights": {
        "enabled": true,
        "header": "Insight for you",
        "mascotImage": {
          "url": "/uploads/insight_bot.png"
        },
        "ctaLabel": "Ask AI",
        "screenConfig": {
          "dashboard": true
        }
      }
    }
  ]
}
```
---

## 10. Summary

| Category | Count |
|----------|-------|
| Required `aiInsights` direct fields | 5 |
| Required `screenConfig` direct fields | 1 |
| Primary API endpoint | 1 |

---

**Owner:** Tracks Dashboard CMS
**Environment:** UAT / QA Strapi
**Reference App:** `abcd-tracks-web`