# Health Insurance Dashboard Page - Complete Schema Documentation

## Content-Type: Insurance Dashboard Page (HIDashboard)

**Collection Name:** `health-insurance-dashboard-pages`  
**Singular Name:** `health-insurance-dashboard-page`  
**Plural Name:** `health-insurance-dashboard-pages`  
**Draft & Publish:** Enabled

> **Changelog:**
> - **v1** (2026-05-19): Initial schema — sidebarFAQs, footer, productCards, trustMarkers, discoverItems, heroSlides.
> - **v2** (2026-05-20): Added `quickSolutionCard`, `disclaimer`, `manageItems`, `contactInfo`, `cashlessHospitalizationBanner`, `cashlessHospitalizationSections`, `cashlessHospitalizationSidebar`, `header` and unified `healthplans` + `healthPlansSidebar`.

---

## All Content-Type Fields (Exact Strapi Field Names)

> Fields marked **[NEW v2]** were added in v2 based on `fallback.ts` alignment.

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `partner` | string | No | `default` | - | Optional partner-specific variant |
| `header` | component | No | fallback | - | Header logo and branding configuration |
| `footerFeatures` | component | No | fallback | - | Footer trust/features list |
| `footerReferenceHeading` | string | No | fallback | - | Footer reference heading |
| `footerReferenceName` | string | No | fallback | - | Footer reference name |
| `footerReferenceCertification` | string | No | fallback | - | Footer certification text |
| `footerLogo` | media/string | No | fallback | - | Footer reference logo |
| `footerSideLogo` | media/string | No | fallback | - | Footer side reference icon |
| `sidebarFAQs` | component | No | fallback | - | Sidebar FAQ block shown in left rail |
| `productCards` | component | No | fallback | - | Product discovery cards |
| `trustMarkers` | component | No | fallback | - | Trust marker pills/cards |
| `discoverItems` | component | No | fallback | - | Discover section cards |
| `heroSlides` | component | No | fallback | - | Hero carousel slides |
| `quickSolutionCard` | component | No | fallback | - | **[NEW v2]** Quick solution CTA card |
| `disclaimer` | component | No | fallback | - | **[NEW v2]** Disclaimer modal content |
| `manageItems` | component | No | fallback | - | **[NEW v2]** Manage section cards |
| `contactInfo` | component | No | fallback | - | **[NEW v2]** Contact Us sidebar entries |
| `cashlessHospitalizationBanner` | component | No | fallback | - | **[NEW v2]** Cashless hospitalization sidebar banner |
| `cashlessHospitalizationSections` | component | No | fallback | - | **[NEW v2]** Cashless hospitalization steps/points sections |
| `cashlessHospitalizationSidebar` | component | No | fallback | - | **[NEW v2]** Cashless hospitalization sidebar header/actions |
| `healthplans` | component | No | fallback | - | **[NEW v2]** Unified plans with embedded benefits chips/timeline |
| `healthPlansSidebar` | component | No | fallback | - | **[NEW v2]** Unified sidebar labels for view-all-plans and plan-benefits |
---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/health-insurance-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health-insurance-dashboard-pages` | List dashboard pages |
| GET | `/api/health-insurance-dashboard-pages/:id` | Get single dashboard page by ID |
| POST | `/api/health-insurance-dashboard-pages` | Create dashboard page |
| PUT | `/api/health-insurance-dashboard-pages/:id` | Update dashboard page |
| DELETE | `/api/health-insurance-dashboard-pages/:id` | Delete dashboard page |

### Query Parameters

**Filtering by Partner:**
```
?filters[partner][$eq]=default
?populate=*
```

**Full Health Dashboard Query:**
```
GET /api/health-insurance-dashboard-pages?
  filters[partner][$eq]=default&
  populate=*
```

**Partner-Specific Content (example):**
```
GET /api/health-insurance-dashboard-pages?
  filters[partner][$eq]=hdfc&
  populate=*
```

---

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health-insurance-dashboard-pages` | List dashboard pages |
| GET | `/api/health-insurance-dashboard-pages/:id` | Get single dashboard page by ID |
| POST | `/api/health-insurance-dashboard-pages` | Create dashboard page |
| PUT | `/api/health-insurance-dashboard-pages/:id` | Update dashboard page |
| DELETE | `/api/health-insurance-dashboard-pages/:id` | Delete dashboard page |

---

### Request Example

**URL:**
```
GET https://cms.abcd.io/api/health-insurance-dashboard-pages?
  filters[partner][$eq]=default&
  populate=*
```
---

### Response Payload Structure

**Success Response (200 OK):**
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123xyz",
      "attributes": {
        "partner": "default",
        "footerFeatures": {
          "content": [
            {
              "featId": "feat-1",
              "text": "23M+ lives insured nationwide",
              "order": 1
            }
          ]
        },
        "footerReferenceHeading": "Powered by",
        "footerReferenceName": "ABCD",
        "footerReferenceCertification": "ISO 27001:2013 certified.",
        "footerLogo": "media", // media
        "footerSideLogo": "media", // media
        "sidebarFAQs": {
          "content": [
            {
              "faqId": "why-health-insurance",
              "title": "Why Health Insurance?",
              "content": "Health insurance protects you financially...",
              "isExternal": false,
              "order": 1
            }
          ]
        },
        "createdAt": "2026-05-18T10:30:00Z",
        "updatedAt": "2026-05-20T10:30:00Z",
        "publishedAt": "2026-05-20T10:30:00Z"
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

**Empty Response (No Match):**
```json
{
  "data": [],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 0,
      "total": 0
    }
  }
}
```

---

## Complete JSON Structure with order fields

> **Note:** Keep this structure aligned with `DashboardClient.tsx` props and `fallback.ts`.  
> **Note:** For repeatable arrays, use `order` in each item when ordering matters.  
> **Note:** Fields marked **[NEW v2]** were introduced in v2.

```json
{
  "data": {
    "subProduct": "health",
    "partner": "default",

    "footerFeatures": {
      "content": [
        { "featId": "feat-1", "text": "23M+ lives insured nationwide", "order": 1 },
        { "featId": "feat-2", "text": "Easy claim assistance", "order": 2 },
        { "featId": "feat-3", "text": "96% claims settled (FY 2024-25)", "order": 3 }
      ]
    },

    "footerReferenceHeading": "Powered by",
    "footerReferenceName": "ABCD",
    "footerReferenceCertification": "ISO 27001:2013 certified.",
    "footerLogo": "media", //media
    "footerSideLogo": "media", //media

    "header": {
      "logoSrc": "media", //media
      "logoAlt": "ABCD Logo",
      "logoSize": "default",
      "mobileLogoSrc": "media", //media
      "mobileLogoAlt": "ABCD Logo",
      "mobileLogoSize": "default"
    },

    "sidebarFAQs": {
      "content": [
        {
          "faqId": "why-health-insurance",
          "title": "Why Health Insurance?",
          "content": "Health insurance protects you financially from medical expenses...",
          "isExternal": false,
          "order": 1
        },
        {
          "faqId": "how-it-works",
          "title": "How Health Insurance at ABCD works?",
          "content": "ABCD health insurance offers comprehensive coverage...",
          "isExternal": false,
          "order": 2
        },
        {
          "faqId": "other-questions",
          "title": "Other questions?",
          "content": "",
          "isExternal": true,
          "externalUrl": "https://help.abcd.com/health-insurance",
          "order": 3
        }
      ]
    },
    "productCards": {
      "content": [
        {
          "cardId": "new-health-plan",
          "title": "New health Plan",
          "description": "Insure you and your family's health with the right cover",
          "ctaText": "Explore",
          "badge": "Popular",
          "enable": true,
          "order": 1,
          "illustration": {
            "iconPath": "media", //media
            "accentEllipsePath": "media", //media
          }
        }
      ]
    },

    "trustMarkers": {
      "content": [
        {
          "markerId": "lives-insured",
          "text": "23M+ lives insured nationwide",
          "iconPath": "media", //media
          "order": 1
        }
      ]
    },

    "discoverItems": {
      "content": [
        {
          "itemId": "cashless-claims",
          "title": "Cashless claims at 12,900+ hospitals",
          "description": "No upfront payments. No stress. Just care.",
          "iconPath": "media", //media
          "showChevron": true,
          "destinationUrl": "https://www.abcd.com/health-insurance/cashless-hospitals",
          "order": 1
        },
        {
          "itemId": "health-track",
          "title": "Health Track",
          "description": "One quick face scan. 20+ health insights",
          "iconPath": "media", //media
          "highlighted": true,
          "theme": "purple",
          "iconSize": 32,
          "destinationUrl": "https://google.com",
          "order": 3
        }
      ]
    },

    "heroSlides": {
      "content": [
        {
          "slideId": "slide-1",
          "title": "Health Insurance is now Tax-free!",
          "subtitle": "Get the same coverage at a lower premium.",
          "ctaText": "Buy now",
          "destinationUrl": "https://www.abcd.com/health-insurance/buy",
          "bannerIcon": "media", //media
          "order": 1
        },
        {
          "slideId": "slide-2",
          "title": "Comprehensive Coverage for Your Family",
          "subtitle": "Protect your loved ones with our best plans.",
          "ctaText": "Get Quote",
          "order": 2
        }
      ]
    },

    "quickSolutionCard": {
      "content": {
        "title": "Need quick solutions?",
        "subtitle": "Buy Pocket insurance tailored for your needs!",
        "destinationUrl": "https://google.com",
        "icon": "media", //media
      }
    },

    "disclaimer": {
      "content": {
        "headerTitle": "Disclaimer",
        "title": "Disclaimer",
        "content": "Disclaimer body text...",
        "doneButtonText": "Done"
      }
    },

    "manageItems": {
      "content": [
        {
          "itemId": "ai-policy-reader",
          "icon": "media", //media
          "title": "Know your existing health policy",
          "description": "See what your policy covers in minutes",
          "trailingIcon": "media", //media
          "showChevron": true,
          "highlighted": true,
          "iconSize": 26,
          "destinationUrl": "https://google.com",
          "order": 1
        },
        {
          "itemId": "my-policies",
          "icon": "media", //media
          "title": "My policies",
          "description": "View your active and past policies",
          "showChevron": true,
          "order": 2
        }
      ]
    },

    "contactInfo": {
      "content": [
        {
          "itemId": "contact-number",
          "label": "Contact number:",
          "value": "1800 270 7000",
          "order": 1
        },
        {
          "itemId": "email",
          "label": "E-mail:",
          "value": "care.digital@adityabirlacapital.com",
          "order": 2
        }
      ]
    },

    "cashlessHospitalizationBanner": {
      "content": {
        "message": "Go cashless at any hospital for worry-free coverage.",
        "actionLabel": "List of cashless network hospitals",
        "actionUrl": "https://www.adityabirlacapital.com"
      }
    },

    "cashlessHospitalizationSections": {
      "content": [
        {
          "sectionId": "steps-to-follow",
          "title": "Steps to follow:",
          "icon": "media", //media
          "order": 1,
          "items": [
            {
              "itemId": "planned",
              "title": "For planned hospitalization -",
              "description": "Claim intimation to be done at least 48 hours before hospitalization",
              "order": 1
            },
            {
              "itemId": "emergency",
              "title": "For emergency hospitalization -",
              "description": "Claim intimation to be done within 48 hours of hospitalization",
              "order": 2
            }
          ]
        },
        {
          "sectionId": "points-to-know",
          "title": "Points to know:",
          "icon": "media", //media
          "order": 2,
          "items": [
            {
              "itemId": "acceptance",
              "description": "This facility will be available subject to acceptance of the hospital.",
              "order": 1
            },
            {
              "itemId": "terms",
              "description": "Policy benefits, exclusions and inclusions are subject to terms and conditions.",
              "order": 2
            },
            {
              "itemId": "blacklist",
              "description": "Service is not available at Blacklisted hospitals.",
              "order": 3
            }
          ]
        },
        {
          "sectionId": "claim-intimation",
          "title": "Claim intimation:",
          "icon": "media", //media
          "order": 3,
          "items": [
            {
              "itemId": "toll-free",
              "title": "Toll-free number -",
              "description": "1800 270 7000",
              "order": 1
            },
            {
              "itemId": "email",
              "title": "Email -",
              "description": "care.digital@adityabirlacapital.com",
              "order": 2
            }
          ]
        }
      ]
    },

    "cashlessHospitalizationSidebar": {
      "headerTitle": "Cashless hospitalization",
      "doneButtonText": "Done",
    },

    "healthplans": [
      {
        "planId": "plan-1",
        "logoUrl": "media", //media
        "planName": "ABHI Health Secure",
        "ctaText": "Buy now",
        "benefits": ["HealthReturns up to 100%", "Single private AC room", "Super reload", "Super credit"],
        "showDetailsLink": true,
        "detailsLinkText": "View more details",
        "planBenefits": {
          "policyDocsLabel": "Policy docs",
          "chips": [
            { 
              "chipId": "top-benefits", 
              "label": "Top benefits", 
              "benefits": [
                {
                  "icon": "media", //media
                  "title": "HealthReturns up to 100%",
                  "description": "Earn premium returns by maintaining healthy activity goals.",
                },
                {
                  "icon": "media", //media
                  "title": "Customize your plan",
                  "description": "Adjust benefits with optional add-ons based on your family needs.",
                },
                {
                  "icon": "media", //media
                  "title": "Home health care",
                  "description": "Access selected healthcare services at home under policy terms.",
                },
              ]
            },
            { 
              "chipId": "covered", 
              "label": "What's Covered?", 
              "benefits": [
                {
                  "icon": "media", //media
                  "title": "In-patient hospitalization",
                  "description": "Covers hospitalization expenses for covered illnesses and procedures.",
                },
                {
                  "icon": "media", //media
                  "title": "Day care procedures",
                  "description": "Includes eligible same-day treatments that do not require 24-hour admission.",
                },
                {
                  "icon": "media", //media
                  "title": "Cashless treatment",
                  "description": "Cashless access at network hospitals subject to policy terms and conditions.",
                }
              ]
            },
            {
              "chipId": "waiting-period",
              "label": "Waiting period",
              "timeline": [
                {
                  "period": "30 days after activation",
                  "description": [
                    "Accidental Cover"
                  ]
                }, {
                  "period": "2 years after activation",
                  "description": [
                    "Accidental Cover",
                    "Specific Illnesses Cover",
                  ]
                }, {
                  "period": "3 years after activation",
                  "description": [
                    "Accidental Cover",
                    "Specific Illnesses Cover",
                    "Maternity and Newborn Cover"
                  ]
                }
              ]
            },
            {  
              "chipId": "eligibility-criteria",
              "label": "Eligibility Criteria",
              "benefits": [
                {
                  "icon": "media", //media
                  "title": "Minimum/Maximum entry age (Adult)",
                  "description": [
                    "Minimum 18 years, Maximum - No capping",
                  ],
                },{
                  "icon": "media", //media
                  "title": "Minimum/Maximum entry age (Child)",
                  "description": [
                    "Depending Child (Floater / Multi Individual), Maximum - 91 days to 25 years",
                    "Individual - minimum age of entry - 5 years"
                  ],
                },
              ],
            }
          ],
          "defaultChipId": "top-benefits"
        },
      },
      {
        "planId": "plan-2",
        "logoUrl": "media", //media
        "planName": "ABHI Health Secure Plus",
        "ctaText": "Buy now",
        "benefits": ["HealthReturns up to 100%", "Single private AC room", "Super reload", "Super credit"],
        "showDetailsLink": true,
        "detailsLinkText": "View more details",
        "planBenefits": {
          "policyDocsLabel": "Policy docs",
          "chips": [
            {
              "chipId": "waiting-period",
              "label": "Waiting period",
              "timeline": [
                {
                  "period": "30 days after activation",
                  "description": [
                    "Accidental Cover"
                  ]
                }, {
                  "period": "2 years after activation",
                  "description": [
                    "Accidental Cover",
                    "Specific Illnesses Cover",
                  ]
                }, {
                  "period": "3 years after activation",
                  "description": [
                    "Accidental Cover",
                    "Specific Illnesses Cover",
                    "Maternity and Newborn Cover"
                  ]
                }
              ]
            },
            {
              "chipId": "eligibility-criteria",
              "label": "Eligibility Criteria",
              "benefits": [
                {
                  "icon": "media", //media
                  "title": "Minimum/Maximum entry age (Adult)",
                  "description": [
                    "Minimum 18 years, Maximum - No capping",
                  ],
                },{
                  "icon": "media", //media
                  "title": "Minimum/Maximum entry age (Child)",
                  "description": [
                    "Depending Child (Floater / Multi Individual), Maximum - 91 days to 25 years",
                    "Individual - minimum age of entry - 5 years"
                  ],
                },
              ],
            }
          ],
          "defaultChipId": "waiting-period"
        },
      }
    ],

    "healthPlansSidebar": {
      "viewAllPlansSidebar": {
        "pageTitle": "Home Page",
        "doneButtonText": "Done",
        "headerTitle": "",
        "subTitle": "",
        "searchPlaceholder": "Ask me anything?"
      },
      "planBenefitsSidebar": {
        "pageTitle": "Plan details",
        "headerTitle": "",
        "subTitle": "",
        "searchPlaceholder": "Ask me anything?"
      }
    }
  }
}
```

---

## Components Detail

### 1. insurance-dashboard.sidebar-faq-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `faqId` | string | Yes | - |
| `title` | string | Yes | - |
| `content` | text | No | "" |
| `isExternal` | boolean | No | `false` |
| `externalUrl` | string | No | - |
| `order` | number | No | 0 |

---

### 2. insurance-dashboard.footer-feature

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `featId` | string | Yes | - |
| `text` | string | Yes | - |
| `order` | number | No | 0 |

---

### 3. insurance-dashboard.product-card

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `cardId` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | string | No | "" |
| `ctaText` | string | No | "Explore" |
| `badge` | string | No | - |
| `enable` | boolean | No | `true` |
| `illustration.iconPath` | media/string | No | - |
| `illustration.accentEllipsePath` | media/string | No | - |
| `order` | number | No | 0 |

---

### 4. insurance-dashboard.trust-marker

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `markerId` | string | Yes | - |
| `text` | string | Yes | - |
| `iconPath` / `icon` | media/string | No | - |
| `order` | number | No | 0 |

---

### 5. insurance-dashboard.discover-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `itemId` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | string | No | "" |
| `iconPath` / `icon` | media/string | No | - |
| `trailingIcon` | media/string | No | - |
| `showChevron` | boolean | No | `false` |
| `highlighted` | boolean | No | `false` |
| `theme` | string | No | - |
| `iconSize` | number | No | - |
| `destinationUrl` | string | No | - |
| `order` | number | No | 0 |

---

### 6. insurance-dashboard.hero-slide

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `slideId` / `id` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |
| `ctaText` | string | No | - |
| `buyNowCtaDestination` | string | No | - |
| `bannerIconPath` / `bannerIcon` | media/string | No | - |
| `order` | number | No | 0 |

---

### 7. insurance-dashboard.quick-solution-card `[NEW v2]`

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `icon` | media/string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |
| `destinationUrl` | string | No | - |

---

### 8. insurance-dashboard.disclaimer `[NEW v2]`

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `headerTitle` | string | No | "Disclaimer" |
| `title` | string | No | "Disclaimer" |
| `content` | text | Yes | - |
| `doneButtonText` | string | No | "Done" |

---

### 9. insurance-dashboard.manage-item `[NEW v2]`

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `itemId` / `id` | string | Yes | - |
| `icon` | media/string | No | - |
| `trailingIcon` | media/string | No | - |
| `theme` | string | No | - |
| `title` | string | Yes | - |
| `description` | string | No | "" |
| `highlighted` | boolean | No | `false` |
| `iconSize` | number | No | - |
| `destinationUrl` | string | No | - |
| `showChevron` | boolean | No | `false` |
| `order` | number | No | 0 |

---

### 10. insurance-dashboard.contact-info-item `[NEW v2]`

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `itemId` / `id` | string | Yes | - |
| `label` | string | Yes | - |
| `value` | string | Yes | - |
| `order` | number | No | 0 |

---

### 11. insurance-dashboard.cashless-hospitalization-banner `[NEW v2]`

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `message` | text | Yes | - |
| `actionLabel` | string | No | - |
| `actionUrl` | string | No | - |

---

### 12. insurance-dashboard.cashless-hospitalization-section `[NEW v2]`

> Each section contains a repeatable list of items.

**Section fields:**

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `sectionId` | string | Yes | - |
| `title` | string | Yes | - |
| `order` | number | No | 0 |

**Section item fields (`items[]`):**

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `itemId` | string | Yes | - |
| `title` | string | No | - |
| `description` | string | Yes | - |
| `order` | number | No | 0 |

---

### 13. insurance-dashboard.healthplans `[NEW v2]`

> Unified plan model used in `healthplans[]`.

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `planId` | string | Yes | - |
| `logoUrl` | media/string | No | - |
| `planName` | string | Yes | - |
| `ctaText` | string | No | "Buy now" |
| `benefits` | string[] | No | [] |
| `showDetailsLink` | boolean | No | `false` |
| `detailsLinkText` | string | No | - |
| `planBenefits.policyDocsLabel` | string | No | "Policy docs" |
| `planBenefits.chips[]` | array | No | [] |
| `planBenefits.defaultChipId` | string | No | "top-benefits" |
| `order` | number | No | 0 |

**healthPlans chips fields (`chips[]`):**

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `itemId` | string | Yes | - |
| `title` | string | No | - |
| `description` | string | Yes | - |
| `order` | number | No | 0 |

---

### 14. insurance-dashboard.healthPlansSidebar `[NEW v2]`

> Unified sidebar labels for plans and plan benefits sidebars.

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `viewAllPlansSidebar.pageTitle` | string | No | "Home Page" |
| `viewAllPlansSidebar.doneButtonText` | string | No | "Done" |
| `viewAllPlansSidebar.headerTitle` | string | No | "" |
| `viewAllPlansSidebar.subTitle` | string | No | "" |
| `viewAllPlansSidebar.searchPlaceholder` | string | No | "Ask me anything?" |
| `planBenefitsSidebar.pageTitle` | string | No | "Plan details" |
| `planBenefitsSidebar.headerTitle` | string | No | "" |
| `planBenefitsSidebar.subTitle` | string | No | "" |
| `planBenefitsSidebar.searchPlaceholder` | string | No | "Ask me anything?" |

---

## Restrictions Summary Table

| Section | Component | Max Items |
|---------|-----------|-----------|
| Sidebar FAQs | sidebar-faq-item | 10 |
| Footer Features | footer-feature | 5 |
| Product Cards | product-card | 6 |
| Trust Markers | trust-marker | 6 |
| Discover Items | discover-item | 5 |
| Hero Slides | hero-slide | 10 |
| Manage Items `[NEW v2]` | manage-item | 10 |
| Contact Info `[NEW v2]` | contact-info-item | 5 |
| Cashless Hosp. Sections `[NEW v2]` | cashless-hospitalization-section | 5 |
| Health Plans `[NEW v2]` | healthplans | 20 |
| Health Plans Sidebar `[NEW v2]` | healthPlansSidebar | 5 blocks |

---

## Populate Query for Full Response

```
GET /api/health-insurance-dashboard-pages?
filters[partner][$eq]=default&
populate=deep
```

---

## Field Usage Examples

### Sidebar FAQ Section
```json
{
  "sidebarFAQs": {
    "content": [
      {
        "faqId": "why-health-insurance",
        "title": "Why Health Insurance?",
        "content": "Health insurance protects you financially...",
        "isExternal": false,
        "order": 1
      }
    ]
  }
}
```

### Footer Reference + Features
```json
{
  "footerFeatures": {
    "content": [
      { "featId": "feat-1", "text": "23M+ lives insured nationwide", "order": 1 }
    ]
  },
  "footerReferenceHeading": "Powered by",
  "footerReferenceName": "ABCD",
  "footerReferenceCertification": "ISO 27001:2013 certified.",
  "footerLogo": "media", //media
  "footerSideLogo": "media" //media
}
```

### Hero Slides
```json
{
  "heroSlides": {
    "content": [
      {
        "slideId": "slide-1",
        "title": "Health Insurance is now Tax-free!",
        "subtitle": "Get the same coverage at a lower premium.",
        "ctaText": "Buy now",
        "buyNowCtaDestination": "https://www.abcd.com/health-insurance/buy",
        "bannerIconPath": "media", //media
        "order": 1
      }
    ]
  }
}
```

### Quick Solution Card `[NEW v2]`
```json
{
  "quickSolutionCard": {
    "content": {
      "title": "Need quick solutions?",
      "subtitle": "Buy Pocket insurance tailored for your needs!",
      "destinationUrl": "https://google.com",
      "icon": "media", //media
    }
  }
}
```

### Disclaimer `[NEW v2]`
```json
{
  "disclaimer": {
    "content": {
      "headerTitle": "Disclaimer",
      "title": "Disclaimer",
      "content": "Aditya Birla Capital Digital Ltd (ABCDL)...",
      "doneButtonText": "Done"
    }
  }
}
```

### Manage Items `[NEW v2]`
```json
{
  "manageItems": {
    "content": [
      {
        "itemId": "ai-policy-reader",
        "icon": "media", //media
        "title": "Know your existing health policy",
        "description": "See what your policy covers in minutes",
        "highlighted": true,
        "iconSize": 26,
        "destinationUrl": "https://google.com",
        "order": 1
      },
      {
        "itemId": "my-policies",
        "icon": "media", //media
        "title": "My policies",
        "description": "View your active and past policies",
        "showChevron": true,
        "order": 2
      }
    ]
  }
}
```

### Contact Info `[NEW v2]`
```json
{
  "contactInfo": {
    "content": [
      { "itemId": "contact-number", "label": "Contact number:", "value": "1800 270 7000", "order": 1 },
      { "itemId": "email", "label": "E-mail:", "value": "care.digital@adityabirlacapital.com", "order": 2 }
    ]
  }
}
```

### Cashless Hospitalization `[NEW v2]`
```json
{
  "cashlessHospitalizationBanner": {
    "content": {
      "message": "Go cashless at any hospital for worry-free coverage.",
      "actionLabel": "List of cashless network hospitals",
      "actionUrl": "https://www.adityabirlacapital.com"
    }
  },
  "cashlessHospitalizationSections": {
    "content": [
      {
        "sectionId": "steps-to-follow",
        "title": "Steps to follow:",
        "icon": "media", //media
        "order": 1,
        "items": [
          {
            "itemId": "planned",
            "title": "For planned hospitalization -",
            "description": "Claim intimation to be done at least 48 hours before hospitalization",
            "order": 1
          }
        ]
      }
    ]
  }
}
```

### Unified Health Plans `[NEW v2]`
```json
{
  "healthplans": [
    {
      "planId": "plan-1",
      "logoUrl": "media_or_url",
      "planName": "ABHI Activ One MAX Economy",
      "ctaText": "Buy now",
      "benefits": ["HealthReturns up to 100%", "Single private AC room"],
      "showDetailsLink": true,
      "detailsLinkText": "View more details",
      "planBenefits": {
        "policyDocsLabel": "Policy docs",
        "chips": [
          { "chipId": "top-benefits", "label": "Top benefits", "benefits": [] },
          { "chipId": "covered", "label": "What's Covered?", "benefits": [] },
          { "chipId": "waiting-period", "label": "Waiting period", "timeline": [] },
          { "chipId": "eligibility-criteria", "label": "Eligibility Criteria", "benefits": [] }
        ],
        "defaultChipId": "top-benefits"
      }
    }
  ]
}
```

### Unified Health Plans Sidebar `[NEW v2]`
```json
{
  "healthPlansSidebar": {
    "viewAllPlansSidebar": {
      "pageTitle": "Home Page",
      "doneButtonText": "Done",
      "headerTitle": "",
      "subTitle": "",
      "searchPlaceholder": "Ask me anything?"
    },
    "planBenefitsSidebar": {
      "pageTitle": "Plan details",
      "headerTitle": "",
      "subTitle": "",
      "searchPlaceholder": "Ask me anything?"
    }
  }
}
```
