# Tracks Dashboard Update Consent - New Strapi Requirements (Minimal)

## Content-Type: Tracks Dashboard Page (Update Consent Delta)

**Collection Name:** `tracks_dashboard_pages`  
**CMS Path:** `tracks-dashboard-pages.updateConsent`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback

---

## Scope of This Document

This file captures only the **new/changed** Strapi requirement for Update Consent.

---

## New Requirement

### `updateConsent.consentConfig.representativeTextCollapsedMobile`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `representativeTextCollapsedMobile` | string | No | fallback to `updateConsent.representativeTextCollapsed` |

---

## Backward Compatibility Key

To support existing CMS payload variants, this alias should also be accepted:

| Alias Field | Maps To |
|-------------|---------|
| `representativeTextCollapsed_mobile` | `representativeTextCollapsedMobile` |

---

## Minimal JSON Example

```json
{
  "data": {
    "updateConsent": {
      "consentConfig": {
        "representativeTextCollapsedMobile": " and appoint ABCD as my authorized representativ... "
      }
    }
  }
}
```

## Endpoint Reference

| Method | Endpoint |
|--------|----------|
| GET | `/api/tracks-dashboard-pages` |
| GET | `/api/tracks-dashboard-pages/:id` |
| PUT | `/api/tracks-dashboard-pages/:id` |
