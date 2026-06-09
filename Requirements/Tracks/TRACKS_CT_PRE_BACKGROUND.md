# Tracks Pre-Background Screen Strapi Reference

**Date:** 2026-05-04
**Purpose:** Reference document for Strapi configuration of `tracks-dashboard-pages` for the pre-background screen section in `abcd-tracks-web`

---

## 1. Overview

**Content Type:** `tracks-dashboard-pages`

**API Endpoint:**

```http
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*
```

This document is intended for the Strapi team and covers the `preBackgroundScreen` CMS fields that should remain available for the Credit Track pre-dashboard flow.

This content is fetched from the dashboard CMS layer, normalized in the app, and then passed to the `PreCTDashboardPage` UI as the content contract for the pre-background experience.

---

## 2. In Scope

This document covers the following dashboard CMS area:

- `preBackgroundScreen`

These fields are consumed in the dashboard CMS transformation layer and then used in the UI for:

- Two-line pre-dashboard headline content
- Supporting subtitle copy
- Primary and secondary CTA labels
- Trust badge text values
- Background color configuration
- Side illustration asset and alt text
- Loading message shown while the dashboard onboarding flow is in progress

---

## 3. Required Components

### 3.1 `preBackgroundScreen`

Dashboard-level configuration for the pre-background or pre-dashboard experience shown before the main credit dashboard is ready.

```text
preBackgroundScreen
├── headlineLine1 (String)
├── headlineLine2 (String)
├── subtitle (Text)
├── primaryCtaLabel (String)
├── secondaryCtaLabel (String)
├── badge1 (String)
├── badge2 (String)
├── badge3 (String)
├── background (String)
├── sideImage (Media)
├── sideImageAlt (String)
└── loadingLabel (String)
```

Important:

- `preBackgroundScreen` should remain a top-level component under `tracks-dashboard-pages`
- `sideImage` should be configured as a Strapi media field
- `background` should remain a simple string value so the app can pass the configured color directly to the UI
- `loadingLabel` should remain editable from CMS because it is shown during the pre-dashboard loading state

### 3.2 Compatibility Notes

The app currently supports a few fallback aliases while transforming the CMS response. These aliases exist for backward compatibility, but the canonical Strapi schema should still use the `preBackgroundScreen` field names documented above.

| Canonical field | Legacy aliases still accepted by app |
|------|------|
| `preBackgroundScreen` | `preCTDashboard` |
| `subtitle` | `bodyText` |
| `badge1` | `trustBadge1` |
| `badge2` | `trustBadge2` |
| `badge3` | `trustBadge3` |
| `background` | `backgroundColor`, `backgroundColour` |
| `sideImage` | `image`, `sideImageSrc`, `imageSrc`, `media` |
| `loadingLabel` | `loadingMessage` |

Important:

- These aliases should be treated as compatibility inputs only
- New Strapi schema definitions and future CMS entries should use the canonical field names in this document
- The app transforms the Strapi media field into a normalized `sideImageSrc` string before rendering

---

## 4. Fields To Keep In Strapi

### 4.1 Required Top-Level Fields

| Field | Type | Required | Notes |
|------|------|----------|------|
| `subProduct` | String | Yes | Filter key used by the app |
| `partner` | String | Yes | Filter key used by the app |
| `preBackgroundScreen` | Component | Yes | Pre-dashboard content block |

### 4.2 Required `preBackgroundScreen` Fields

| Path | Required | Notes |
|------|----------|------|
| `preBackgroundScreen.headlineLine1` | Yes | First line of the hero-style heading |
| `preBackgroundScreen.headlineLine2` | Yes | Second line of the hero-style heading |
| `preBackgroundScreen.subtitle` | Yes | Supporting copy shown below the heading |
| `preBackgroundScreen.primaryCtaLabel` | Yes | Primary CTA text shown on the page |
| `preBackgroundScreen.secondaryCtaLabel` | Yes | Secondary CTA text shown on the page |
| `preBackgroundScreen.badge1` | Yes | First trust badge text |
| `preBackgroundScreen.badge2` | Yes | Second trust badge text |
| `preBackgroundScreen.badge3` | Yes | Third trust badge text |
| `preBackgroundScreen.background` | Yes | Background color value used by the pre-dashboard section |
| `preBackgroundScreen.sideImage` | Yes | Media illustration shown on the right side of the layout |
| `preBackgroundScreen.sideImageAlt` | Yes | Alt text for the side illustration |
| `preBackgroundScreen.loadingLabel` | Yes | Loading message shown while report data is being fetched |

---

## 5. Sample Values

### 5.1 `preBackgroundScreen`

```json
{
  "preBackgroundScreen": {
    "headlineLine1": "Smart Features.",
    "headlineLine2": "Real Impact.",
    "subtitle": "Track how your score and credit behavior have evolved over time to stay financially aware",
    "primaryCtaLabel": "Find out now >",
    "secondaryCtaLabel": "Get your free score >",
    "badge1": "835 Predicted score",
    "badge2": "+35pts Secure",
    "badge3": "+98% Accurate",
    "background": "#FFF4CE",
    "sideImage": "/uploads/predashboard_side_image.png",
    "sideImageAlt": "Pre-dashboard credit score illustration",
    "loadingLabel": "Fetching your credit report..."
  }
}
```

---


Important:

- The documented response above uses the same `tracks-dashboard-pages` API endpoint as the dashboard reference
- `preBackgroundScreen` is expected as a nested top-level component in the response
- `sideImage` should remain a media object in the API response so the app can resolve the asset URL during normalization

---

## 7. Summary

| Category | Count |
|----------|-------|
| Core components in scope | 1 |
| Required `preBackgroundScreen` direct fields | 12 |
| Primary API endpoint | 1 |

---

**Owner:** Tracks Dashboard CMS
**Environment:** UAT / QA Strapi
**Reference App:** `abcd-tracks-web`