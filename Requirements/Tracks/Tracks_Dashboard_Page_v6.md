# Tracks Dashboard Credit Factor Banners - Schema Documentation

## Content-Type: Tracks Dashboard Page (Credit Factor Banners Section)

**Collection Name:** `tracks_dashboard_pages`  
**CMS Path:** `tracks-dashboard-pages.creditFactors`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback


## All Content-Type Fields

### `creditFactors.creditAgeBanner`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `title` | string | No | `"Build your credit age"` |
| `description` | string | No | `"Older credit accounts help improve your credit score"` |
| `ctaLabel` | string | No | `"Learn more"` |
| `ctaUrl` | string | No | `""` |
| `enabled` | boolean | No | `true` |

### `creditFactors.creditEnquiriesBanner`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `title` | string | No | `"Limit credit enquiries"` |
| `description` | string | No | `"Too many enquiries in a short time can lower your score"` |
| `ctaLabel` | string | No | `"Learn more"` |
| `ctaUrl` | string | No | `""` |
| `enabled` | boolean | No | `true` |

---

## Complete JSON Structure

```json
{
  "data": {
    "creditFactors": {
      "creditAgeBanner": {
        "title": "Build your credit age",
        "description": "Older credit accounts help improve your credit score",
        "ctaLabel": "Learn more",
        "ctaUrl": "",
        "enabled": true
      },
      "creditEnquiriesBanner": {
        "title": "Limit credit enquiries",
        "description": "Too many enquiries in a short time can lower your score",
        "ctaLabel": "Learn more",
        "ctaUrl": "",
        "enabled": true
      }
    }
  }
}
```

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

### tracks-dashboard.credit-factor-banner

> Shared component used by `repaymentBanner`, `creditUtilizationBanner`, `creditMixBanner`, `creditAgeBanner`, and `creditEnquiriesBanner`.

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | No | factor-specific fallback |
| `description` | string | No | factor-specific fallback |
| `ctaLabel` | string | No | factor-specific fallback |
| `ctaUrl` | string | No | `""` |
| `enabled` | boolean | No | `true` |
