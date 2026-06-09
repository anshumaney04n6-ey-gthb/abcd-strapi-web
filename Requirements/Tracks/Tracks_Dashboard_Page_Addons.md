# Tracks Dashboard Pay Bills - Add-On Fields

## Content-Type: Tracks Dashboard Page (Pay Bills Section)

**Collection Name:** `tracks_dashboard_pages`  
**CMS Path:** `tracks-dashboard-pages.payBills`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback

---

## Add-On Fields for `payBills`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `payBillCtaLabel` | string | No | `"Pay Bills"` |
| `bbpsUrl` | string | No | `""` |

---

## Complete JSON Structure

```json
{
  "data": {
    "payBills": {
      "payBillCtaLabel": "Pay Bills",
      "bbpsUrl": "https://bbps-url.example.com"
    }
  }
}
```

---

## Field-level Mapping

| Field Path | Strapi Field Name |
|------------|-------------------|
| `payBills.payBillCtaLabel` | `payBills.payBillCtaLabel` |
| `payBills.bbpsUrl` | `payBills.bbpsUrl` |

---

## CMS API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tracks-dashboard-pages` | List all tracks dashboard page entries |
| GET | `/api/tracks-dashboard-pages/:id` | Get single tracks dashboard page entry |
| POST | `/api/tracks-dashboard-pages` | Create tracks dashboard page entry |
| PUT | `/api/tracks-dashboard-pages/:id` | Update tracks dashboard page entry |
| DELETE | `/api/tracks-dashboard-pages/:id` | Delete tracks dashboard page entry |
