# Tracks Dashboard - New Strapi Requirements (Minimal)

## Content-Type: Tracks Dashboard Page

**Collection Name:** `tracks_dashboard_pages`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback

---

## Scope of This Document

This file captures only the **new/changed** Strapi requirements for Tracks Dashboard.

---

## 1. Score Ranges - 5 Levels Support

### `scoreRanges`

**CMS Path:** `tracks-dashboard-pages.scoreRanges`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `sidebarTitle` | string | No | `"Credit Score Ranges"` |
| `sectionTitle` | string | No | `"RANGES OF THE SCORE"` |
| `actionButtonText` | string | No | `"Got it"` |
| `ranges` | array | No | See below |

### `scoreRanges.ranges[]` - Array Item

| Field Name | Type | Required | Default | Valid Values |
|------------|------|----------|---------|--------------|
| `id` | string | Yes | - | Unique identifier |
| `level` | enum | Yes | - | `'excellent'`, `'veryGood'`, `'good'`, `'fair'`, `'needsWork'` |
| `label` | string | Yes | - | Display label |
| `rangeStart` | number | Yes | - | Starting score (e.g., 750) |
| `rangeEnd` | number | Yes | - | Ending score (e.g., 900) |
| `color` | string | Yes | - | Hex color code (e.g., `#0A6A34`) |

### Required: 5 Distinct Ranges

The system **must** support exactly **5 score range levels**:

1. **Excellent** → `level: 'excellent'`
2. **Very Good** → `level: 'veryGood'` ⭐ **(Distinct from "Good")**
3. **Good** → `level: 'good'`
4. **Fair / Okay** → `level: 'fair'`
5. **Needs Work** → `level: 'needsWork'`

### JSON Example

```json
{
  "data": {
    "scoreRanges": {
      "sidebarTitle": "Credit Score Ranges",
      "sectionTitle": "RANGES OF THE SCORE",
      "actionButtonText": "Got it",
      "ranges": [
        {
          "id": "excellent",
          "level": "excellent",
          "label": "Excellent",
          "rangeStart": 750,
          "rangeEnd": 900,
          "color": "#0A6A34"
        },
        {
          "id": "very-good",
          "level": "veryGood",
          "label": "Very Good",
          "rangeStart": 700,
          "rangeEnd": 749,
          "color": "#7CB342"
        },
        {
          "id": "good",
          "level": "good",
          "label": "Good",
          "rangeStart": 650,
          "rangeEnd": 699,
          "color": "#9ACD32"
        },
        {
          "id": "fair",
          "level": "fair",
          "label": "Fair / Okay",
          "rangeStart": 550,
          "rangeEnd": 649,
          "color": "#F57C00"
        },
        {
          "id": "needs-work",
          "level": "needsWork",
          "label": "Needs Work",
          "rangeStart": 300,
          "rangeEnd": 549,
          "color": "#D32F2F"
        }
      ]
    }
  }
}
```

---
-

## Populate Query

```
/api/tracks-dashboard-pages?
filters[subProduct][$eq]=credit&
filters[partner][$eq]=default&
populate=*
```

---
