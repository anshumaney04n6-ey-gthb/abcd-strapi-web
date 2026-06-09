# Tracks Dashboard Comparator - Schema Documentation

## Content-Type: Tracks Dashboard Page (Comparator Section)

**Collection Name:** `tracks_dashboard_pages`  
**CMS Path:** `tracks-dashboard-pages.comparatorOnApp`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback

---

## All Content-Type Fields

### `comparatorOnApp`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `sidebarHeader.title` | string | No | `"Comparator"` |
| `sidebarHeader.backButtonVariant` | enum | No | `"pill"` |
| `sidebarHeader.backButtonColor` | string | No | `"#050000"` |
| `sidebarHeader.titleColor` | string | No | `"#050000"` |
| `sidebarHeader.background.variant` | enum | No | `"white"` |
| `sidebarHeader.background.showPattern` | boolean | No | `false` |
| `sidebarHeader.showHelpIcon` | boolean | No | `true` |
| `MainTitle` | string | No | `"Factors that impact your credit score"` |
| `title` | string | No | `"VIEW CREDIT SCORE CHANGES ON THE ABCD APP"` |
| `subtitle` | string | No | `"Download our mobile app to see how each factor has impacted your credit score"` |
| `abcdLogoSrc` | media/string | No | `/logos/lob/abcd.svg` |
| `appDownloadText` | string | No | `"Download the app now"` |
| `ctaButtons` | component[] | No | See below |
| `actionButtonText` | string | No | `"Got it"` |

#### ctaButtons item

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `label` | string | Yes | - |
| `link` | string | Yes | - |
| `iconSrc` | media/string | No | - |
| `iconAlt` | string | No | - |

---

## Complete JSON Structure

```json
{
  "data": {
    "comparatorOnApp": {
      "sidebarHeader": {
        "title": "Comparator",
        "backButtonVariant": "pill",
        "backButtonColor": "#050000",
        "titleColor": "#050000",
        "background": { "variant": "white", "showPattern": false },
        "showHelpIcon": true
      },
      "MainTitle": "Factors that impact your credit score",
      "title": "VIEW CREDIT SCORE CHANGES ON THE ABCD APP",
      "subtitle": "Download our mobile app to see how each factor has impacted your credit score",
      "abcdLogoSrc": "media_or_url",
      "appDownloadText": "Download the app now",
      "ctaButtons": [
        {
          "label": "App Store",
          "link": "https://apps.apple.com/",
          "iconSrc": "media_or_url",
          "iconAlt": "Apple App Store"
        },
        {
          "label": "Google Play",
          "link": "https://play.google.com/store",
          "iconSrc": "media_or_url",
          "iconAlt": "Google Play Store"
        }
      ],
      "actionButtonText": "Got it"
    }
  }
}
```
---

## Fallback Content Mapping

> `fallback.ts` path -> Strapi field name

| Fallback Path | Strapi Field Name |
|---------------|-------------------|
| `comparatorOnApp` | `comparatorOnApp` |

---

### Field-level Fallback Mapping

> For Tracks comparator, field names map 1:1 from fallback object to Strapi fields inside each section.

#### `comparatorOnApp`

| Fallback Field Path | Strapi Field Name |
|---------------------|-------------------|
| `comparatorOnApp.sidebarHeader.title` | `comparatorOnApp.sidebarHeader.title` |
| `comparatorOnApp.sidebarHeader.backButtonVariant` | `comparatorOnApp.sidebarHeader.backButtonVariant` |
| `comparatorOnApp.sidebarHeader.backButtonColor` | `comparatorOnApp.sidebarHeader.backButtonColor` |
| `comparatorOnApp.sidebarHeader.titleColor` | `comparatorOnApp.sidebarHeader.titleColor` |
| `comparatorOnApp.sidebarHeader.background.variant` | `comparatorOnApp.sidebarHeader.background.variant` |
| `comparatorOnApp.sidebarHeader.background.showPattern` | `comparatorOnApp.sidebarHeader.background.showPattern` |
| `comparatorOnApp.sidebarHeader.showHelpIcon` | `comparatorOnApp.sidebarHeader.showHelpIcon` |
| `comparatorOnApp.MainTitle` | `comparatorOnApp.MainTitle` (also accepts `mainTitle`) |
| `comparatorOnApp.title` | `comparatorOnApp.title` |
| `comparatorOnApp.subtitle` | `comparatorOnApp.subtitle` |
| `comparatorOnApp.abcdLogoSrc` | `comparatorOnApp.abcdLogoSrc` (also accepts `abcdLogoPath`) |
| `comparatorOnApp.appDownloadText` | `comparatorOnApp.appDownloadText` |
| `comparatorOnApp.ctaButtons[]` | `comparatorOnApp.ctaButtons[]` |
| `comparatorOnApp.actionButtonText` | `comparatorOnApp.actionButtonText` |

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

---

## Components Detail

### 1. tracks-dashboard.sidebar-header (Comparator variant)

> Sidebar header used by `comparatorOnApp`. Uses `white` background by default (unlike `downloadReport`/`refreshOnApp`/`payBills` which use `red`).

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | No | `"Comparator"` |
| `backButtonVariant` | enum (`chevron` \| `close` \| `arrow` \| `pill`) | No | `"pill"` |
| `backButtonColor` | string | No | `"#050000"` |
| `titleColor` | string | No | `"#050000"` |
| `background.variant` | enum (`gold` \| `red` \| `white` \| `custom`) | No | `"white"` |
| `background.showPattern` | boolean | No | `false` |
| `showHelpIcon` | boolean | No | `true` |

---

### 2. tracks-dashboard.comparator-on-app

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `sidebarHeader` | component | No | fallback |
| `MainTitle` | string | No | `"Factors that impact your credit score"` |
| `title` | string | No | `"VIEW CREDIT SCORE CHANGES ON THE ABCD APP"` |
| `subtitle` | string | No | `"Download our mobile app to see how each factor has impacted your credit score"` |
| `abcdLogoSrc` | media/string | No | `/logos/lob/abcd.svg` |
| `appDownloadText` | string | No | `"Download the app now"` |
| `ctaButtons` | component[] | No | fallback |
| `actionButtonText` | string | No | `"Got it"` |

---

### 3. tracks-dashboard.cta-button-item

> Used in `comparatorOnApp.ctaButtons`.

| Field | Type | Required | Default |
|------------|------|----------|---------|
| `label` | string | Yes | - |
| `link` | string | Yes | - |
| `iconSrc` | media/string | No | - |
| `iconAlt` | string | No | - |


