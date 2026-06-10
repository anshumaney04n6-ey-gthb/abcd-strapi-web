# Health Insurance Dashboard Page - Complete Schema Documentation

## Content-Type: Insurance Dashboard Page (HIDashboard)

**Collection Name:** `health-insurance-dashboard-pages`  
**Singular Name:** `health-insurance-dashboard-page`  
**Plural Name:** `health-insurance-dashboard-pages`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Current)

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `partner` | string | No | `default` | Optional partner variant |
| `header` | object | No | fallback | Header logo config |
| `footer` | object | No | fallback | Footer heading/certification/features/logo |
| `disclaimer` | object | No | fallback | Disclaimer sidebar/modal content |
| `sidebarFAQs` | object | No | fallback | FAQ block for sidebar |
| `quickSolutionCard` | object | No | fallback | Quick action card |
| `heroSlides` | object | No | fallback | Hero carousel slides |
| `productCards` | object | No | fallback | Product cards as keyed object |
| `trustMarkers` | object | No | fallback | Trust marker list |
| `discoverItems` | object | No | fallback | Discover cards as keyed object |
| `manageItems` | object | No | fallback | Manage cards as keyed object |
| `trackApplication` | object | No | fallback | Track application sidebar content |
| `contactUs` | object | No | fallback | Contact sidebar content (with nested contactInfo) |
| `cashlessHospitalization` | object | No | fallback | Cashless sidebar banner/sections |
| `healthplans` | array | No | fallback | Health plans and plan benefit chips |
| `healthPlansSidebar` | object | No | fallback | View-all-plans and plan-benefits sidebar text |

---

## Deprecated / Removed Fields

The following legacy fields are no longer part of the current schema contract:

- `footerFeatures`
- `footerReferenceHeading`
- `footerReferenceName`
- `footerReferenceCertification`
- `footerLogo`
- `footerSideLogo`
- `contactInfo` (top-level)
- `cashlessHospitalizationBanner`
- `cashlessHospitalizationSections`
- `cashlessHospitalizationSidebar`
- `trackApplicationSidebar`
- `contactUsSidebar`

---

## API Endpoints

### Base URL

```
/api/health-insurance-dashboard-pages
```

### Supported Methods

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health-insurance-dashboard-pages` | List dashboard pages |
| GET | `/api/health-insurance-dashboard-pages/:id` | Get one dashboard page |
| POST | `/api/health-insurance-dashboard-pages` | Create dashboard page |
| PUT | `/api/health-insurance-dashboard-pages/:id` | Update dashboard page |
| DELETE | `/api/health-insurance-dashboard-pages/:id` | Delete dashboard page |

### Common Query

```
GET /api/health-insurance-dashboard-pages?filters[partner][$eq]=default&populate=deep
```

---

## Current JSON Contract (Aligned to fallback)

```json
{
  "data": {
    "subProduct": "health",
    "partner": "default",

    "header": {
      "logo": {
        "src": "media", // media
        "alt": "ABCD Logo",
        "size": "large"
      },
      "mobileLogo": {
        "src": "media", // media
        "alt": "ABCD Logo",
        "size": "default"  // dropdown options small | large | default
      }
    },

    "footer": {
      "heading": "Powered by - HI",
      "certification": "ISO 27001:2013 certified. - HI",
      "features": [
        "23M+ lives insured nationwide",
        "Easy claim assistance",
        "96% claims settled (FY 2024-25)"
      ],
      "logo": {
        "src": "media", // media
        "alt": "Footer Logo"
      },
      "sideLogo": {
        "src": "media", // media
        "alt": "Footer Side Logo"
      }
    },

    "disclaimer": {
      "headerAndDashboardTitle": "Disclaimer HI",
      "title": "Disclaimer - HI",
      "content": "Aditya Birla Capital Digital Ltd (ABCDL) is a distributor of insurance products and the obligation of insurance is subject to the terms and conditions of the insurance policy. The insurance product is underwritten by Aditya Birla Health Insurance Co. Ltd. (ABHICL). ABCDL does not underwrite the insurance or guarantee the obligations of ABHICL. Please read the policy document carefully before purchasing. The information herein is for general guidance and is not a substitute for professional medical advice. ABCDL shall not be held responsible for any loss or damage caused due to your reliance on any information provided herein.",
      "ctaLabel": "Done",
      "enabled": true
    },

    "sidebarFAQs": {
      "enabled": true,
      "content": [
        {
          "title": "What does my health insurance cover?",
          "content": "Health insurance protects you financially...",
          "icon": "media",
          "isExternal": false,
        },
        {
            "title": "When can I start using my policy?",
            "content": "ABCD health insurance offers comprehensive coverage with cashless claims at network hospitals, easy renewal, and customizable plans to suit your needs.",
            "icon": "media", // media
            "isExternal": false,
        },
        {
          "title": "Other questions?",
          "content": "",
          "icon": "media",
          "isExternal": true,
          "externalUrl": "https://help.abcd.com/health-insurance",
        },
      ]
    },

    "quickSolutionCard": {
      "enabled": true,
      "icon": "media", // media
      "title": "Need quick solutions?",
      "subtitle": "Buy Pocket insurance tailored for your needs!",
      "destinationUrl": "https://www.abcd.com/health-insurance/pocket"
    },

    "heroSlides": {
      "enabled": true,
      "content": [
        {
          "title": "Health Insurance is now Tax-free!",
          "subtitle": "Get the same coverage at a lower premium.",
          "ctaText": "Buy now",
          "destinationUrl": "https://www.abcd.com/health-insurance/buy",
          "bannerIcon": "media", // media
        },
        {
            "title": "Comprehensive Coverage for Your Family",
            "subtitle": "Protect your loved ones with our best plans.",
            "ctaText": "Get Quote",
            "destinationUrl": "https://www.abcd.com/health-insurance/get-quote",
        }
      ]
    },

    "productCards": {
      "enabled": true,
      "newHealthPlan": {
        "enable": true,
        "title": "New health Plan",
        "description": "Insure you and your family's health with the right cover",
        "ctaText": "Explore",
        "badge": "Popular",
        "illustration": {
          "icon": "media",
          "accentEllipse": "media"
        }
      },
      "superTopUp": {
        "enable": true,
        "title": "Super Top Up Plan",
        "description": "Upgrade your current plan",
        "ctaText": "Explore",
        "illustration": {
          "icon": "media",
          "accentEllipse": "media"
        }
      },
      "portYourPolicy": {
        "enable": true,
        "title": "Port your policy",
        "description": "Change your existing insurer",
        "ctaText": "Explore",
        "illustration": {
          "icon": "media", // media
          "accentEllipse": "media" // media
        }
      }
    },

    "trustMarkers": {
      "enabled": true,
      "content": [
        {
            "icon": "media", // media
            "text": "23M+ lives insured nationwide",
        },
        {
            "icon": "media", // media
            "text": "Easy claim assistance",
        },
        {
            "icon": "media", // media
            "text": "96% claims settled (FY 2024-25)",
        },
      ]
    },

    "discoverItems": {
      "enabled": true,
      "cashlessClaims": {
        "enabled": true,
        "icon": "media", // media
        "title": "Cashless claims at 12,900+ hospitals",
        "description": "No upfront payments. No stress. Just care."
      },
      "viewAllPlans": {
        "enabled": true,
        "icon": "media", // media
        "title": "View all plans",
        "description": "View and compare health insurance plans"
      },
      "healthTrack": {
        "enabled": true,
        "icon": "media", // media
        "title": "Health Track",
        "description": "One quick face scan. 20+ health insights",
        "highlighted": true,
        "theme": "yellow", // dropdown options yellow | purple
        "destinationUrl": "https://www.abcd.com/health-insurance/health-track"
      }
    },

    "manageItems": {
      "enabled": true,
      "aiPolicyReader": {
        "enabled": true,
        "icon": "media", // media
        "title": "Know your existing health policy",
        "description": "See what your policy covers in minutes",
        "highlighted": true,
        "theme": "yellow", // dropdown options yellow | purple
        "destinationUrl": "https://www.abcd.com/health-insurance/policy-reader"
      },
      "myPolicies": {
        "enabled": true,
        "icon": "media", // media
        "title": "My policies",
        "description": "View your active and past policies"
      }
    },

    "trackApplicationSidebar": {
      "headerTitle": "Home Page",
      "pageTitle": "Track your application",
      "helpBannerMessage": "Contact us if you need any help",
      "ctaLabel": "Done"
    },

    "contactUsSidebar": {
      "headerTitle": "Home Page",
      "pageTitle": "Contact us at:",
      "ctaLabel": "Done",
      "contactInfo": [
        {
          "label": "Contact number:",
          "value": "1800 270 7000",
          "order": 1
        },
        {
          "label": "E-mail:",
          "value": "care.digital@adityabirlacapital.com",
          "order": 2
        }
      ]
    },

    "cashlessHospitalizationSidebar": {
      "headerTitle": "Cashless hospitalization - HI",
      "ctaLabel": "Done - HI",
      "banner": {
        "title": "Go cashless at any hospital for worry-free coverage.",
        "actionLabel": "List of cashless network hospitals",
        "actionUrl": "https://www.adityabirlacapital.com"
      },
      "sections": [
      {
        "title": "Steps to follow:",
        "items": [
          {
            "title": "For planned hospitalization -",
            "description": "Claim intimation to be done at least 48 hours before hospitalization"
          },
          {
            "title": "For emergency hospitalization -",
            "description": "Claim intimation to be done within 48 hours of hospitalization"
          }
        ]
      },
      {
        "title": "Points to know:",
        "items": [
          {
            "title": "",
            "description": "This facility will be available subject to acceptance of the hospital."
          },
          {
            "title": "",
            "description": "Policy benefits, exclusions and inclusions are subject to terms and conditions."
          },
          {
            "title": "",
            "description": "Service is not available at Blacklisted hospitals."
          }
        ]
      },
      {
        "title": "Claim intimation:",
        "items": [
          {
            "title": "Toll-free number -",
            "description": "1800 270 7000"
          },
          {
            "title": "Email -",
            "description": "care.digital@adityabirlacapital.com"
          }
        ]
      }   
    ]
    },

    "healthPlansSidebar": {
      "viewAllPlansSidebar": {
        "pageTitle": "Home Page",
        "ctaLabel": "Done"
      },
      "planBenefitsSidebar": {
        "pageTitle": "Plan details"
      }
    }
  }
}
```

---

## Component-Level Notes

### `header`

- `header.logo` and `header.mobileLogo` are nested objects with `src`, `alt`, `size`.
- Legacy keys like `logoSrc`, `logoAlt`, `logoSize` are deprecated.

### `footer`

- Footer is now a grouped object (`heading`, `certification`, `features`, `logo`, `sideLogo`).
- Legacy top-level footer keys are deprecated.

### `sidebarFAQs`

- Uses `content[]`.
- Each entry supports `icon` directly from CMS.

### `productCards`, `discoverItems`, `manageItems`

- `productCards` is keyed by `newHealthPlan`, `superTopUp`, `portYourPolicy`.
- `discoverItems` is keyed by `cashlessClaims`, `viewAllPlans`, `healthTrack`.
- `manageItems` is keyed by `aiPolicyReader`, `myPolicies`.
- All three support section-level `enabled`; cards support item-level `enabled`/`enable`.

### `trackApplication` and `contactUs`

- These replace legacy sidebar-specific and top-level contact blocks.
- CTA key is `ctaLabel`.
- `contactUs.contactInfo[]` expects `label` and `value` (no `itemId` required).

### `cashlessHospitalization`

- Single consolidated object with `headerTitle`, `ctaLabel`, `banner`, `sections`.
- Replaces separate banner/sections/sidebar objects.

### `healthPlansSidebar`

- Current fallback contract uses:
  - `viewAllPlansSidebar.pageTitle`, `viewAllPlansSidebar.ctaLabel`
  - `planBenefitsSidebar.pageTitle`

### `header.logo.size and header.mobileLogo.size`
- This needs to be a dropdown with options - small | large | default

### `manageItems and discover - theme`
- theme needs to be a dropdown with options - yellow | purple

---

## Populate Query

```
GET /api/health-insurance-dashboard-pages?filters[partner][$eq]=default&populate=deep
```
