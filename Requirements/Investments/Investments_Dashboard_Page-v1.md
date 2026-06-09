# Investments Dashboard Page - Complete Schema Documentation

## Content-Type: Investments Dashboard Page

**Collection Name:** `investments_dashboard_pages`  
**Singular Name:** `investments-dashboard-page`  
**Plural Name:** `investments-dashboard-pages`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `subProduct` | enum | Yes | `fixed-deposits` | - | Product variant filter key |
| `partner` | string | No | `default` | - | Optional partner-specific variant |
| `header` | component | No | fallback | - | Dashboard header logo configuration |
| `userSidebarAssets` | component | No | fallback | - | Icon/illustration assets for user profile sidebar |
| `bannerFD` | component | No | fallback | - | Top FD hero banner/carousel block |
| `resumeKYC` | component | No | fallback | - | Resume KYC strip configuration |
| `calculator` | component | No | fallback | - | Calculator UI text/options block |
| `fdGenie` | component | No | fallback | - | FD Genie input model |
| `fdGenieRates` | component[] | No | fallback | - | FD provider/rate matrix |
| `portfolio` | component | No | fallback | - | Portfolio section base labels/flags |
| `rd` | component | No | fallback | - | Recurring Deposit section configuration |
| `explore` | component | No | fallback | - | Explore FD list, filters, cards, carousel |
| `highlights` | component | No | fallback | - | Special highlights cards |
| `whyChooseUs` | component | No | fallback | - | Why choose us panel |
| `bookFD` | component | No | fallback | - | Book FD steps and documents |
| `learnMore` | component | No | fallback | - | Learn-more resources cards |
| `faq` | component | No | fallback | - | Sidebar FAQ entries |
| `glFaq` | component | No | fallback | - | Main GLFAQ section (tabbed FAQ block) |
| `faqItems` | component[] | No | - | - | Optional flat FAQ array (legacy/alternate input) |
| `defaultOpenFaqIds` | json | No | `[]` | - | Optional FAQ default-open ids (legacy/alternate input) |
| `footer` | component | No | fallback | - | Footer details/features/graphics |

---

## API Endpoints

### Base URL
```
/api/investments-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/investments-dashboard-pages` | List all dashboard pages |
| GET | `/api/investments-dashboard-pages/:id` | Get single dashboard page |
| POST | `/api/investments-dashboard-pages` | Create dashboard page |
| PUT | `/api/investments-dashboard-pages/:id` | Update dashboard page |
| DELETE | `/api/investments-dashboard-pages/:id` | Delete dashboard page |

### Query Parameters
```
?populate=*
?filters[subProduct][$eq]=fixed-deposits
?filters[partner][$eq]=default
```

---

## Complete JSON Structure with enabled/order fields

> **Note:** Keep this structure aligned with DashboardClient and fallback content.  
> **Note:** For repeatable arrays, use `order` in each item when ordering matters.

```json
{
  "data": {
    "subProduct": "fixed-deposits",
    "partner": "default",

    "header": {
      "logo": {
        "src": "media_or_url",
        "alt": "ABCD"
      },
      "mobileHeaderLogo": "media_or_url"
    },

    "userSidebarAssets": {
      "iconProfile": "media_or_url",
      "iconInfo": "media_or_url",
      "iconLogout": "media_or_url",
      "logoFooter": "media_or_url",
      "logoutIllustration": "media_or_url",
      "otpIllustration": "media_or_url"
    },

    "bannerFD": {
      "amount": "8.05",
      "unit": "p.a",
      "prefix": "Earn up to ",
      "heading": "Suryoday Small Finance Bank",
      "badge": "Popular Choice",
      "buttonLabel": "Book now",
      "logoImagePath": "media_or_url",
      "bannerImagePath": "media_or_url",
      "backgroundImagePath": "media_or_url",
      "badgeIconPath": "media_or_url",
      "chevronIconPath": "media_or_url",
      "decorativeIconPath": "media_or_url",
      "gradientColor1": "rgba(...)",
      "gradientColor2": "rgba(...)",
      "items": [
        {
          "order": 1,
          "id": "item-1",
          "iconPath": "media_or_url",
          "label": "Instant withdrawal",
          "description": "available"
        }
      ],
      "cards": [
        {
          "order": 1,
          "id": "card-1",
          "iconPath": "media_or_url",
          "title": "RBI",
          "subtitle": "Regulated"
        }
      ],
      "banners": [
        {
          "order": 1,
          "amount": "8.75",
          "unit": "p.a",
          "prefix": "Earn up to ",
          "heading": "Shivalik Small Finance Bank",
          "badge": "Highest Interest Rate",
          "buttonLabel": "Book now",
          "items": [],
          "cards": []
        }
      ]
    },

    "resumeKYC": {
      "heading": "Almost there! Complete your KYC.",
      "supportingText": "Just add your PAN details to get started.",
      "resumeButtonText": "Resume",
      "progressClockSrc": "media_or_url",
      "closeIconSrc": "media_or_url"
    },

    "calculator": {
      "heading": "Find the FD that fits you",
      "depositLabel": "Deposit amount (in ₹)",
      "depositPlaceholder": "Enter amount",
      "tenureLabel": "Investment Tenure",
      "checkboxLabel": "I am a senior citizen",
      "buttonLabel": "Search Banks",
      "currencySymbol": "₹",
      "depositMin": 0,
      "depositMax": 10000000,
      "depositStep": 1000,
      "defaultDeposit": 100000,
      "defaultTenure": "1y-2y",
      "tenureOptions": [
        { "id": "1y-2y", "label": "1Y to 2Y", "value": "1y-2y" }
      ],
      "sliderLabels": ["1K", "1L", "10L", "50L", "1Cr"],
      "sliderMarkerValues": [1000, 100000, 1000000, 5000000, 10000000],
      "banksHeading": "Banks that fit you well",
      "selectedPlanHeading": "Your Selected Plan",
      "recommendedPlanHeading": "✨ Recommended Plan",
      "recalculateLabel": "Recalculate",
      "bookFDLabel": "Book FD",
      "banksPerSlide": 3,
      "bankOptions": [
        {
          "id": "shivalik",
          "name": "Shivalik Bank",
          "logoUrl": "media_or_url",
          "tenure": "1 Year",
          "rate": "8.75%",
          "isSelected": true,
          "rank": 1,
          "compoundingValue": 4
        }
      ],
      "selectedPlan": {
        "investedAmount": "₹1.00L",
        "corpus": "₹1.09L",
        "tenure": "1 Year",
        "yield": "8.75%"
      },
      "recommendedPlan": {
        "investedAmount": "₹1.00L",
        "corpus": "₹2.57L",
        "tenure": "5 Years",
        "yield": "8.75%"
      }
    },

    "fdGenie": {
      "header": "Find the FD that fits you",
      "depositRange": {
        "min": 1000,
        "max": 10000000,
        "tickMarks": [{ "label": "1K", "value": 1000 }]
      },
      "tenureChips": [
        { "label": "1Y to 2Y", "minMonths": 12, "maxMonths": 24 }
      ],
      "seniorCitizenLabel": "Senior citizen",
      "womanLabel": "Woman",
      "ctaLabel": "Get my Best FD Options"
    },

    "fdGenieRates": [
      {
        "providerName": "Shivalik SF Bank",
        "bankLogo": "media_or_url",
        "tenureMonths": 12,
        "regularRate": 8.75,
        "seniorCitizenRate": 9.0,
        "womanRate": 8.85,
        "compoundingType": "Quarterly",
        "compoundingValue": 4,
        "rbiRegulated": true
      }
    ],

    "portfolio": {
      "portfolioValue": "₹0",
      "portfolioValueLabel": "Current Portfolio Value",
      "stats": [{ "label": "Total Invested", "value": "₹0" }],
      "banks": [],
      "showViewMoreButton": false
    },

    "rd": {
      "title": "Build Savings with Recurring Deposits",
      "banks": [
        {
          "id": "shivalik",
          "name": "Shivalik SF Bank",
          "logoUrl": "media_or_url",
          "description": "High Returns"
        }
      ],
      "selectedBankId": "shivalik",
      "depositOptions": [{ "id": "1k", "amount": 1000, "label": "₹1,000" }],
      "selectedDepositAmount": 5000,
      "tenureOptions": [{ "id": "1y", "years": 1, "label": "1 Year" }],
      "selectedTenureYears": 5,
      "interestRate": 8.0,
      "maturityAmount": 365000,
      "interestEarned": 15000,
      "interestRateOptions": [{ "value": "8.0", "label": "8.0%" }],
      "chevronIconUrl": "media_or_url",
      "bookRDButtonText": "Book RD"
    },

    "explore": {
      "heading": "Explore FDs",
      "filters": {
        "selected": "all",
        "options": [
          { "id": "all", "label": "All" },
          { "id": "banks", "label": "Banks" },
          { "id": "nbfcs", "label": "NBFCs" },
          { "id": "tax-saver", "label": "Tax Saver" }
        ]
      },
      "filterInfoBanners": [
        {
          "filterId": "nbfcs",
          "variant": "warning",
          "noteLabel": "NBFCs",
          "description": "string",
          "iconSrc": "media_or_url",
          "iconAlt": "string"
        }
      ],
      "fdMasterTable": [
        {
          "id": "suryoday",
          "bankName": "Suryoday SF Bank",
          "logo": "media_or_url",
          "isBank": true,
          "isNBFC": false,
          "isTaxSaver": false,
          "highlightBadge": { "label": "High Returns", "theme": "yellow" },
          "subBadge": { "label": "optional", "theme": "optional" },
          "features": ["feature text"],
          "interestRate": { "prefix": "up to", "value": 8.05, "unit": "p.a" },
          "cta": { "label": "Book FD", "action": "BOOK_FD" }
        }
      ],
      "cards": [
        {
          "id": "suryoday",
          "bankName": "Suryoday SF Bank",
          "logo": "media_or_url",
          "categoryIds": ["banks"],
          "highlightBadge": { "label": "High Returns", "theme": "yellow" },
          "features": ["feature text"],
          "interestRate": { "prefix": "up to", "value": 8.05, "unit": "p.a" },
          "cta": { "label": "Book FD", "action": "BOOK_FD" }
        }
      ],
      "carousel": {
        "enabled": true,
        "visibleCards": 4,
        "showIndicator": true
      }
    },

    "highlights": {
      "title": "Special highlights",
      "showNavigation": true,
      "items": [
        {
          "id": "rewards-fd",
          "title": "Earn rewards on your first FD",
          "description": "string",
          "ctaText": "Book Now",
          "badgeText": "optional",
          "imageSrc": "media_or_url",
          "imageAlt": "string",
          "patternImageSrc": "media_or_url",
          "background": "linear-gradient(...)"
        }
      ]
    },

    "whyChooseUs": {
      "title": "Why choose us?",
      "headerIconPath": "media_or_url",
      "headerIconAlt": "Why choose us",
      "isOpenByDefault": true,
      "columns": 2,
      "features": [
        {
          "id": "feature-1",
          "iconPath": "media_or_url",
          "label": "Higher interest rate"
        }
      ]
    },

    "bookFD": {
      "title": "Book an FD in 5 easy steps",
      "highlightedText": "5 easy steps",
      "rectangleLineIconSrc": "media_or_url",
      "stopLineIconSrc": "media_or_url",
      "steps": [
        {
          "id": "kyc",
          "label": "Complete KYC",
          "iconSrc": "media_or_url",
          "iconAlt": "KYC"
        }
      ],
      "requiredDocuments": [
        { "id": 1, "label": "Aadhaar card" }
      ],
      "checkmarkIconSrc": "media_or_url",
      "checkmarkIconAlt": "Document required"
    },

    "learnMore": {
      "title": "Learn more about FDs",
      "showPagination": true,
      "items": [
        {
          "id": "book-fd",
          "title": "How to Book FD?",
          "thumbnailSrc": "media_or_url",
          "thumbnailAlt": "optional",
          "ctaLabel": "Watch",
          "ctaTone": "warm",
          "showPlayIcon": true,
          "url": "https://..."
        }
      ]
    },

    "faq": {
      "items": [
        {
          "id": "why-fd",
          "title": "Why Fixed Deposit?",
          "icon": "media_or_url",
          "content": "string",
          "isExternal": false,
          "externalUrl": "optional"
        }
      ],
      "defaultExpandedIds": []
    },

    "glFaq": {
      "title": "Frequently Asked Questions",
      "tabs": [
        {
          "id": "general",
          "label": "General",
          "defaultOpenIds": ["what-is-fd"],
          "items": [
            {
              "id": "what-is-fd",
              "question": "What is a Fixed Deposit?",
              "answer": "A Fixed Deposit (FD) is a financial instrument that allows you to invest a lump sum amount for a fixed period at a predetermined interest rate."
            }
          ]
        }
      ]
    },

    "footer": {
      "referenceDetails": {
        "heading": "Powered by",
        "name": "ABCD"
      },
      "features": [{ "id": "feature-1", "text": "100% Digital Journey" }],
      "sideLogoDetails": {
        "image": "media_or_url",
        "alt": "FD Footer"
      },
      "waveLineUrl": "media_or_url"
    }
  }
}
```

---

## Components Detail

### 1. investments-dashboard.header

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `logo.src` | media/string | No | `/logos/lob/abcd.svg` |
| `logo.alt` | string | No | `ABCD` |
| `mobileHeaderLogo` | media/string | No | - |

---

### 2. investments-dashboard.user-sidebar-assets

> Icon/illustration asset paths for the user profile sidebar panel.

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `iconProfile` | media/string | No | `/assets/sidebar/icon-profile.svg` |
| `iconInfo` | media/string | No | `/assets/sidebar/icon-info.svg` |
| `iconLogout` | media/string | No | `/assets/sidebar/icon-logout.svg` |
| `logoFooter` | media/string | No | `/assets/sidebar/logo-abcd-footer.png` |
| `logoutIllustration` | media/string | No | `/assets/sidebar/logout-illustration.png` |
| `otpIllustration` | media/string | No | `/assets/profile/otp-illustration.png` |

---

### 3. investments-dashboard.banner-fd-item
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `iconPath` | media/string | No | - |
| `label` | string | No | "" |
| `description` | string | No | "" |

---

### 4. investments-dashboard.banner-fd-card
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `iconPath` | media/string | No | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |

---

### 5. investments-dashboard.fd-genie-rate

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `providerName` | string | Yes | - |
| `bankLogo` | media/string | No | - |
| `tenureMonths` | number | Yes | - |
| `regularRate` | number | Yes | - |
| `seniorCitizenRate` | number | Yes | - |
| `womanRate` | number | Yes | - |
| `compoundingType` | string | No | - |
| `compoundingValue` | number | Yes | - |
| `rbiRegulated` | boolean | No | `true` |

---

### 6. investments-dashboard.explore-fd-master-row

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `bankName` | string | Yes | - |
| `logo` | media/string | No | - |
| `isBank` | boolean | No | `true` |
| `isNBFC` | boolean | No | `false` |
| `isTaxSaver` | boolean | No | `false` |
| `highlightBadge` | component | No | null |
| `subBadge` | component | No | null |
| `features` | string[] | No | `[]` |
| `interestRate` | component | Yes | - |
| `cta` | component | No | `{ "label": "Book FD", "action": "BOOK_FD" }` |

---

### 7. investments-dashboard.faq-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `icon` | media/string | No | - |
| `content` | text | No | "" |
| `isExternal` | boolean | No | `false` |
| `externalUrl` | string | No | - |

---

### 8. investments-dashboard.gl-faq

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | No | "Frequently Asked Questions" |
| `tabs` | component[] | Yes | - |

Sub-component: `gl-faq-tab`

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `label` | string | Yes | - |
| `defaultOpenIds` | string[] | No | `[]` |
| `items` | component[] | Yes | - |

Sub-component: `gl-faq-item`

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `question` | string | Yes | - |
| `answer` | text | Yes | - |

---

## Restrictions Summary Table

| Section | Component | Max Items |
|---------|-----------|-----------|
| Banner Items | banner-fd-item | 3 |
| Banner Cards | banner-fd-card | 3 |
| Banner Carousel Slides | bannerFD.banners | 3 |
| Why Choose Us Features | whyChooseUs.features | 6 |
| Book FD Steps | bookFD.steps | 5 |
| Learn More Items | learnMore.items | 3 |
| Highlights Items | highlights.items | 3 |

---

## Transform Compatibility Notes

This schema is designed to work with the dashboard transformer in content/index.ts:

1. Numeric-keyed objects like `{ "0": {...}, "1": {...} }` are normalized to arrays.
2. Legacy wrappers like `{ content: [...] }` are unwrapped.
3. `faq.items` and flat `faqItems` are both accepted.
4. `faq.defaultExpandedIds` and `defaultOpenFaqIds` are both accepted.
5. `whyChooseUs.features` supports `label/text` and `iconPath/icon` aliases.
6. `glFaq` is passed through as-is and merged with fallback when missing.

---

## Fallback Content Mapping

> `fallback.ts` path -> Strapi field name

| Fallback Path | Strapi Field Name |
|---------------|-------------------|
| `header` | `header` |
| `userSidebarAssets` | `userSidebarAssets` |
| `bannerFD` | `bannerFD` |
| `resumeKYC` | `resumeKYC` |
| `calculator` | `calculator` |
| `fdGenie` | `fdGenie` |
| `fdGenieRates` | `fdGenieRates` |
| `portfolio` | `portfolio` |
| `rd` | `rd` |
| `explore` | `explore` |
| `highlights` | `highlights` |
| `whyChooseUs` | `whyChooseUs` |
| `bookFD` | `bookFD` |
| `learnMore` | `learnMore` |
| `faq` | `faq` |
| `glFaq` | `glFaq` |
| `faqItems` | `faqItems` (alternate) |
| `defaultOpenFaqIds` | `defaultOpenFaqIds` (alternate) |
| `footer` | `footer` |

---

## API Response Example (Actual Strapi Response)

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "subProduct": "fixed-deposits",
        "partner": "default",
        "createdAt": "2024-01-01T00:00:00.000Z",
        "updatedAt": "2024-01-01T00:00:00.000Z",
        "publishedAt": "2024-01-01T00:00:00.000Z",

        "header": {
          "logo": {
            "data": {
              "id": 1,
              "attributes": { "url": "/uploads/abcd-logo.svg" }
            }
          },
          "mobileHeaderLogo": {
            "data": {
              "id": 2,
              "attributes": { "url": "/uploads/abcd-logo-mobile.svg" }
            }
          }
        },

        "userSidebarAssets": {
          "id": 1,
          "iconProfile": "/assets/sidebar/icon-profile.svg",
          "iconInfo": "/assets/sidebar/icon-info.svg",
          "iconLogout": "/assets/sidebar/icon-logout.svg",
          "logoFooter": "/assets/sidebar/logo-abcd-footer.png",
          "logoutIllustration": "/assets/sidebar/logout-illustration.png",
          "otpIllustration": "/assets/profile/otp-illustration.png"
        },

        "bannerFD": {
          "id": 1,
          "amount": "8.05",
          "unit": "p.a",
          "prefix": "Earn up to ",
          "heading": "Suryoday Small Finance Bank",
          "badge": "Popular Choice",
          "buttonLabel": "Book now",
          "gradientColor1": "rgba(255, 200, 0, 0.8)",
          "gradientColor2": "rgba(255, 150, 0, 0.6)",
          "logoImagePath": "/uploads/suryoday-logo.svg",
          "items": [
            { "id": 1, "label": "Instant withdrawal", "description": "available" }
          ],
          "cards": [
            { "id": 1, "title": "RBI", "subtitle": "Regulated" }
          ],
          "banners": [
            {
              "id": 1,
              "amount": "8.75",
              "unit": "p.a",
              "prefix": "Earn up to ",
              "heading": "Shivalik Small Finance Bank",
              "badge": "Highest Interest Rate",
              "buttonLabel": "Book now"
            }
          ]
        },

        "resumeKYC": {
          "id": 1,
          "heading": "Almost there! Complete your KYC.",
          "supportingText": "Just add your PAN details to get started.",
          "resumeButtonText": "Resume"
        },

        "calculator": {
          "id": 1,
          "heading": "Find the FD that fits you",
          "depositLabel": "Deposit amount (in ₹)",
          "depositMin": 0,
          "depositMax": 10000000,
          "defaultDeposit": 100000,
          "defaultTenure": "1y-2y",
          "tenureOptions": [
            { "id": 1, "id_": "1y-2y", "label": "1Y to 2Y", "value": "1y-2y" }
          ]
        },

        "fdGenieRates": [
          {
            "id": 1,
            "providerName": "Shivalik SF Bank",
            "tenureMonths": 12,
            "regularRate": 8.75,
            "seniorCitizenRate": 9.0,
            "womanRate": 8.85,
            "compoundingType": "Quarterly",
            "compoundingValue": 4,
            "rbiRegulated": true
          }
        ],

        "whyChooseUs": {
          "id": 1,
          "title": "Why choose us?",
          "headerIconPath": "/uploads/why-choose-us.svg",
          "isOpenByDefault": true,
          "columns": 2,
          "features": [
            { "id": 1, "iconPath": "/uploads/icon-1.svg", "label": "Higher interest rate" }
          ]
        },

        "faq": {
          "id": 1,
          "items": [
            {
              "id": 1,
              "id_": "why-fd",
              "title": "Why Fixed Deposit?",
              "content": "Fixed deposits offer guaranteed returns...",
              "isExternal": false
            }
          ],
          "defaultExpandedIds": ["why-fd"]
        },

        "footer": {
          "id": 1,
          "referenceDetails": {
            "heading": "Powered by",
            "name": "ABCD"
          },
          "features": [
            { "id": 1, "text": "100% Digital Journey" },
            { "id": 2, "text": "Get your FD Receipt instantly" }
          ],
          "sideLogoDetails": {
            "image": "/uploads/fd-footer-case.png",
            "alt": "FD Footer"
          },
          "waveLineUrl": "/uploads/fd-footer-lines.svg"
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

## Populate Query for Full Response

```
/api/investments-dashboard-pages?
filters[subProduct][$eq]=fixed-deposits&
filters[partner][$eq]=default&
populate=deep
```

---

## Source Files

| File | Purpose |
|------|---------|
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/fallback.ts` | Default fallback dashboard content and type contract |
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/index.ts` | CMS fetcher + transformer (`transformDashboardCMSResponse`) |
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/page.tsx` | Server component entry point |
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/DashboardClient.tsx` | Client dashboard renderer (`TDDashboard`) |
