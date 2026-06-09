# Strapi Requirement: digimetal-cohort-banners

## Content Type

**Collection Name:** `digimetal-cohort-banners`

## Structure

Each entry represents a cohort+subProduct+partner combination and contains an array of promo banners.

### Top-Level Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `subProduct` | Enumeration (`gold`, `silver`) | Yes | Product filter |
| `partner` | Short text | No | Partner code filter (e.g., `abcd`, `partner_x`). If empty, applies to all partners |
| `cohortId` | Short text | Yes | Cohort identifier (e.g., `COHORT_A1`) |
| `promoBanners` | Repeatable Component | Yes | Array of promo banner items |

### promoBanners Component Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `backgroundColor` | Short text | Yes | CSS color or gradient (e.g., `linear-gradient(180deg, #fff4ce 32%, #f7a500 215%)`) |
| `preTitle` | Short text | No | Small text above the title |
| `preTitleColor` | Short text | No | CSS color for pre-title |
| `title` | Short text | Yes | Main banner title |
| `highlightedText` | Short text | No | Highlighted portion within the title |
| `subtitle` | Short text | No | Text below the title |
| `ctaText` | Short text | Yes | CTA button label |
| `ctaUrl` | Short text | No | URL the CTA navigates to |
| `image` | Media (single) | No | Banner image (square variant). Use Strapi's built-in `alternativeText` for alt. |
| `leftImage` | Media (single) | No | Left image (landscape variant). Use Strapi's built-in `alternativeText` for alt. |
| `rightImage` | Media (single) | No | Right image (landscape variant). Use Strapi's built-in `alternativeText` for alt. |
| `order` | Integer | No | Sort order (ascending) |

## Filtering

The web app queries this content type with these Strapi filters:

```
filters[subProduct][$eq]=gold
filters[cohortId][$eq]=COHORT_A1
filters[partner][$eq]=abcd 
populate[promoBanners][populate]=*
```

## Sample Strapi API Response

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "subProduct": "gold",
        "partner": "abcd",
        "cohortId": "COHORT_A1",
        "promoBanners": [
          {
            "id": 1,
            "backgroundColor": "linear-gradient(180deg, #fff4ce 32%, #f7a500 215%)",
            "preTitle": "EXCLUSIVE OFFER",
            "preTitleColor": "#845800",
            "title": "Unlock potential growth with",
            "highlightedText": "Gold SIP",
            "subtitle": "Starting from \u20b9100",
            "ctaText": "Start SIP",
            "ctaUrl": "/digitalmetal/gold/customer/sip",
            "image": null,
            "leftImage": {
              "data": {
                "attributes": {
                  "url": "/uploads/gold_bar_left.webp",
                  "alternativeText": "Gold bars"
                }
              }
            },
            "rightImage": {
              "data": {
                "attributes": {
                  "url": "/uploads/gold_bar_right.webp",
                  "alternativeText": "Gold coins"
                }
              }
            },
            "order": 1
          },
          {
            "id": 2,
            "backgroundColor": "linear-gradient(180deg, #e8f5e9 32%, #81c784 215%)",
            "preTitle": "NEW",
            "preTitleColor": "#2e7d32",
            "title": "Gift digital gold to",
            "highlightedText": "your loved ones",
            "subtitle": "Instant delivery, zero hassle",
            "ctaText": "Send Gift",
            "ctaUrl": "/digitalmetal/gold/customer/gift",
            "image": null,
            "leftImage": {
              "data": {
                "attributes": {
                  "url": "/uploads/gift_left.webp",
                  "alternativeText": "Gift box"
                }
              }
            },
            "rightImage": {
              "data": {
                "attributes": {
                  "url": "/uploads/gift_right.webp",
                  "alternativeText": "Gold gift"
                }
              }
            },
            "order": 2
          }
        ]
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 1,
      "total": 1
    }
  }
}
```


