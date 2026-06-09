# Tracks Dashboard Sidebars - Schema Documentation

## Content-Type: Tracks Dashboard Page (Sidebar Sections)

**Collection Name:** `tracks_dashboard_pages`  
**CMS Path:** `tracks-dashboard-pages.downloadReport`, `tracks-dashboard-pages.refreshOnApp`, `tracks-dashboard-pages.payBills`  
**Merge Strategy:** `deepMergeWithFallback` — per-field override, missing fields use fallback

---

## All Content-Type Fields

### 1. `downloadReport`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `sidebarHeader.title` | string | No | `"Get report"` |
| `sidebarHeader.backButtonVariant` | enum | No | `"pill"` |
| `sidebarHeader.backButtonColor` | string | No | `"#050000"` |
| `sidebarHeader.titleColor` | string | No | `"#ffffff"` |
| `sidebarHeader.background.variant` | enum | No | `"red"` |
| `sidebarHeader.background.showPattern` | boolean | No | `false` |
| `title` | string | No | `"GET YOUR CREDIT REPORT"` |
| `subtitle` | string | No | `"Enter the Email ID on which you want to receive your credit score report"` |
| `emailLabel` | string | No | `"Email ID"` |
| `emailPlaceholder` | string | No | `"Enter Email ID"` |
| `primaryButtonText` | string | No | `"Download report"` |
| `secondaryButtonText` | string | No | `"Send to email"` |
| `successIcon` | media/string | No | `/icons/done.svg` |
| `successTitle` | string | No | `"Report downloaded successfully"` |
| `successEmailTitle` | string | No | `"Report sent to email ID successfully"` |
| `successInfoMessage` | string | No | `"Not sure how to read your report?\nLearn more here"` |
| `successInfoIcon` | media/string | No | `/icons/lightbulb-variant.svg` |
| `successInfoIconColor` | string | No | `"#F7A500"` |
| `successBackButtonText` | string | No | `"Back to dashboard"` |
| `toastDownloadSuccess` | string | No | `"Report downloaded successfully"` |
| `toastDownloadError` | string | No | `"Failed to download report. Please try again."` |
| `toastEmailSuccess` | string | No | `"Report sent to your email successfully"` |
| `toastEmailError` | string | No | `"Failed to send report to email. Please try again."` |
| `toastEmailRequired` | string | No | `"Email address is required"` |

---

### 2. `refreshOnApp`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `sidebarHeader.title` | string | No | `"Credit Score"` |
| `sidebarHeader.backButtonVariant` | enum | No | `"pill"` |
| `sidebarHeader.backButtonColor` | string | No | `"#050000"` |
| `sidebarHeader.titleColor` | string | No | `"#ffffff"` |
| `sidebarHeader.background.variant` | enum | No | `"red"` |
| `sidebarHeader.background.showPattern` | boolean | No | `false` |
| `sidebarHeader.showHelpIcon` | boolean | No | `true` |
| `title` | string | No | `"Download the ABCD app to refresh your credit score"` |
| `subtitle` | string | No | `"Keep a monthly check on your credit report using our mobile app"` |
| `illustrationSrc` | media/string | No | `/icons/Refresh-your-credit-score.svg` |
| `illustrationAlt` | string | No | `"Refresh Credit Score"` |
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

### 3. `payBills`

| Field Name | Type | Required | Default |
|------------|------|----------|---------|
| `sidebarHeader.title` | string | No | `"Pay Bills"` |
| `sidebarHeader.backButtonVariant` | enum | No | `"pill"` |
| `sidebarHeader.backButtonColor` | string | No | `"#050000"` |
| `sidebarHeader.titleColor` | string | No | `"#ffffff"` |
| `sidebarHeader.background.variant` | enum | No | `"red"` |
| `sidebarHeader.background.showPattern` | boolean | No | `false` |
| `sidebarHeader.showHelpIcon` | boolean | No | `true` |
| `title` | string | No | `"PAY YOUR BILLS AND EMI ON THE ABCD APP"` |
| `subtitle` | string | No | `"Download our mobile app to easily pay off your bills and EMIs"` |
| `illustrationSrc` | media/string | No | `/icons/calendar-blue.png` |
| `illustrationAlt` | string | No | `"Pay Bills"` |
| `abcdLogoSrc` | media/string | No | `/logos/lob/abcd.svg` |
| `appDownloadText` | string | No | `"Download the app now"` |
| `ctaButtons` | component[] | No | Same as `refreshOnApp` |
| `actionButtonText` | string | No | `"Got it"` |

---

## Complete JSON Structure

```json
{
  "data": {
    "downloadReport": {
      "sidebarHeader": {
        "title": "Get report",
        "backButtonVariant": "pill",
        "backButtonColor": "#050000",
        "titleColor": "#ffffff",
        "background": { "variant": "red", "showPattern": false }
      },
      "title": "GET YOUR CREDIT REPORT",
      "subtitle": "Enter the Email ID on which you want to receive your credit score report",
      "emailLabel": "Email ID",
      "emailPlaceholder": "Enter Email ID",
      "primaryButtonText": "Download report",
      "secondaryButtonText": "Send to email",
      "successIcon": "media_or_url",
      "successTitle": "Report downloaded successfully",
      "successEmailTitle": "Report sent to email ID successfully",
      "successInfoMessage": "Not sure how to read your report?\nLearn more here",
      "successInfoIcon": "media_or_url",
      "successInfoIconColor": "#F7A500",
      "successBackButtonText": "Back to dashboard",
      "toastDownloadSuccess": "Report downloaded successfully",
      "toastDownloadError": "Failed to download report. Please try again.",
      "toastEmailSuccess": "Report sent to your email successfully",
      "toastEmailError": "Failed to send report to email. Please try again.",
      "toastEmailRequired": "Email address is required"
    },

    "refreshOnApp": {
      "sidebarHeader": {
        "title": "Credit Score",
        "backButtonVariant": "pill",
        "backButtonColor": "#050000",
        "titleColor": "#ffffff",
        "background": { "variant": "red", "showPattern": false },
        "showHelpIcon": true
      },
      "title": "Download the ABCD app to refresh your credit score",
      "subtitle": "Keep a monthly check on your credit report using our mobile app",
      "illustrationSrc": "media_or_url",
      "illustrationAlt": "Refresh Credit Score",
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
    },

    "payBills": {
      "sidebarHeader": {
        "title": "Pay Bills",
        "backButtonVariant": "pill",
        "backButtonColor": "#050000",
        "titleColor": "#ffffff",
        "background": { "variant": "red", "showPattern": false },
        "showHelpIcon": true
      },
      "title": "PAY YOUR BILLS AND EMI ON THE ABCD APP",
      "subtitle": "Download our mobile app to easily pay off your bills and EMIs",
      "illustrationSrc": "media_or_url",
      "illustrationAlt": "Pay Bills",
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

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tracks-dashboard-pages` | Get all dashboard pages |
| GET | `/api/tracks-dashboard-pages/:id` | Get dashboard page by ID |
| POST | `/api/tracks-dashboard-pages` | Create new dashboard page |
| PUT | `/api/tracks-dashboard-pages/:id` | Update dashboard page |
| DELETE | `/api/tracks-dashboard-pages/:id` | Delete dashboard page |

---

## Components Detail

### 1. tracks-dashboard.sidebar-header

> Shared sidebar header used by `downloadReport`, `refreshOnApp`, and `payBills`.

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | No | - |
| `backButtonVariant` | enum (`chevron` \| `close` \| `arrow` \| `pill`) | No | `"pill"` |
| `backButtonColor` | string | No | `"#050000"` |
| `titleColor` | string | No | `"#ffffff"` |
| `background.variant` | enum (`gold` \| `red` \| `white` \| `custom`) | No | `"red"` |
| `background.showPattern` | boolean | No | `false` |
| `showHelpIcon` | boolean | No | `false` |

> `showHelpIcon` is only used by `refreshOnApp` and `payBills`.

---

### 2. tracks-dashboard.download-report

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `sidebarHeader` | component | No | fallback |
| `title` | string | No | `"GET YOUR CREDIT REPORT"` |
| `subtitle` | string | No | `"Enter the Email ID on which you want to receive your credit score report"` |
| `emailLabel` | string | No | `"Email ID"` |
| `emailPlaceholder` | string | No | `"Enter Email ID"` |
| `primaryButtonText` | string | No | `"Download report"` |
| `secondaryButtonText` | string | No | `"Send to email"` |
| `successIcon` | media/string | No | `/icons/done.svg` |
| `successTitle` | string | No | `"Report downloaded successfully"` |
| `successEmailTitle` | string | No | `"Report sent to email ID successfully"` |
| `successInfoMessage` | string | No | `"Not sure how to read your report?\nLearn more here"` |
| `successInfoIcon` | media/string | No | `/icons/lightbulb-variant.svg` |
| `successInfoIconColor` | string | No | `"#F7A500"` |
| `successBackButtonText` | string | No | `"Back to dashboard"` |
| `toastDownloadSuccess` | string | No | `"Report downloaded successfully"` |
| `toastDownloadError` | string | No | `"Failed to download report. Please try again."` |
| `toastEmailSuccess` | string | No | `"Report sent to your email successfully"` |
| `toastEmailError` | string | No | `"Failed to send report to email. Please try again."` |
| `toastEmailRequired` | string | No | `"Email address is required"` |

---

### 3. tracks-dashboard.refresh-on-app

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `sidebarHeader` | component | No | fallback |
| `title` | string | No | `"Download the ABCD app to refresh your credit score"` |
| `subtitle` | string | No | `"Keep a monthly check on your credit report using our mobile app"` |
| `illustrationSrc` | media/string | No | `/icons/Refresh-your-credit-score.svg` |
| `illustrationAlt` | string | No | `"Refresh Credit Score"` |
| `abcdLogoSrc` | media/string | No | `/logos/lob/abcd.svg` |
| `appDownloadText` | string | No | `"Download the app now"` |
| `ctaButtons` | component[] | No | fallback |
| `actionButtonText` | string | No | `"Got it"` |

---

### 4. tracks-dashboard.pay-bills

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `sidebarHeader` | component | No | fallback |
| `title` | string | No | `"PAY YOUR BILLS AND EMI ON THE ABCD APP"` |
| `subtitle` | string | No | `"Download our mobile app to easily pay off your bills and EMIs"` |
| `illustrationSrc` | media/string | No | `/icons/calendar-blue.png` |
| `illustrationAlt` | string | No | `"Pay Bills"` |
| `abcdLogoSrc` | media/string | No | `/logos/lob/abcd.svg` |
| `appDownloadText` | string | No | `"Download the app now"` |
| `ctaButtons` | component[] | No | fallback |
| `actionButtonText` | string | No | `"Got it"` |

---

### 5. tracks-dashboard.cta-button-item

> Used in `refreshOnApp.ctaButtons` and `payBills.ctaButtons`.

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `label` | string | Yes | - |
| `link` | string | Yes | - |
| `iconSrc` | media/string | No | - |
| `iconAlt` | string | No | - |

---
