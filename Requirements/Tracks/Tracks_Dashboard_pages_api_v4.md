# Tracks Dashboard Score Ranges - Schema Documentation

## Content-Type: Tracks Dashboard Page (Score Ranges Section)

**Collection Name:** `tracks_dashboard_pages`  
**CMS Path:** `tracks-dashboard-pages.scoreRanges`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback

---

## All Content-Type Fields

### `scoreRanges`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `sidebarTitle` | string | No | `"Credit Score Ranges"` |
| `sectionTitle` | string | No | `"RANGES OF THE SCORE"` |
| `actionButtonText` | string | No | `"Got it"` |
| `ranges` | component[] | No | See below |

#### ranges item

| Field Name | Type | Required | Default | Options |
|------------|------|----------|---------|---------|
| `id` | string | Yes | - | - |
| `level` | enum | Yes | - | `excellent`, `good`, `fair`, `needsWork` |
| `label` | string | Yes | - | - |
| `rangeStart` | number | Yes | - | - |
| `rangeEnd` | number | Yes | - | - |
| `color` | string | Yes | - | Hex color code |

---

## Complete JSON Structure

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
          "level": "good",
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

## Fallback Content Mapping

> `fallback.ts` path -> Strapi field name

| Fallback Path | Strapi Field Name |
|---------------|-------------------|
| `scoreRanges` | `scoreRanges` |

---

### Field-level Fallback Mapping

> For Tracks scoreRanges, field names map 1:1 from fallback object to Strapi fields.

#### `scoreRanges`

| Fallback Field Path | Strapi Field Name |
|---------------------|-------------------|
| `scoreRanges.sidebarTitle` | `scoreRanges.sidebarTitle` |
| `scoreRanges.sectionTitle` | `scoreRanges.sectionTitle` |
| `scoreRanges.actionButtonText` | `scoreRanges.actionButtonText` |
| `scoreRanges.ranges[]` | `scoreRanges.ranges[]` |
| `scoreRanges.ranges[].id` | `scoreRanges.ranges[].id` (also accepts `rangeId`) |
| `scoreRanges.ranges[].level` | `scoreRanges.ranges[].level` |
| `scoreRanges.ranges[].label` | `scoreRanges.ranges[].label` |
| `scoreRanges.ranges[].rangeStart` | `scoreRanges.ranges[].rangeStart` |
| `scoreRanges.ranges[].rangeEnd` | `scoreRanges.ranges[].rangeEnd` |
| `scoreRanges.ranges[].color` | `scoreRanges.ranges[].color` |

---

## Standard Credit Score Ranges

Based on industry standards:

| Score Range | Category Label | Color | Level |
|-------------|---------------|-------|-------|
| 750–900 | Excellent | Green (#0A6A34) | excellent |
| 700–749 | Very Good | Light Green (#7CB342) | good |
| 650–699 | Good | Yellow-Green (#9ACD32) | good |
| 550–649 | Fair / Okay | Orange (#F57C00) | fair |
| 300–549 | Needs Work | Red (#D32F2F) | needsWork |

---

## CMS API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tracks-dashboard-pages` | List all tracks dashboard page entries |
| GET | `/api/tracks-dashboard-pages/:id` | Get single tracks dashboard page entry |
| POST | `/api/tracks-dashboard-pages` | Create tracks dashboard page entry |
| PUT | `/api/tracks-dashboard-pages/:id` | Update tracks dashboard page entry |
| DELETE | `/api/tracks-dashboard-pages/:id` | Delete tracks dashboard page entry |

---

## Components Detail

### 1. tracks-dashboard.score-ranges

> Configuration for the score ranges sidebar and its content.

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| `sidebarTitle` | string | No | `"Credit Score Ranges"` | Title shown in sidebar header |
| `sectionTitle` | string | No | `"RANGES OF THE SCORE"` | Section title inside sidebar |
| `actionButtonText` | string | No | `"Got it"` | Text for action button |
| `ranges` | component[] | No | fallback | Array of score range items |

---

### 2. tracks-dashboard.score-range-item

> Individual score range configuration.

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| `id` | string | Yes | - | Unique identifier (also accepts `rangeId`) |
| `level` | enum | Yes | - | Score level: `excellent`, `good`, `fair`, `needsWork` |
| `label` | string | Yes | - | Display label (e.g., "Excellent", "Very Good") |
| `rangeStart` | number | Yes | - | Starting score of range (inclusive) |
| `rangeEnd` | number | Yes | - | Ending score of range (inclusive) |
| `color` | string | Yes | - | Hex color code for range display |

---


### Custom Score Ranges
```json
{
  "scoreRanges": {
    "sidebarTitle": "Know Your Score",
    "sectionTitle": "SCORE CATEGORIES",
    "actionButtonText": "Close",
    "ranges": [
      {
        "id": "excellent",
        "level": "excellent",
        "label": "Excellent 🎉",
        "rangeStart": 750,
        "rangeEnd": 900,
        "color": "#0A6A34"
      }
    ]
  }
}
```


## Color Reference

Recommended color codes for score ranges:

| Color Name | Hex Code | Usage |
|------------|----------|-------|
| Dark Green | `#0A6A34` | Excellent scores (750-900) |
| Light Green | `#7CB342` | Very Good scores (700-749) |
| Yellow-Green | `#9ACD32` | Good scores (650-699) |
| Orange | `#F57C00` | Fair scores (550-649) |
| Red | `#D32F2F` | Needs Work (300-549) |

---



