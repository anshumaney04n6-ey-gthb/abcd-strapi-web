# PL Dashboard CMS — New Field

## Content-Type: personal-loan-dashboard-pages

**Collection Name:** `personal-loan-dashboard-pages`
**Singular Name:** `personal-loan-dashboard-pages`
**Plural Name:** `personal-loan-dashboard-pages`
**Draft & Publish:** Enabled

**Component:** `dashboard.highlighter-conadd complete example jatent` (nested under `hero.highlighterContent`)

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/personal-loan-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/personal-loan-dashboard-pages` | List all dashboards |
| GET | `/api/personal-loan-dashboard-pages/:id` | Get single dashboard by ID |
| POST | `/api/personal-loan-dashboard-pages` | Create new dashboard |
| PUT | `/api/personal-loan-dashboard-pages/:id` | Update dashboard content |
| DELETE | `/api/personal-loan-dashboard-pages/:id` | Delete dashboard |

late=*
```

---

## New Field

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `pqOffer` | component | Yes | see below |

Add this single key (component) to the `dashboard.highlighter-content` component, alongside the existing `newJourney`, `resumeJourney`, `preApprovedOffer`, `exclusiveOffer`, etc. variants. No other changes.

### `pqOffer` sub-fields

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | `"Congratulations!"` |
| `subtitleTemplate` | string | Yes | `"is Pre-approved, just for you by {lenderName}"` |
| `ctaText` | string | Yes | `"Apply Now"` |
| `autoRotateMs` | integer | Yes | `60000` |

**Notes**
- `subtitleTemplate` supports a `{lenderName}` token. The app substitutes the active offer's lender name at render time.
- `title` is suffixed with the user's first name at render time (e.g. `"Congratulations! Rahul"`); CMS should provide only the base copy.
- `autoRotateMs` controls how long each PQ offer is shown in the carousel before the next one auto-advances.

---

## API Response Example

```json
{
  "hero": {
    "ctaText": "Apply Now",
    "eligibilityCriteria": [
      { "label": "Age:", "value": "21 to 65 years" },
      { "label": "Income:", "value": "Min. ₹30,000/m" },
      { "label": "Residency:", "value": "PAN India" }
    ],
    "highlighterContent": {
      "newJourney": {
        "title": "Get instant loans up to ₹ 15 Lakhs",
        "subtitle": "Instant Disbursal, ZERO Documentation, Flexible EMIs",
        "ctaText": "Apply now",
        "illustrationSrc": "/assets/personal-loan/icons/handcoins.webp"
      },
      "resumeJourney": {
        "title": "Welcome back, pick up where you left",
        "subtitle": "Resume your application in minutes and get faster disbursal",
        "ctaText": "Resume",
        "illustrationSrc": "/assets/personal-loan/icons/resume-app.webp"
      },
      "preApprovedOffer": {
        "title": "You have a ",
        "subtitle": "Check out your",
        "ctaText": "Apply",
        "illustrationSrc": "/assets/personal-loan/icons/handcoins.webp"
      },
      "exclusiveOffer": {
        "title": "Staff exclusive personal loan offer",
        "subtitle": "Check out your staff offer -",
        "ctaText": "Apply Now",
        "illustrationSrc": "/assets/personal-loan/icons/exclusive.webp",
        "redirectUrl": "https://google.com"
      },
      "progress": {
        "title": "Your disbursement is in progress",
        "subtitle": "We are processing your loan disbursement. This usually completes shortly.",
        "ctaText": "Check Status",
        "illustrationSrc": "/assets/personal-loan/icons/progress-app.webp"
      },
      "success": {
        "title": "Loan disbursed successfully",
        "subtitle": "Your loan amount has been credited to your account.",
        "ctaText": "Download Documents",
        "illustrationSrc": "/assets/personal-loan/icons/disb-success.webp"
      },
      "failed": {
        "title": "Disbursement failed",
        "subtitle": "We could not complete disbursement this time. Please retry or check details.",
        "ctaText": "Check Status",
        "illustrationSrc": "/assets/personal-loan/icons/disb-failed.webp"
      },
      "rejected": {
        "title": "Application rejected",
        "subtitle": "Your application could not be approved based on current checks.",
        "ctaText": "Check Status",
        "illustrationSrc": "/assets/personal-loan/icons/disb-failed.webp"
      },
      "pqOffer": {
        "title": "Congratulations!",
        "subtitleTemplate": "is Pre-approved, just for you by {lenderName}",
        "ctaText": "Apply Now",
        "autoRotateMs": 60000
      }
    }
  }
}
```
