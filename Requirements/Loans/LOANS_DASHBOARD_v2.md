# Loans CMS Requirements v2 - Personal Loan dashboard Page

**Date:** 2026-04-29  
**Status:** IMPLEMENTED  
**Collection Type:** `personal-loan-dashboard-pages`

---

## 1. Components

### 1.1 Dashboard Page Sections
 
| Key | Component | Purpose |
|-----|-----------|---------|
| `header` | `dashboard-header` | Logo configuration |
| `hero` | `dashboard-hero` | Hero section with CTA, eligibilityCriteria, highrlight content |
| `referralBanner` | `dashboard-referal` | How to referal |
| `ratesAndCharges` | `dashboard-rate-and-charge` | Rate and charges |
| `getStarted` | `dashboard-get-started` | Get Started |
| `benefitBlock` | `dashboard-benefit-block` | Benefits |
| `trustedPartners ` | `dashboard-trusted-partners` | Trusted partners section |
| `faq` | `dashboard-faq` | FAQ section with tabs |
| `footer` | `dashboard-footer` | Footer with reference details |
| `exclusiveEmployeeBanner` | `dashboard-exclusive-employee-banner` | Exclusive Employee Banner section |
| `exclusiveBanner Banner` | `dashboard-exclusive-banner` | Exclusive Banner section |

### 1.2 Reusable Components

| Component | Used In |
|-----------|---------|
| `logo` | `header.logo` |
| `eligibility-criteria` | `hero.eligibilityCriteria[]` |
| `highlighterContent` | `hero.highlighter-content` |
| `dashboard-highlighter-content` | `hero.highlighterContent.newJourney`, `hero.highlighterContent.resumeJourney`, `hero.highlighterContent.preApprovedOffer`, `hero.highlighterContent.exclusiveOffer`, `hero.highlighterContent.progress`, `hero.highlighterContent.success`, `hero.highlighterContent.failed`, `hero.highlighterContent.rejected` |
| `assets` | `referralBanner.assets` |
| `rate-and-charges-item` | `ratesAndCharges.item[]` |
| `get-started-item` | `fetStarted.items[]` |
| `benefit-block-item` | `benefitBlock.items[]` |
| `trusted-partner-column` | `trustedPartners.columns[]` |
| `faq-tab` | `faq.tabs[]` |
| `eligibility-item` | `eligibility.items[]` |
| `security-feature` | `securityFeatures.items[]` |
| `side-logo-details` | `footer.sideLogoDetails` |
| `reference-details` | `footer.referenceDetails` |
| `footer-feature` | `footer.features[]` |



---

## 2. Schema

### 2.1 `header`

| Field | Type | Required |
|-------|------|:--------:|
| `logo` | logo | Yes |

**logo:**
| Field | Type | Required |
|-------|------|:--------:|
| `src` | string | Yes |
| `alt` | string | Yes |
| `size` | integer | Yes |

### 2.2 `hero`

| Field | Type | Required |
|-------|------|:--------:|
| `ctaText` | string | Yes |
| `eligibilityCriteria` | eligibility-criteria[] | No |
| `highlighterContent` | highlighter-content | No |

**eligibility-criteria:**
| Field | Type | Required |
|-------|------|:--------:|
| `label` | string | Yes |
| `value` | string | Yes |


**highlighter-content:**
| Field | Type | Required |
|-------|------|:--------:|
| `newJourney` | dashboard-highlighter-content | No |
| `resumeJourney` | dashboard-highlighter-content | No |
| `preApprovedOffer` | dashboard-highlighter-content | No |
| `exclusiveOffer` | dashboard-highlighter-content | No |
| `progress` | dashboard-highlighter-content | No |
| `success` | dashboard-highlighter-content | No |
| `failed` | dashboard-highlighter-content | No |
| `rejected` | dashboard-highlighter-content | No |

**dashboard-highlighter-content:**
| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `subtitle` | string | Yes |
| `ctaText` | string | Yes |
| `illustrationSrc` | string | Yes |



### 2.3 `referralBanner`

| Field | Type | Required |
|-------|------|:--------:|
| `isVisible` | boolean | No |
| `title` | string | Yes |
| `subtitle` | string | Yes |
| `termsText` | string | Yes |
| `assets` | assets | No |

**assets:**
| Field | Type | Required |
|-------|------|:--------:|
| `treasureChest` | string | No |
| `goldCoin` | string | No |
| `chevron` | string | No |


### 2.4 `ratesAndCharges`
referralBanner ratesAndCharges
| Field | Type | Required |
|-------|------|:--------:|
| `text` | string | Yes |
| `items` | rate-and-charges-item[] | Yes |
| `cardBackground` | string | No |
| `cardBorder` | string | No |

**rate-and-charges-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `title` | string | Yes |
| `description` | string | Yes |
| `image` | string | No |
| `imageAlt` | string | No |

### 2.5 `inlineInfoBanner`

| Field | Type | Required |
|-------|------|:--------:|
| `isVisible` | boolean | No |
| `text` | string | Yes |
| `highlightedText` | string | No |
| `iconSrc` | string | Yes |
| `iconAlt` | string | No |
| `chevronSrc` | string | No |
| `chevronAlt` | string | No |
| `backgroundColor` | string | No |
| `borderColor` | string | No |
| `textColor` | string | No |
| `highlightedTextColor` | string | No |

### 2.6 `getStarted`

| Field | Type | Required |
|-------|------|:--------:|
| `headingPrefix` | string | Yes |
| `headingHighlight` | string | Yes |
| `headingSuffix` | string | Yes |
| `items` | get-started-item[] | Yes |
| `cardBackground` | string | No |
| `cardBorder` | string | No |

**get-started-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `title` | string | Yes |
| `description` | string | Yes |
| `image` | string | No |
| `imageAlt` | string | No |

### 2.7 `calculator`

| Field | Type | Required |
|-------|------|:--------:|
| `sectionTitle` | string | Yes |
| `title` | string | Yes |
| `description` | string | Yes |
| `ctaText` | string | Yes |
| `illustrationIcon` | string | Yes |
| `ctaAriaLabel` | string | No |

### 2.8 `benefitBlock`

| Field | Type | Required |
|-------|------|:--------:|
| `items` | benefit-block-item[] | No |
| `footerText` | string | Yes |
| `footerLeftIcon` | string | Yes |
| `footerRightIcon` | string | Yes |

**benefit-block-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `icon` | string | Yes |
| `text` | string | Yes |

### 2.9 `trustedPartners`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | benefit-block-item[] | Yes |
| `subtitle` | string | Yes |
| `columns` | column[] | No |

**column:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `name` | string | Yes |
| `logoUrl` | string | Yes |
| `highlighted` | boolean | No |

### 2.10 `faq`

| Field | Type | Required |
|-------|------|:--------:|
| `tabs` | faq-tab[] | Yes |

**faq-tab:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `label` | string | Yes |
| `content` | string | Yes |
| `icon` | string | Yes |

### 2.11 `footer`

| Field | Type | Required |
|-------|------|:--------:|
| `referenceDetails` | reference-details | Yes |
| `sideLogoDetails` | side-logo-Details | Yes |
| `features` | feature[] | Yes |

**reference-details:**
| Field | Type | Required |
|-------|------|:--------:|
| `heading` | string | Yes |
| `name` | string | Yes |
| `logo` | string | Yes |
| `certification` | string | Yes |

**side-logo-details:**
| Field | Type | Required |
|-------|------|:--------:|
| `image` | string | Yes |
| `alt` | string | Yes |

**feature:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `text` | string | Yes |

### 2.12 `exclusiveEmployeeBanner`

| Field | Type | Required |
|-------|------|:--------:|
| `imageSrc` | string | Yes |
| `mobileImageSrc` | string | No |
| `imageAlt` | string | Yes |

### 2.13 `exclusiveBanner`
 
| Field | Type | Required |
|-------|------|:--------:|
| `imageSrc` | string | Yes |
| `mobileImageSrc` | string | No |
| `imageAlt` | string | Yes |


## 3. Expected API Response

**Endpoint:** `GET /api/loans-dashboard-pages?filters[subProduct][$eq]=personal&populate=*`


```json
{
  "data": {
    "header": {
      "logo": {
        "src": "/logos/lob/abcd.svg",
        "alt": "ABCD Logo",
        "size": 40
      }
    },
    "hero": {
      "ctaText": "Apply Now",
      "eligibilityCriteria": [
        {
          "label": "Age:",
          "value": "21 to 65 years"
        },
        {
          "label": "Income:",
          "value": "Min. ₹30,000/m"
        },
        {
          "label": "Residency:",
          "value": "PAN India"
        }
      ],
      "highlighterContent": {
        "newJourney": {
          "title": "Get instant loans up to ₹ 15 Lakhs",
          "subtitle": "Instant Disbursal, ZERO Documentation, Flexible EMIs",
          "ctaText": "Apply now",
          "illustrationSrc": "/assets/personal-loan/icons/handcoins.svg"
        },
        "resumeJourney": {
          "title": "Welcome back, pick up where you left",
          "subtitle": "Resume your application in minutes and get faster disbursal",
          "ctaText": "Resume",
          "illustrationSrc": "/assets/personal-loan/icons/resume-app.svg"
        },
        "preApprovedOffer": {
          "title": "You have a pre-approved offer",
          "subtitle": "Check out your pre-approved offer -",
          "ctaText": "Check Offer",
          "illustrationSrc": "/assets/personal-loan/icons/handcoins.svg"
        },
        "exclusiveOffer": {
          "title": "Staff exclusive personal loan offer",
          "subtitle": "Check out your staff offer -",
          "ctaText": "Apply Now",
          "illustrationSrc": "/assets/personal-loan/icons/exclusive.svg"
        },
        "progress": {
          "title": "Your disbursement is in progress",
          "subtitle": "We are processing your loan disbursement. This usually completes shortly.",
          "ctaText": "Check Status",
          "illustrationSrc": "/assets/personal-loan/icons/progress-app.svg"
        },
        "success": {
          "title": "Loan disbursed successfully",
          "subtitle": "Your loan amount has been credited to your account.",
          "ctaText": "Download Documents",
          "illustrationSrc": "/assets/personal-loan/icons/disb-success.svg"
        },
        "failed": {
          "title": "Disbursement failed",
          "subtitle": "We could not complete disbursement this time. Please retry or check details.",
          "ctaText": "Check Status",
          "illustrationSrc": "/assets/personal-loan/icons/disb-failed.svg"
        },
        "rejected": {
          "title": "Application rejected",
          "subtitle": "Your application could not be approved based on current checks.",
          "ctaText": "Check Status",
          "illustrationSrc": "/assets/personal-loan/icons/disb-failed.svg"
        }
      }
    },
    "referralBanner": {
      "isVisible": true,
      "title": "Help friends start their gold journey",
      "subtitle": "Refer friends & earn ₹250 in ABCD Coins.",
      "termsText": "*T&C",
      "assets": {
        "treasureChest": "/assets/personal-loan/referralBanner/treasure-chest.png",
        "goldCoin": "/assets/personal-loan/referralBanner/gold-coin.png",
        "chevron": "/assets/personal-loan/referralBanner/double-chevron.png"
      }
    },
    "ratesAndCharges": {
      "text": "Rates and charges",
      "items": [
        {
          "id": "loan-amount",
          "title": "Loan Amount",
          "description": "Min. ₹25,000 and Max. 5 Lakhs",
          "image": "/assets/personal-loan/icons/goldhand.webp"
        },
        {
          "id": "repayment-tenure",
          "title": "Repayment Tenure",
          "description": "12 months to 36 months",
          "image": "/assets/personal-loan/icons/percentage.webp"
        },
        {
          "id": "rate-of-interest",
          "title": "Rate of Interest",
          "description": "10.99% to 30% per annum",
          "image": "/assets/personal-loan/icons/percentage.webp"
        },
        {
          "id": "processing-fees",
          "title": "Processing Fees",
          "description": "1.18% - 4.13% of Loan amount incl. GST.",
          "image": "/assets/personal-loan/icons/file.webp"
        }
      ],
      "cardBackground": "linear-gradient(90deg, rgba(255, 213, 108, 0.2) 0%, rgba(124, 34, 121, 0.05) 100%), linear-gradient(90deg, #fff 0%, #fff 100%)",
      "cardBorder": "1px solid rgba(124, 34, 121, 0.2)"
    },
    "inlineInfoBanner": {
      "isVisible": true,
      "highlightedText": "Get a free credit score!",
      "text": " Auto track your loans & credit card reports",
      "iconSrc": "/assets/personal-loan/icons/creditcard.svg",
      "iconAlt": "Info",
      "chevronSrc": "/assets/personal-loan/referralBanner/double-chevron.png"
    },
    "getStarted": {
      "headingPrefix": "Only ",
      "headingHighlight": "3 steps",
      "headingSuffix": ", and you get the money!",
      "items": [
        {
          "id": "basic-details",
          "title": "Provide Basic Details",
          "description": "Choose your amount, pay online, and instantly own certified digital gold backed by real assets.",
          "image": "/assets/personal-loan/icons/document.svg"
        },
        {
          "id": "choose-offers",
          "title": "Choose & Apply Loan Offers",
          "description": "Choose your amount, pay online, and instantly own certified digital gold backed by real assets.",
          "image": "/assets/personal-loan/icons/filter.svg"
        },
        {
          "id": "get-cash",
          "title": "Get instant Cash in Bank",
          "description": "Choose your amount, pay online, and instantly own certified digital gold backed by real assets.",
          "image": "/assets/personal-loan/icons/money.svg"
        }
      ],
      "cardBackground": "linear-gradient(90deg, rgba(255, 213, 108, 0.2) 0%, rgba(124, 34, 121, 0.05) 100%), linear-gradient(90deg, #fff 0%, #fff 100%)",
      "cardBorder": "1px solid rgba(124, 34, 121, 0.2)"
    },
    "calculator": {
      "sectionTitle": "Financial tools & calculators",
      "title": "EMI for your Personal Loan",
      "description": "Calculate your potential EMI in seconds.",
      "ctaText": "Calculate",
      "illustrationIcon": "/assets/personal-loan/icons/calculator.png",
      "ctaAriaLabel": "Calculate your EMI"
    },
    "benefitBlock": {
      "items": [
        {
          "id": "instant-offer",
          "icon": "/assets/personal-loan/icons/pl-benefit-bolt.svg",
          "text": "Get\nInstant Offer"
        },
        {
          "id": "no-paperwork",
          "icon": "/assets/personal-loan/icons/pl-benefit-laptop-cloud.svg",
          "text": "No Paperwork\nRequired"
        },
        {
          "id": "lowest-interest",
          "icon": "/assets/personal-loan/icons/pl-benefit-three-steps.svg",
          "text": "Lowest\ninterest rate"
        }
      ],
      "footerText": "1 Lakh+ people got a personal loan in just a few clicks",
      "footerLeftIcon": "/assets/personal-loan/icons/pl-benefit-star.svg",
      "footerRightIcon": "/assets/personal-loan/icons/pl-benefit-star.svg"
    },
    "trustedPartners": {
      "title": "Our Trusted Lending Partners",
      "subtitle": "",
      "columns": [
        {
          "id": "partner-1",
          "name": "ICICI Lombard",
          "logoUrl": "/assets/personal-loan/icons/icic.svg"
        },
        {
          "id": "partner-2",
          "name": "ACKO",
          "logoUrl": "/assets/personal-loan/icons/acko.svg"
        },
        {
          "id": "partner-3",
          "name": "Digit",
          "logoUrl": "/assets/personal-loan/icons/digit.svg"
        },
        {
          "id": "partner-4",
          "name": "Tata AIG",
          "logoUrl": "/assets/personal-loan/icons/tata.svg"
        },
        {
          "id": "partner-5",
          "name": "Bajaj Allianz General",
          "logoUrl": "/assets/personal-loan/icons/general.svg"
        }
      ]
    },
    "faq": {
      "tabs": [
        {
          "id": "why-digital-gold",
          "label": "Why Digital Gold?",
          "content": "Digital gold offers secure investment with instant buying and selling.",
          "icon": "/assets/sidebar-faq/why-digital-gold.webp"
        },
        {
          "id": "how-digital-gold-works",
          "label": "How Digital gold works?",
          "content": "Start investing in gold digitally with just a few clicks.",
          "icon": "/assets/sidebar-faq/how-it-works.webp"
        },
        {
          "id": "other-questions",
          "label": "Other questions?",
          "content": "Find answers to all your questions about digital gold.",
          "icon": "/assets/sidebar-faq/other-questions.webp"
        }
      ]
    },
    "footer": {
      "referenceDetails": {
        "heading": "Powered by",
        "name": "Aditya Birla Capital Digital Ltd",
        "logo": "/assets/personal-loan/icons/abcfooter.svg",
        "certification": "Aditya Birla Capital Digital Ltd"
      },
      "sideLogoDetails": {
        "image": "/assets/personal-loan/icons/goldbag.svg",
        "alt": "Decorative footer waves"
      },
      "features": [
        {
          "id": "instant-offer",
          "text": "Get Instant Offer"
        },
        {
          "id": "no-paperwork",
          "text": "No Paperwork"
        },
        {
          "id": "low-interest",
          "text": "Lowest interest rate"
        }
      ]
    },
    "exclusiveEmployeeBanner": {
      "imageSrc": "",
      "mobileImageSrc": "",
      "imageAlt": "Exclusive Employee Offer"
    },
    "exclusiveBanner": {
      "imageSrc": "",
      "mobileImageSrc": "",
      "imageAlt": "Exclusive Offer"
    }
  }
}