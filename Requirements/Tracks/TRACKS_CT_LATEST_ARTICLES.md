# Tracks Latest Articles Strapi Reference

**Date:** 2026-06-11
**Purpose:** Small Strapi requirement note for new Latest Articles fields in `abcd-tracks-web`

---

## API

```http
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*
```

---

## Fields In Scope

Only these new `latestArticles` fields are in scope:
keep already added field as it is.

- `latestArticles.linkText` (String)
- `latestArticles.ctaText` (String)
- `latestArticles.articles[].ctaText` (String)
- `latestArticles.articles[].order` (Number)

---

## Updated Shape

```text
latestArticles
+-- linkText (String)
+-- ctaText (String)
`-- articles[]
  +-- ctaText (String)
  `-- order (Number)
```

---

## Field Details

| Field | Required | Description |
|------|----------|-------------|
| `latestArticles.linkText` | YES | Text for the section header link that opens the full articles sidebar. Example: `View all`. |
| `latestArticles.ctaText` | YES | CTA text for the full articles sidebar action button. Example: `Got it`. |
| `latestArticles.articles[].ctaText` | YES | CTA text shown for each article item inside the sidebar list. Example: `View Now`. |
| `latestArticles.articles[].order` | YES | Numeric display order for article cards and sidebar article list. Lower numbers appear first. |

---

## Sample Value

```json
{
  "latestArticles": {
    "linkText": "View all",
    "ctaText": "Got it",
    "articles": [
      {
        "ctaText": "View Now",
        "order": 1
      },
      {
        "ctaText": "Read More",
        "order": 2
      }
    ]
  }
}
```
