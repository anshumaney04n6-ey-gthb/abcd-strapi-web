# Investments Dashboard Page - Final Requirements (ID Field Refactoring)

## Overview

This document outlines the complete schema for the Investments Dashboard Page with all `id` fields renamed to appropriate `table-nameid` fields to comply with Strapi's reserved field restrictions.

---

## Content-Type: Investments Dashboard Page

**Collection Name:** `investments_dashboard_pages`  
**Plural Name:** `investments-dashboard-pages`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Renamed ID Fields)

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

## ⛔ Removed Fields (Not Required in Strapi Schema)

The following fields have been **removed** from the schema as they are resolved dynamically at runtime and should **NOT** be created in Strapi:

| Parent Section | Removed Field | Reason |
|----------------|---------------|--------|
| `calculator` | `bankOptions` | Bank options are resolved dynamically at runtime based on user inputs, not stored in CMS |
| `calculator` | `selectedPlan` | Selected plan is computed at runtime based on user selection, not a CMS field |
| `calculator` | `recommendedPlan` | Recommended plan is computed at runtime based on user inputs, not a CMS field |
| `fdGenie.depositRange` | `tickMarks` | Tick marks are handled by the frontend UI, not configurable from CMS |
| `explore` | `cards` | Cards are derived from `fdMasterTable` at runtime in the frontend, not stored separately in CMS |
| `explore` | `carousel` | Carousel config is handled by the frontend UI, not configurable from CMS |

**Removed sub-components (do NOT create in Strapi):**
- ~~`investments-dashboard.calculator-bank-option`~~ — was the sub-component for `bankOptions`
- ~~`investments-dashboard.fd-genie-tick-mark`~~ — was the sub-component for `tickMarks`
- ~~`investments-dashboard.explore-card`~~ — was the sub-component for `cards` (derived from `fdMasterTable` at runtime)

---

## Complete JSON Structure with Renamed ID Fields

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
          "bannerItemId": "item-1",
          "iconPath": "media_or_url",
          "label": "Instant withdrawal",
          "description": "available"
        }
      ],
      "cards": [
        {
          "order": 1,
          "bannerCardId": "card-1",
          "iconPath": "media_or_url",
          "title": "RBI",
          "subtitle": "Regulated"
        }
      ],
      "banners": [
        {
          "order": 1,
          "bannerFDId": "shivalik",//
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
        {
          "tenureOptionId": "1y-2y",
          "label": "1Y to 2Y",
          "value": "1y-2y"
        }
      ],
      "sliderLabels": ["1K", "1L", "10L", "50L", "1Cr"],
      "sliderMarkerValues": [1000, 100000, 1000000, 5000000, 10000000],
      "banksHeading": "Banks that fit you well",
      "selectedPlanHeading": "Your Selected Plan",
      "recommendedPlanHeading": "✨ Recommended Plan",
      "recalculateLabel": "Recalculate",
      "bookFDLabel": "Book FD",
      "banksPerSlide": 3
    },

    "fdGenie": {
      "header": "Find the FD that fits you",
      "depositRange": {
        "min": 1000,
        "max": 10000000
      },
      "tenureChips": [
        {
          "label": "1Y to 2Y",
          "minMonths": 12,
          "maxMonths": 24
        }
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
      "stats": [
        {
          "label": "Total Invested",
          "value": "₹0"
        }
      ],
      "banks": [
        {
          "portfolioBankId": "suryoday",
          "bankName": "Suryoday Bank",
          "bankLogoUrl": "media_or_url",
          "interestRate": "8.05%"
        }
      ],
      "showViewMoreButton": false
    },

    "rd": {
      "title": "Build Savings with Recurring Deposits",
      "banks": [
        {
          "rdBankId": "shivalik",
          "name": "Shivalik SF Bank",
          "logoUrl": "media_or_url",
          "description": "High Returns 🚀"
        }
      ],
      "selectedBankId": "shivalik",
      "depositOptions": [
        {
          "depositOptionId": "1k",
          "amount": 1000,
          "label": "₹1,000"
        }
      ],
      "selectedDepositAmount": 5000,
      "tenureOptions": [
        {
          "rdTenureOptionId": "1y",
          "years": 1,
          "label": "1 Year"
        }
      ],
      "selectedTenureYears": 5,
      "interestRate": 8.0,
      "maturityAmount": 365000,
      "interestEarned": 15000,
      "interestRateOptions": [
        {
          "value": "8.0",
          "label": "8.0%"
        }
      ],
      "chevronIconUrl": "media_or_url",
      "bookRDButtonText": "Book RD"
    },

    "explore": {
      "heading": "Explore FDs",
      "filters": {
        "selected": "all",
        "options": [
          {
            "filterOptionId": "all",
            "label": "All"
          },
          {
            "filterOptionId": "banks",
            "label": "Banks"
          },
          {
            "filterOptionId": "nbfcs",
            "label": "NBFCs"
          },
          {
            "filterOptionId": "tax-saver",
            "label": "Tax Saver"
          }
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
          "fdMasterTableItemId": "suryoday",
          "bankCode": "SMCBIN",
          "bankName": "Suryoday SF Bank",
          "logo": "media_or_url",
          "isBank": true,
          "isNBFC": false,
          "isTaxSaver": false,
          "highlightBadge": {
            "label": "High Returns",
            "theme": "yellow"
          },
          "subBadge": {
            "label": "optional",
            "theme": "optional"
          },
          "features": ["feature text"],
          "interestRate": {
            "prefix": "up to",
            "value": 8.05,
            "unit": "p.a"
          },
          "cta": {
            "label": "Book FD",
            "action": "BOOK_FD"
          }
        }
      ]
    },

    "highlights": {
      "title": "Special highlights",
      "showNavigation": true,
      "items": [
        {
          "highlightItemId": "rewards-fd",
          "title": "Earn rewards on your first FD",
          "description": "string",
          "ctaText": "Book Now",
          "badgeText": "optional",
          "imageSrc": "media_or_url",
          "imageAlt": "string",
          "patternImageSrc": "media_or_url",
          "background": "linear-gradient(180deg, rgba(255, 255, 255, 0.2) 0%, rgba(255, 213, 108, 0.2) 100%), #ffffff"
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
          "featureId": "feature-1",
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
          "stepId": "kyc",
          "label": "Complete KYC",
          "iconSrc": "media_or_url",
          "iconAlt": "KYC"
        }
      ],
      "requiredDocuments": [
        {
          "documentId": "doc-1",
          "label": "Aadhaar card"
        }
      ],
      "checkmarkIconSrc": "media_or_url",
      "checkmarkIconAlt": "Document required"
    },

    "learnMore": {
      "title": "Learn more about FDs",
      "showPagination": true,
      "items": [
        {
          "learnMoreItemId": "book-fd",
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
          "faqItemId": "why-fd",
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
          "faqTabId": "general",
          "label": "General",
          "defaultOpenIds": [],
          "items": [
            {
              "glFaqItemId": "general-1",
              "question": "What is a Fixed Deposit?",
              "answer": "string"
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
      "features": [
        {
          "featureId": "feature-1",
          "text": "100% Digital Journey"
        }
      ],
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

## Components Detail with Renamed ID Fields

### 1. investments-dashboard.header

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `logo.src` | media/string | No | `/logos/lob/abcd.svg` |
| `logo.alt` | string | No | `ABCD` |
| `mobileHeaderLogo` | media/string | No | - |

---

### 2. investments-dashboard.user-sidebar-assets

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
| `bannerItemId` | string | Yes | - |
| `iconPath` | media/string | No | - |
| `label` | string | No | "" |
| `description` | string | No | "" |

---

### 4. investments-dashboard.banner-fd-card
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `bannerCardId` | string | Yes | - |
| `iconPath` | media/string | No | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |

---

### 5. investments-dashboard.banner-fd-carousel-item
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `bannerFDId` | string | Yes | - |
| `amount` | string | Yes | - |
| `unit` | string | No | "p.a" |
| `prefix` | string | No | "Earn up to " |
| `heading` | string | Yes | - |
| `badge` | string | No | "" |
| `buttonLabel` | string | Yes | "Book now" |
| `items` | component[] | No | `[]` |
| `cards` | component[] | No | `[]` |

---

### 6. investments-dashboard.calculator-tenure-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `tenureOptionId` | string | Yes | - |
| `label` | string | Yes | - |
| `value` | string | Yes | - |

---

### ~~7. investments-dashboard.calculator-bank-option~~ — REMOVED

> **⛔ REMOVED:** The `bankOptions` field (and its sub-component) has been removed from the calculator section. Bank options are resolved dynamically at runtime, not from CMS.

---

### ~~8. investments-dashboard.fd-genie-tick-mark~~ — REMOVED

> **⛔ REMOVED:** The `tickMarks` field (and its sub-component) has been removed from the `fdGenie.depositRange` section. Tick marks are handled by the frontend.

---

### 9. investments-dashboard.fd-genie-tenure-chip

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `tenureChipId` | string | Yes | - |
| `label` | string | Yes | - |
| `minMonths` | number | Yes | - |
| `maxMonths` | number | Yes | - |

---

### 10. investments-dashboard.fd-genie-rate

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

### 11. investments-dashboard.portfolio-bank

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `portfolioBankId` | string | Yes | - |
| `bankName` | string | Yes | - |
| `bankLogoUrl` | media/string | No | - |
| `interestRate` | string | No | - |

---

### 12. investments-dashboard.rd-bank

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `rdBankId` | string | Yes | - |
| `name` | string | Yes | - |
| `logoUrl` | media/string | No | - |
| `description` | string | No | "" |

---

### 13. investments-dashboard.rd-deposit-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `depositOptionId` | string | Yes | - |
| `amount` | number | Yes | - |
| `label` | string | Yes | - |

---

### 14. investments-dashboard.rd-tenure-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `rdTenureOptionId` | string | Yes | - |
| `years` | number | Yes | - |
| `label` | string | Yes | - |

---

### 15. investments-dashboard.rd-interest-rate-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `interestRateOptionId` | string | Yes | - |
| `value` | string | Yes | - |
| `label` | string | Yes | - |

---

### 16. investments-dashboard.filter-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `filterOptionId` | string | Yes | - |
| `label` | string | Yes | - |

---

### 17. investments-dashboard.filter-info-banner

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `filterInfoBannerId` | string | Yes | - |
| `filterId` | string | Yes | - |
| `variant` | enum | No | "warning" |
| `noteLabel` | string | Yes | - |
| `description` | text | Yes | - |
| `iconSrc` | media/string | No | - |
| `iconAlt` | string | No | "" |

---

### 18. investments-dashboard.explore-fd-master-row

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `fdMasterTableItemId` | string | Yes | - |
| `bankCode` | string | No | "" |
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

### ~~19. investments-dashboard.explore-card~~ — REMOVED

> **⛔ REMOVED:** The `cards` field (and its sub-component) has been removed from the explore section. Cards are derived from `fdMasterTable` at runtime in the frontend.

---

### 20. investments-dashboard.highlights-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `highlightItemId` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | text | Yes | - |
| `ctaText` | string | Yes | - |
| `badgeText` | string | No | - |
| `imageSrc` | media/string | Yes | - |
| `imageAlt` | string | Yes | - |
| `patternImageSrc` | media/string | No | - |
| `background` | **text** | Yes | - |

**⚠️ IMPORTANT:** The `background` field **MUST be a Text field (not Color picker)** to accept CSS gradient values.

---

### 21. investments-dashboard.why-choose-us-feature

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `featureId` | string | Yes | - |
| `iconPath` | media/string | No | - |
| `label` | string | Yes | - |

---

### 22. investments-dashboard.book-fd-step

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `stepId` | string | Yes | - |
| `label` | string | Yes | - |
| `iconSrc` | media/string | No | - |
| `iconAlt` | string | No | "" |

---

### 23. investments-dashboard.book-fd-document

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `documentId` | number | Yes | - |
| `label` | string | Yes | - |

---

### 24. investments-dashboard.learn-more-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `learnMoreItemId` | string | Yes | - |
| `title` | string | Yes | - |
| `thumbnailSrc` | media/string | No | - |
| `thumbnailAlt` | string | No | "" |
| `ctaLabel` | string | Yes | - |
| `ctaTone` | enum | No | "warm" |
| `showPlayIcon` | boolean | No | `false` |
| `url` | string | Yes | - |

---

### 25. investments-dashboard.faq-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `faqItemId` | string | Yes | - |
| `title` | string | Yes | - |
| `icon` | media/string | No | - |
| `content` | text | No | "" |
| `isExternal` | boolean | No | `false` |
| `externalUrl` | string | No | - |

---

### 26. investments-dashboard.gl-faq-tab

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `faqTabId` | string | Yes | - |
| `label` | string | Yes | - |
| `defaultOpenIds` | string[] | No | `[]` |
| `items` | component[] | Yes | - |

---

### 27. investments-dashboard.gl-faq-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `glFaqItemId` | string | Yes | - |
| `question` | string | Yes | - |
| `answer` | text | Yes | - |

---

### 28. investments-dashboard.footer-feature

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `featureId` | string | Yes | - |
| `text` | string | Yes | - |

---

## ID Field Mapping Reference

| Component | Old Field | New Field |
|-----------|-----------|-----------|
| banner-fd-item | `id` | `bannerItemId` |
| banner-fd-card | `id` | `bannerCardId` |
| banner-fd-carousel | `id` | `bannerFDId` |
| calculator-tenure-option | `id` | `tenureOptionId` |
| ~~calculator-bank-option~~ | ~~`id`~~ | ~~`bankOptionId`~~ — REMOVED |
| ~~fd-genie-tick-mark~~ | ~~`id`~~ | ~~`tickMarkId`~~ — REMOVED |
| fd-genie-tenure-chip | `id` | `tenureChipId` |
| portfolio-bank | `id` | `portfolioBankId` |
| rd-bank | `id` | `rdBankId` |
| rd-deposit-option | `id` | `depositOptionId` |
| rd-tenure-option | `id` | `rdTenureOptionId` |
| rd-interest-rate-option | `id` | `interestRateOptionId` |
| filter-option | `id` | `filterOptionId` |
| filter-info-banner | `id` | `filterInfoBannerId` |
| explore-fd-master-row | `id` | `fdMasterTableItemId` |
| ~~explore-card~~ | ~~`id`~~ | ~~`exploreCardId`~~ — REMOVED |
| highlights-item | `id` | `highlightItemId` |
| why-choose-us-feature | `id` | `featureId` |
| book-fd-step | `id` | `stepId` |
| book-fd-document | `id` | `documentId` |
| learn-more-item | `id` | `learnMoreItemId` |
| faq-item | `id` | `faqItemId` |
| gl-faq-tab | `id` | `faqTabId` |
| gl-faq-item | `id` | `glFaqItemId` |
| footer-feature | `id` | `featureId` |

---

## Restrictions Summary Table

| Section | Component | Max Items |
|---------|-----------|-----------|
| Banner Items | banner-fd-item | 3 |
| Banner Cards | banner-fd-card | 3 |
| Banner Carousel Slides | bannerFD.banners | 3 |
| Highlights Items | highlights.items | 3 |
| Why Choose Us Features | whyChooseUs.features | 6 |
| Book FD Steps | bookFD.steps | 5 |
| Learn More Items | learnMore.items | 3 |

---

## Important Field Type Guidelines

### Background Field in Highlights Items
❌ **DO NOT use:** Color Picker field type (only accepts hex colors)  
✅ **DO use:** Text field type

The `background` field must accept full CSS strings like:
```css
linear-gradient(180deg, rgba(255, 255, 255, 0.2) 0%, rgba(255, 213, 108, 0.2) 100%), #ffffff
```

**Examples of valid background values:**
- `linear-gradient(180deg, rgba(255, 255, 255, 0.2) 0%, rgba(255, 213, 108, 0.2) 100%), #ffffff` (gradient + fallback color)
- `linear-gradient(90deg, #ff0000, #0000ff)` (simple gradient)
- `#ffffff` (single color)
- `rgba(255, 255, 255, 0.5)` (rgba color)

---




