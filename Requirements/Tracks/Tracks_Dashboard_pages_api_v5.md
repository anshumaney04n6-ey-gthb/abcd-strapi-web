# Tracks Dashboard InsightCard - Schema Documentation

## Content-Type: Tracks Dashboard Page (InsightCard Section)

**Collection Name:** `tracks_dashboard_pages`  
**CMS Path:** `tracks-dashboard-pages.insightCard`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback

---

## All Content-Type Fields

### `insightCard`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `bannerActionText` | string | No | `"See what's changed"` |
| `reportActionText` | string | No | `"Get report"` |

---

## Complete JSON Structure

```json
{
  "data": {
    "insightCard": {
      "bannerActionText": "See what's changed",
      "reportActionText": "Get report"
    }
  }
}
```

---

## Fallback Content Mapping

> `fallback.ts` path -> Strapi field name

| Fallback Path | Strapi Field Name |
|---------------|-------------------|
| `insightCard` | `insightCard` |

---

### Field-level Fallback Mapping

> For Tracks insightCard, field names map 1:1 from fallback object to Strapi fields.

#### `insightCard`

| Fallback Field Path | Strapi Field Name |
|---------------------|-------------------|
| `insightCard.bannerActionText` | `insightCard.bannerActionText` |
| `insightCard.reportActionText` | `insightCard.reportActionText` |

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

## Component Detail

### tracks-dashboard.insight-card

> Controls the action text labels displayed in the InsightCard component on the dashboard.

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| `bannerActionText` | string | yes | `"See what's changed"` | Text for comparator/banner action button |
| `reportActionText` | string | yes | `"Get report"` | Text for download report action button |



