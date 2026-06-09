# Credit Card Landing Page - Complete CMS Schema Documentation

## Content-Type: Credit Card Landing Page

**Collection Name:** `credit_card_landing_pages`  
**Singular Name:** `cards-landing-page`  
**Plural Name:** `cards-landing-page`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `subProduct` | enum | Yes | `credit` | - | Values: `credit` |
| `headerLogo` | media (image) | Yes | - | - | Main header logo |
| `headerLogoAlt` | string | No | `"ABCD Logo"` | - | Header logo alt text |
| `mobileHeaderLogo` | media (image) | No | - | - | Mobile header logo URL (string path) |
| `heroSlides` | component[] | No | - | 5 | Hero carousel slides |
| `heroCarouselAutoPlay` | boolean | No | `true` | - | Enable hero carousel auto-play |
| `heroCarouselAutoPlayInterval` | integer | No | `5000` | - | Auto-play interval in ms |
| `heroCarouselShowArrows` | boolean | No | `true` | - | Show prev/next arrows |
| `heroCarouselShowIndicators` | boolean | No | `true` | - | Show carousel dot/bar indicators |
| `heroCarouselIndicatorStyle` | enum | No | `bars` | - | Values: `bars`, `dots` |
| `heroBackgroundVariant` | enum | No | `light` | - | Values: `default`, `light` |
| `heroShowSeparator` | boolean | No | `true` | - | Show separator below hero |
| `heroProductHighlighters` | component[] | No | - | 5 | Product highlight badge items |
| `poweredByImage` | media (image) | No | - | - | Powered-by partner logo in hero |
| `poweredByAlt` | string | No | `"Credilio"` | - | Alt text for powered-by image |
| `poweredByShieldIcon` | media (image) | No | - | - | Shield icon alongside powered-by |
| `widgetHeaderBadgeText` | string | No | `"Join 50L+ customers"` | - | Badge text above widget title |
| `widgetTitle` | string | No | `"Apply for Credit Card"` | - | Widget form title |
| `widgetMobileInputPlaceholder` | string | No | `"Enter Mobile Number"` | - | Placeholder for mobile input |
| `widgetConsentLabel` | string | No | `"I agree to the Terms & Conditions and Privacy Policy"` | - | Full consent label text |
| `widgetTermsText` | string | No | `"Terms & Conditions"` | - | Terms link anchor text |
| `widgetTermsUrl` | string | No | `"/terms"` | - | Terms link URL |
| `widgetPrivacyText` | string | No | `"Privacy Policy"` | - | Privacy link anchor text |
| `widgetPrivacyUrl` | string | No | `"/privacy"` | - | Privacy link URL |
| `widgetCtaText` | string | No | `"Get Started"` | - | Widget submit button text |
| `widgetHeaderBadgeIcon` | string | No | `"/icons/medal-badge.svg"` | - | Icon path for widget header badge *(in fallback, not yet consumed by LandingClient)* |
| `widgetMobileHelperText` | string | No | `"OTP will be sent to verify your number"` | - | Helper text below mobile input *(in fallback, not yet consumed by LandingClient)* |
| `smartFeaturesTitle` | string | No | `"Smart Features. Real Impact."` | - | Smart features section title |
| `smartFeaturesAutoScroll` | boolean | No | `true` | - | Enable auto-scroll for feature cards |
| `smartFeaturesAutoScrollInterval` | integer | No | `4000` | - | Auto-scroll interval in ms |
| `smartFeaturesPauseOnHover` | boolean | No | `false` | - | Pause auto-scroll on hover |
| `smartFeaturesShowDots` | boolean | No | `false` | - | Show pagination dots |
| `smartFeaturesCards` | component[] | No | - | 5 | Feature card items |
| `offeringsTitle` | string | No | `"Our Offerings"` | - | Offerings section title |
| `offeringsBackgroundImage` | media (image) | No | - | - | Background image for offerings section |
| `offeringsItems` | component[] | No | - | 6 | Individual offering items |
| `ownACreditCardTitle` | string | No | `"Own a credit card in just"` | - | Steps section main title |
| `ownACreditCardHighlightedTitle` | string | No | `"4 steps"` | - | Highlighted part of the steps title |
| `ownACreditCardHighlightedTitleUnderlineImage` | media (image) | No | - | - | Underline/border SVG below highlighted title *(in fallback, not yet passed as prop in LandingClient)* |
| `ownACreditCardSteps` | component[] | No | - | 6 | Steps items |
| `faqTitle` | string | No | `"Frequently Asked Questions"` | - | FAQ section title |
| `faqAllowMultiple` | boolean | No | `false` | - | Allow multiple FAQ items open simultaneously |
| `faqItems` | component[] | No | - | 10 | FAQ items |
| `appPromoBannerAppLabel` | string | No | `"The ABCD app"` | - | App label text |
| `appPromoBannerTitle` | string | No | `"Everything Finance\nas simple as\nABCD"` | - | Banner headline (desktop) |
| `appPromoBannerMobileTitle` | string | No | `"Everything Finance\nas simple as\nABCD"` | - | Banner headline (mobile) |
| `appPromoBannerSubtitle` | string | No | `"Download the ABCD app and start doing more with\nyour money everyday"` | - | Banner subtext (desktop) |
| `appPromoBannerMobileSubtitle` | string | No | `"Download the ABCD app and start doing more with your money everyday"` | - | Banner subtext (mobile) |
| `appPromoBannerFromLabel` | string | No | `"From the house of"` | - | "From the house of" label |
| `appPromoBannerHouseLogo` | media (image) | No | - | - | House/group logo image |
| `appPromoBannerHouseLogoAlt` | string | No | `"ABCD Group Logo"` | - | Alt text for house logo |
| `appPromoBannerQrCode` | media (image) | No | - | - | QR code image |
| `appPromoBannerQrAlt` | string | No | `"Scan to download ABCD app"` | - | Alt text for QR code |
| `appPromoBannerPhoneImage` | media (image) | No | - | - | Phone mockup image |
| `appPromoBannerPhoneImageAlt` | string | No | `"ABCD app preview on phone"` | - | Alt text for phone image |
| `appPromoBannerCtaVisibility` | enum | No | `all` | - | Values: `all`, `mobile`, `desktop` |
| `appPromoBannerCompanyInfoLayout` | enum | No | `row` | - | Company info layout direction. Values: `row`, `column` |
| `appPromoBannerCtaButtons` | component[] | No | - | 3 | App store CTA buttons |
| `footerReferenceHeading` | string | No | `"Powered by"` | - | Footer reference heading |
| `footerReferenceName` | string | No | `"ABCD"` | - | Footer reference entity name |
| `footerReferenceLogo` | media (image) | No | - | - | Footer reference logo |
| `footerFeatures` | component[] | No | - | 6 | Footer feature badge items |
| `footerSideImage` | media (image) | No | - | - | Footer side decorative image |
| `footerSideImageAlt` | string | No | `"Stack of credit cards"` | - | Alt text for footer side image |

---

## API Endpoints

### Base URL
```
/api/cards-landing-page
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/cards-landing-page` | List all landing page |
| GET | `/api/cards-landing-page/:id` | Get single landing page |
| POST | `/api/cards-landing-page` | Create landing page |
| PUT | `/api/cards-landing-page/:id` | Update landing page |
| DELETE | `/api/cards-landing-page/:id` | Delete landing page |

### Query Parameters
```
?populate=*
?filters[subProduct][$eq]=credit
```

### cURL Example

```bash
curl -s \

  'http://localhost:1337/api/cards-landing-page?filters[subProduct][$eq]=credit&populate=*'
```

---

## Complete JSON Structure with enabled/order fields

> **Note:** `enabled` is at section level. `order` is inside each array item to control item ordering within that array.
>
> **Field names shown below are EXACT Strapi field names as defined in schema.**

```json
{
  "data": {
    "subProduct": "credit",

    "headerLogo": { "media_object" },
    "headerLogoAlt": "ABCD Logo",
    "mobileHeaderLogo": { "media_object" },

    "heroSlides": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "title": "string (required)",
          "subtitle": "string",
          "background": { "media_object (required)" }
        }
      ]
    },

    "heroCarouselAutoPlay": true,
    "heroCarouselAutoPlayInterval": 5000,
    "heroCarouselShowArrows": true,
    "heroCarouselShowIndicators": true,
    "heroCarouselIndicatorStyle": "bars",
    "heroBackgroundVariant": "light",
    "heroShowSeparator": true,

    "heroProductHighlighters": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "text": "string (required)",
          "showIcon": true
        }
      ]
    },

    "poweredByImage": { "media_object" },
    "poweredByAlt": "Credilio",
    "poweredByShieldIcon": { "media_object" },

    "widgetHeaderBadgeText": "Join 50L+ customers",
    "widgetTitle": "Apply for Credit Card",
    "widgetMobileInputPlaceholder": "Enter Mobile Number",
    "widgetConsentLabel": "I agree to the Terms & Conditions and Privacy Policy",
    "widgetTermsText": "Terms & Conditions",
    "widgetTermsUrl": "/terms",
    "widgetPrivacyText": "Privacy Policy",
    "widgetPrivacyUrl": "/privacy",
    "widgetCtaText": "Get Started",
    "widgetHeaderBadgeIcon": "/icons/medal-badge.svg",
    "widgetMobileHelperText": "OTP will be sent to verify your number",

    "smartFeaturesTitle": "Smart Features. Real Impact.",
    "smartFeaturesAutoScroll": true,
    "smartFeaturesAutoScrollInterval": 4000,
    "smartFeaturesPauseOnHover": false,
    "smartFeaturesShowDots": false,
    "smartFeaturesCards": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "stepNumber": "string (required)",
          "heading": "string (required)",
          "description": "text (required)",
          "ctaLabel": "string",
          "image": { "media_object" },
          "mobileImage": { "media_object" },
          "floatingLabels": []
        }
      ]
    },

    "offeringsTitle": "Our Offerings",
    "offeringsBackgroundImage": { "media_object" },
    "offeringsItems": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "heading": "string (required)",
          "description": "text (required)",
          "icon": { "media_object (required)" }
        }
      ]
    },

    "ownACreditCardTitle": "Own a credit card in just",
    "ownACreditCardHighlightedTitle": "4 steps",
    "ownACreditCardHighlightedTitleUnderlineImage": { "media_object" },
    "ownACreditCardSteps": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "title": "string (required)",
          "description": "text (required)",
          "icon": { "media_object" }
        }
      ]
    },

    "faqTitle": "Frequently Asked Questions",
    "faqAllowMultiple": false,
    "faqItems": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "question": "string (required)",
          "answer": "text (required)"
        }
      ]
    },

    "appPromoBannerAppLabel": "The ABCD app",
    "appPromoBannerTitle": "Everything Finance\nas simple as\nABCD",
    "appPromoBannerMobileTitle": "Everything Finance\nas simple as\nABCD",
    "appPromoBannerSubtitle": "Download the ABCD app and start doing more with\nyour money everyday",
    "appPromoBannerMobileSubtitle": "Download the ABCD app and start doing more with your money everyday",
    "appPromoBannerFromLabel": "From the house of",
    "appPromoBannerHouseLogo": { "media_object" },
    "appPromoBannerHouseLogoAlt": "ABCD Group Logo",
    "appPromoBannerQrCode": { "media_object" },
    "appPromoBannerQrAlt": "Scan to download ABCD app",
    "appPromoBannerPhoneImage": { "media_object" },
    "appPromoBannerPhoneImageAlt": "ABCD app preview on phone",
    "appPromoBannerCtaVisibility": "all",
    "appPromoBannerCompanyInfoLayout": "row",
    "appPromoBannerCtaButtons": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "label": "string (required)",
          "link": "string (required)",
          "icon": { "media_object (required)" },
          "iconAlt": "string (required)",
          "analyticsId": "string",
          "analyticsCTAText": "string"
        }
      ]
    },

    "footerReferenceHeading": "Powered by",
    "footerReferenceName": "ABCD",
    "footerReferenceLogo": { "media_object" },
    "footerFeatures": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "text": "string (required)"
        }
      ]
    },
    "footerSideImage": { "media_object" },
    "footerSideImageAlt": "Stack of credit cards"
  }
}
```

---

## Components Detail

### 1. cards-landing.hero-slide
**Max Items:** 5

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | - |
| `background` | media (image) | Yes | - |
| `order` | integer | Yes | - |

---

### 2. cards-landing.product-highlighter
**Max Items:** 5

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `text` | string | Yes | - |
| `showIcon` | boolean | No | `true` |
| `order` | integer | Yes | - |

---

### 3. cards-landing.smart-feature-card
**Max Items:** 5

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `stepNumber` | string | Yes | - |
| `heading` | string | Yes | - |
| `description` | text | Yes | - |
| `ctaLabel` | string | No | `"Apply now"` |
| `image` | media (image) | No | - |
| `mobileImage` | media (image) | No | - |
| `floatingLabels` | json | No | `[]` |
| `order` | integer | Yes | - |

---

### 4. cards-landing.offering-item
**Max Items:** 6

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `heading` | string | Yes | - |
| `description` | text | Yes | - |
| `icon` | media (image) | Yes | - |
| `order` | integer | Yes | - |

---

### 5. cards-landing.own-a-card-step
**Max Items:** 6

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | text | Yes | - |
| `icon` | media (image) | No | - |
| `order` | integer | Yes | - |

---

### 6. cards-landing.faq-item
**Max Items:** 10

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `question` | string | Yes | - |
| `answer` | text | Yes | - |
| `order` | integer | Yes | - |

---

### 7. cards-landing.app-promo-cta-button
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `label` | string | Yes | - |
| `link` | string | Yes | - |
| `icon` | media (image) | Yes | - |
| `iconAlt` | string | Yes | - |
| `analyticsId` | string | No | - |
| `analyticsCTAText` | string | No | - |
| `order` | integer | Yes | - |

---

### 8. cards-landing.footer-feature
**Max Items:** 6

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `text` | string | Yes | - |
| `order` | integer | Yes | - |

---

## Restrictions Summary Table

| Section | Component | Max Items |
|---------|-----------|-----------|
| Hero Slides | hero-slide | 5 |
| Hero Product Highlighters | product-highlighter | 5 |
| Smart Feature Cards | smart-feature-card | 5 |
| Offering Items | offering-item | 6 |
| Own a Card Steps | own-a-card-step | 6 |
| FAQ Items | faq-item | 10 |
| App Promo CTA Buttons | app-promo-cta-button | 3 |
| Footer Features | footer-feature | 6 |

---

## Widget Section Defaults

| Field | Default Value |
|-------|---------------|
| `widgetHeaderBadgeText` | `"Join 50L+ customers"` |
| `widgetTitle` | `"Apply for Credit Card"` |
| `widgetMobileInputPlaceholder` | `"Enter Mobile Number"` |
| `widgetConsentLabel` | `"I agree to the Terms & Conditions and Privacy Policy"` |
| `widgetTermsText` | `"Terms & Conditions"` |
| `widgetTermsUrl` | `"/terms"` |
| `widgetPrivacyText` | `"Privacy Policy"` |
| `widgetPrivacyUrl` | `"/privacy"` |
| `widgetCtaText` | `"Get Started"` |
| `widgetHeaderBadgeIcon` | `"/icons/medal-badge.svg"` |
| `widgetMobileHelperText` | `"OTP will be sent to verify your number"` |

---

## Hero Section Defaults

| Field | Default Value |
|-------|---------------|
| `heroCarouselAutoPlay` | `true` |
| `heroCarouselAutoPlayInterval` | `5000` |
| `heroCarouselShowArrows` | `true` |
| `heroCarouselShowIndicators` | `true` |
| `heroCarouselIndicatorStyle` | `"bars"` |
| `heroBackgroundVariant` | `"light"` |
| `heroShowSeparator` | `true` |
| `poweredByAlt` | `"Credilio"` |

---

## Smart Features Section Defaults

| Field | Default Value |
|-------|---------------|
| `smartFeaturesTitle` | `"Smart Features. Real Impact."` |
| `smartFeaturesAutoScroll` | `true` |
| `smartFeaturesAutoScrollInterval` | `4000` |
| `smartFeaturesPauseOnHover` | `false` |
| `smartFeaturesShowDots` | `false` |

---


---

## FAQ Section Defaults

| Field | Default Value |
|-------|---------------|
| `faqTitle` | `"Frequently Asked Questions"` |
| `faqAllowMultiple` | `false` |

---

## Own a Credit Card Section Defaults

| Field | Default Value |
|-------|---------------|
| `ownACreditCardTitle` | `"Own a credit card in just"` |
| `ownACreditCardHighlightedTitle` | `"4 steps"` |
| `ownACreditCardHighlightedTitleUnderlineImage` | *(media: `steps-border.svg`)* |

---

## Footer Section Defaults

| Field | Default Value |
|-------|---------------|
| `footerReferenceHeading` | `"Powered by"` |
| `footerReferenceName` | `"ABCD"` |
| `footerSideImageAlt` | `"Stack of credit cards"` |

---

## App Promo Banner Defaults

| Field | Default Value |
|-------|---------------|
| `appPromoBannerAppLabel` | `"The ABCD app"` |
| `appPromoBannerTitle` | `"Everything Finance\nas simple as\nABCD"` |
| `appPromoBannerFromLabel` | `"From the house of"` |
| `appPromoBannerHouseLogoAlt` | `"ABCD Group Logo"` |
| `appPromoBannerQrAlt` | `"Scan to download ABCD app"` |
| `appPromoBannerPhoneImageAlt` | `"ABCD app preview on phone"` |
| `appPromoBannerCtaVisibility` | `"all"` |
| `appPromoBannerCompanyInfoLayout` | `"row"` |

---

## API Response Example

> **Note:** Strapi returns data as a **flat object** — no `attributes` wrapper.
> Media fields are flat `{ id, documentId, url, mime }`. A `documentId` string is present alongside numeric `id`.

```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123xyz",
      "subProduct": "credit",
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z",
      "publishedAt": "2024-01-01T00:00:00.000Z",

      "headerLogoAlt": "ABCD Logo",

      "heroCarouselAutoPlay": true,
      "heroCarouselAutoPlayInterval": 5000,
      "heroCarouselShowArrows": true,
      "heroCarouselShowIndicators": true,
      "heroCarouselIndicatorStyle": "bars",
      "heroBackgroundVariant": "light",
      "heroShowSeparator": true,
      "poweredByAlt": "Credilio",

      "widgetHeaderBadgeText": "Join 50L+ customers",
      "widgetTitle": "Apply for Credit Card",
      "widgetMobileInputPlaceholder": "Enter Mobile Number",
      "widgetConsentLabel": "I agree to the Terms & Conditions and Privacy Policy",
      "widgetTermsText": "Terms & Conditions",
      "widgetTermsUrl": "/terms",
      "widgetPrivacyText": "Privacy Policy",
      "widgetPrivacyUrl": "/privacy",
      "widgetCtaText": "Get Started",
      "widgetHeaderBadgeIcon": "/icons/medal-badge.svg",
      "widgetMobileHelperText": "OTP will be sent to verify your number",

      "smartFeaturesTitle": "Smart Features. Real Impact.",
      "smartFeaturesAutoScroll": true,
      "smartFeaturesAutoScrollInterval": 4000,
      "smartFeaturesPauseOnHover": false,
      "smartFeaturesShowDots": false,

      "offeringsTitle": "Our Offerings",

      "ownACreditCardTitle": "Own a credit card in just",
      "ownACreditCardHighlightedTitle": "4 steps",
      "ownACreditCardHighlightedTitleUnderlineImage": { "id": 24, "documentId": "media-024", "url": "/uploads/steps-border.svg", "mime": "image/svg+xml" },

      "faqTitle": "Frequently Asked Questions",
      "faqAllowMultiple": false,

      "appPromoBannerAppLabel": "The ABCD app",
      "appPromoBannerTitle": "Everything Finance\nas simple as\nABCD",
      "appPromoBannerMobileTitle": "Everything Finance\nas simple as\nABCD",
      "appPromoBannerSubtitle": "Download the ABCD app and start doing more with\nyour money everyday",
      "appPromoBannerMobileSubtitle": "Download the ABCD app and start doing more with your money everyday",
      "appPromoBannerFromLabel": "From the house of",
      "appPromoBannerHouseLogoAlt": "ABCD Group Logo",
      "appPromoBannerQrAlt": "Scan to download ABCD app",
      "appPromoBannerPhoneImageAlt": "ABCD app preview on phone",
      "appPromoBannerCtaVisibility": "all",
      "appPromoBannerCompanyInfoLayout": "row",

      "footerReferenceHeading": "Powered by",
      "footerReferenceName": "ABCD",
      "footerSideImageAlt": "Stack of credit cards",

      "headerLogo": { "id": 1, "documentId": "media-001", "url": "/uploads/abcd.svg", "mime": "image/svg+xml", "width": 200, "height": 50 },
      "mobileHeaderLogo": { "id": 2, "documentId": "media-002", "url": "/uploads/abcd_mobile.svg", "mime": "image/svg+xml", "width": 120, "height": 40 },

      "heroSlides": [
        {
          "id": 1,
          "order": 1,
          "title": "Explore 100+ Credit Cards from Leading Banks",
          "subtitle": "Compare features, check eligibility and apply digitally in minutes.",
          "background": { "id": 3, "documentId": "media-003", "url": "/uploads/hero-card.png", "mime": "image/png" }
        }
      ],

      "heroProductHighlighters": [
        { "id": 1, "order": 1, "text": "100% Digital Process", "showIcon": true },
        { "id": 2, "order": 2, "text": "Personalised Recommendations", "showIcon": true },
        { "id": 3, "order": 3, "text": "No Paperwork", "showIcon": false }
      ],

      "poweredByImage": { "id": 4, "documentId": "media-004", "url": "/uploads/credit-logo.png", "mime": "image/png" },
      "poweredByShieldIcon": { "id": 5, "documentId": "media-005", "url": "/uploads/powered-by-shield-icon.png", "mime": "image/png" },

      "smartFeaturesCards": [
        {
          "id": 1,
          "order": 1,
          "stepNumber": "01",
          "heading": "Personalised Recommendations",
          "description": "Get card suggestions matched to your income & credit profile.",
          "ctaLabel": "Apply now",
          "image": { "id": 6, "documentId": "media-006", "url": "/uploads/ellipses-bg.png", "mime": "image/png" },
          "mobileImage": { "id": 7, "documentId": "media-007", "url": "/uploads/mobile_ellipses.png", "mime": "image/png" },
          "floatingLabels": []
        },
        {
          "id": 2,
          "order": 2,
          "stepNumber": "02",
          "heading": "100% Digital Process",
          "description": "End-to-end online journey, no branch visits, no delays.",
          "ctaLabel": "Apply now",
          "image": { "id": 8, "documentId": "media-008", "url": "/uploads/digital.png", "mime": "image/png" },
          "mobileImage": { "id": 9, "documentId": "media-009", "url": "/uploads/mobile_digital.png", "mime": "image/png" },
          "floatingLabels": []
        },
        {
          "id": 3,
          "order": 3,
          "stepNumber": "03",
          "heading": "No Paperwork",
          "description": "Complete your application digitally, without any paperwork.",
          "ctaLabel": "Apply now",
          "image": { "id": 10, "documentId": "media-010", "url": "/uploads/no-paperwork.png", "mime": "image/png" }, 
          "mobileImage": null,
          "floatingLabels": []
        }
      ],

      "offeringsBackgroundImage": { "id": 11, "documentId": "media-011", "url": "/uploads/offerings-background.png", "mime": "image/png" },
      "offeringsItems": [
        {
          "id": 1,
          "order": 1,
          "heading": "Eligibility-Based Credit Card Options",
          "description": "View cards you're most likely to get approved for.",
          "icon": { "id": 12, "documentId": "media-012", "url": "/uploads/eligibility.svg", "mime": "image/svg+xml" }
        },
        {
          "id": 2,
          "order": 2,
          "heading": "FD-Backed Credit Cards",
          "description": "Hassle-free options for users building or improving their credit score.",
          "icon": { "id": 13, "documentId": "media-013", "url": "/uploads/fd-backed.svg", "mime": "image/svg+xml" }
        },
        {
          "id": 3,
          "order": 3,
          "heading": "Wide Selection Across Categories",
          "description": "Choose from 100+ cards covering rewards, cashback, travel, fuel, lifestyle, and premium benefits.",
          "icon": { "id": 14, "documentId": "media-014", "url": "/uploads/wide-selection.svg", "mime": "image/svg+xml" }
        },
        {
          "id": 4,
          "order": 4,
          "heading": "Multiple Lending Partners",
          "description": "Access cards from 9+ leading banks through a single platform.",
          "icon": { "id": 15, "documentId": "media-015", "url": "/uploads/lending-partners.svg", "mime": "image/svg+xml" }
        }
      ],

      "ownACreditCardSteps": [
        {
          "id": 1,
          "order": 1,
          "title": "Tell us about yourself",
          "description": "Sign in with your existing credentials or register quickly as a new user to get started.",
          "icon": { "id": 16, "documentId": "media-016", "url": "/uploads/own-a-credit-card-step-1.png", "mime": "image/png" }
        },
        {
          "id": 2,
          "order": 2,
          "title": "Choose your perfect card",
          "description": "Fill in important details like income, employment type and preferences.",
          "icon": { "id": 17, "documentId": "media-017", "url": "/uploads/own-a-credit-card-step-2.png", "mime": "image/png" }
        },
        {
          "id": 3,
          "order": 3,
          "title": "Fill in a few more details",
          "description": "Browse through available plans, compare features and premiums, and select the right card.",
          "icon": { "id": 18, "documentId": "media-018", "url": "/uploads/own-a-credit-card-step-3.png", "mime": "image/png" }
        },
        {
          "id": 4,
          "order": 4,
          "title": "Verify and finish up",
          "description": "Complete your KYC verification and submit your application digitally.",
          "icon": { "id": 19, "documentId": "media-019", "url": "/uploads/own-a-credit-card-step-4.png", "mime": "image/png" }
        }
      ],

      "faqItems": [
        {
          "id": 1,
          "order": 1,
          "question": "What is the Credit Card journey inside the ABCL App?",
          "answer": "This journey enables you to explore, compare, and apply for credit cards from multiple banks/NBFCs directly within the ABCL App. User can choose from 100+ Credit Cards via 9+ Lenders."
        },
        {
          "id": 2,
          "order": 2,
          "question": "What types of credit cards are available?",
          "answer": "We offer a wide range of credit cards including rewards cards, cashback cards, travel cards, fuel cards, lifestyle cards, and premium credit cards from leading banks and NBFCs."
        },
        {
          "id": 3,
          "order": 3,
          "question": "How is eligibility checked?",
          "answer": "Our system uses advanced algorithms to check your eligibility based on your income, credit score, employment status, and other financial parameters without impacting your credit score."
        },
        {
          "id": 4,
          "order": 4,
          "question": "Will checking eligibility impact my credit score?",
          "answer": "No, our eligibility check uses a soft inquiry which does not impact your credit score. Only hard inquiries during the final application stage may have a minimal impact."
        }
      ],

      "appPromoBannerCtaButtons": [
        {
          "id": 1,
          "order": 1,
          "label": "App Store",
          "link": "https://apps.apple.com/",
          "icon": { "id": 20, "documentId": "media-020", "url": "/uploads/apple.svg", "mime": "image/svg+xml" },
          "iconAlt": "Apple App Store",
          "analyticsId": "CC_LANDING_APP_DOWNLOAD_BADGE_CLICK",
          "analyticsCTAText": "app_store"
        },
        {
          "id": 2,
          "order": 2,
          "label": "Google Play",
          "link": "https://play.google.com/store",
          "icon": { "id": 21, "documentId": "media-021", "url": "/uploads/google.svg", "mime": "image/svg+xml" },
          "iconAlt": "Google Play Store",
          "analyticsId": "CC_LANDING_APP_DOWNLOAD_BADGE_CLICK",
          "analyticsCTAText": "google_play"
        }
      ],

      "footerReferenceLogo": { "id": 22, "documentId": "media-022", "url": "/uploads/abcd-logo.svg", "mime": "image/svg+xml" },
      "footerFeatures": [
        { "id": 1, "order": 1, "text": "100% Digital Process" },
        { "id": 2, "order": 2, "text": "No Paperwork" },
        { "id": 3, "order": 3, "text": "Personalised Recommendations" },
        { "id": 4, "order": 4, "text": "Trusted banks" }
      ],
      "footerSideImage": { "id": 23, "documentId": "media-023", "url": "/uploads/credit-cards-stack.png", "mime": "image/png" }
    }
  ],
  "meta": { "pagination": { "page": 1, "pageSize": 25, "pageCount": 1, "total": 1 } }
}
```

---

## Populate Query for Full Response

```
/api/cards-landing-page?filters[subProduct][$eq]=credit&populate[headerLogo]=*&populate[mobileHeaderLogo]=*&populate[heroSlides][populate]=*&populate[heroProductHighlighters]=*&populate[poweredByImage]=*&populate[poweredByShieldIcon]=*&populate[smartFeaturesCards][populate]=*&populate[offeringsBackgroundImage]=*&populate[offeringsItems][populate]=*&populate[ownACreditCardSteps][populate]=*&populate[faqItems]=*&populate[appPromoBannerHouseLogo]=*&populate[appPromoBannerQrCode]=*&populate[appPromoBannerPhoneImage]=*&populate[appPromoBannerCtaButtons][populate]=*&populate[footerReferenceLogo]=*&populate[footerFeatures]=*&populate[footerSideImage]=*
```

Or use deep populate:
```
/api/cards-landing-page?filters[subProduct][$eq]=credit&populate=deep
```

---

## Sections Enabled Flags

The `sectionsEnabled` object in the frontend component controls section visibility. These can optionally be exposed as CMS boolean fields per section:

| Section Flag | Default | Description |
|---|---|---|
| `heroSection` | `true` | Main hero carousel section |
| `productHighlighters` | `true` | Product badge highlights in hero |
| `heroSeparator` | `true` | Divider below hero |
| `smartFeatures` | `true` | Smart feature cards carousel |
| `offerings` | `true` | Our Offerings grid |
| `ownACreditCardSection` | `true` | Step-by-step guide section |
| `faq` | `true` | FAQ accordion section |
| `appPromoBanner` | `true` | App download promotional banner |

---