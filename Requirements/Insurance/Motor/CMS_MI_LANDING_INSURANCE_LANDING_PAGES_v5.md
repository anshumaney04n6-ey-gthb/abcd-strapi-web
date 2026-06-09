# Motor Landing CMS Requirements

---

**Date:** 2026-05-11   
**Purpose:** Define Strapi schema and sample payloads for sections currently expected by insurance-web but missing or incomplete in CMS for the motor landing page.

---

**Content Type:** `insurance-landing-page`  
**API Endpoint:** `GET /api/insurance-landing-pages?filters[subProduct][$eq]=motor&filters[partner][$eq]=default&populate=*`

---

## Table of Contents

1. [Content Keys](#content-keys)
2. [Component Structure](#component-structure)
   - [Component - Motor Statistics](#component---motor-statistics)
3. [Sample API Response](#sample-api-response)

---


## Content Keys

| Section | CMS Key | Content Type |
|---------|---------|--------------|
| Motor Statistics | `motorStatistics` | component |
| motorCriticalIconUrl | `motorCriticalIconUrl` | String |
| motorCriticalIconAlt | `motorCriticalIconAlt` | String |
| positiveIconSrc | `positiveIconSrc` | String |
| positiveIconAlt | `positiveIconAlt` | String |
| negativeIconSrc | `negativeIconSrc` | String |
| negativeIconAlt | `negativeIconAlt` | String |
| negativeIconOnlySrc | `negativeIconOnlySrc` | String |
| addOnsBenefitIconSrc | `addOnsBenefitIconSrc` | String |
| typeOfMotorButtonIconUrl | `typeOfMotorButtonIconUrl` | String |
| vehicleBannerHouseLogoSrc | `vehicleBannerHouseLogoSrc` | String |
| vehicleBannerHouseLogoAlt | `vehicleBannerHouseLogoAlt` | String |
| vehicleBannerQrSrc | `vehicleBannerQrSrc` | String |
| vehicleBannerQrAlt | `vehicleBannerQrAlt` | String |
| vehicleBannerHeroImageSrc | `vehicleBannerHeroImageSrc` | String |
| vehicleBannerHeroImageAlt | `vehicleBannerHeroImageAlt` | String |

---

## Component Structure

### Component - Motor Statistics

**CMS Key:** `motorStatistics`  
**Fallback Constant:** `FALLBACK_LANDING_CONTENT.motorStatistics`

#### Component Structure
```
├── motorStatistics (component)
    ├── enabled (Boolean)
    └── content (object)
        └── items (array of objects)
            ├── id (String)
            ├── title (String, optional)
            ├── value (String, optional)
            ├── description (String)
            ├── iconUrl (String)
            └── order (Integer)
```
 

#### Sample JSON Data
```json
{
  "motorStatistics": {
    "enabled": true,
    "content": {
      "items": [
        {
          "id": "0",
          "title": "Legal Requirements Changed in 2025",
          "description": "New motor vehicle regulations introduced in 2025 have strengthened insurance mandates, increased coverage limits, and imposed stricter penalties for non-compliance.",
          "iconUrl": "/assets/landing/motorLegalRequirementLogo.webp",
          "order": 0
        },
        {
          "id": "1",
          "value": "5.8 Lakh",
          "description": "Motor vehicle accidents in India annually",
          "iconUrl": "/assets/landing/statistic1.webp",
          "order": 1
        },
        {
          "id": "2",
          "value": "₹2.5 Lakh",
          "description": "Average motor accident claim amount",
          "iconUrl": "/assets/landing/statistic2.webp",
          "order": 2
        },
        {
          "id": "3",
          "value": "72%",
          "description": "Vehicles in India are under-insured with only basic third-party cover",
          "iconUrl": "/assets/landing/statistic3.webp",
          "order": 3
        },
        {
          "id": "4",
          "value": "₹2,500",
          "description": "Fine for driving without a valid insurance",
          "iconUrl": "/assets/landing/statistic4.webp",
          "order": 4
        }
      ]
    }
  }
}
```


---

## Sample API Response

```json
{
  "data": [
    {
      "motorStatistics": {
        "enabled": true,
        "content": {
          "items": [
            {
              "id": "0",
              "title": "Legal Requirements Changed in 2025",
              "value": null,
              "description": "New motor vehicle regulations introduced in 2025 have strengthened insurance mandates, increased coverage limits, and imposed stricter penalties for non-compliance.",
              "iconUrl": "/assets/landing/motorLegalRequirementLogo.webp",
              "order": 0
            },
            {
              "id": "1",
              "title": null,
              "value": "5.8 Lakh",
              "description": "Motor vehicle accidents in India annually",
              "iconUrl": "/assets/landing/statistic1.webp",
              "order": 1
            },
            {
              "id": "2",
              "title": null,
              "value": "₹2.5 Lakh",
              "description": "Average motor accident claim amount",
              "iconUrl": "/assets/landing/statistic2.webp",
              "order": 2
            },
            {
              "id": "3",
              "title": null,
              "value": "72%",
              "description": "Vehicles in India are under-insured with only basic third-party cover",
              "iconUrl": "/assets/landing/statistic3.webp",
              "order": 3
            },
            {
              "id": "4",
              "title": null,
              "value": "₹2,500",
              "description": "Fine for driving without a valid insurance",
              "iconUrl": "/assets/landing/statistic4.webp",
              "order": 4
            }
          ]
        }
      }
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

---

