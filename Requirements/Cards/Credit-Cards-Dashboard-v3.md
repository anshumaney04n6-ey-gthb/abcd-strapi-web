# Credit Card Dashboard - Complete CMS Schema Documentation

## Content-Type: Credit Card Dashboard

**Collection Name:** `credit_card_dashboards`  
**Singular Name:** `credit-card-dashboard`  
**Plural Name:** `cards-dashboard-page`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `subProduct` | enum | Yes | `credit` | - | Values: `credit` |
| `benefitsSectionTitle` | string | No | `"One platform, many benefits"` | - | Left panel: many benefits section heading |
| `factsSectionTitle` | string | No | `"Some random facts"` | - | Left panel: random facts section heading |
| `disclaimerText` | string | No | `"To refer to the Terms & Conditions"` | - | Disclaimer body text |
| `disclaimerLinkText` | string | No | `"Tap here"` | - | Disclaimer CTA link text |
| `carouselPanelCycleInterval` | integer | No | `60000` | - | How long (ms) each carousel panel is displayed |
| `carouselAnimationDuration` | integer | No | `1500` | - | Carousel transition animation duration in ms |
| `navigationTabs` | component[] | No | - | 6 | Top nav tabs (Invest, Insure, Loans, My Track, …) |
| `offeringsTitle` | string | No | `"Our offerings"` | - | Right panel: offerings section heading |
| `offerings` | component[] | No | - | 6 | Right panel offering cards |
| `stillExploringTitle` | string | No | `"Still Exploring?"` | - | Right panel: still exploring section heading |
| `stillExploringSubtitle` | string | No | `"Apply for a credit card with our partner banks"` | - | Right panel: still exploring section subtitle |
| `stillExploringCards` | component[] | No | - | - | Inline bank cards embedded in the dashboard. Queried individually by `bankId` via populate filters on the dashboard endpoint. |
| `ownStepTitlePrefix` | string | No | `"Own a credit card in just"` | - | Right panel: own step module title prefix |
| `ownStepSteps` | component[] | No | - | 6 | Right panel own step items |
| `learnAboutUsText` | string | No | `"How did you learn about us?"` | - | Right panel: learn about us label |
| `learnAboutUsArrowIcon` | media (image) | No | - | - | Arrow icon for learn about us row |
| `learnAboutUsArrowIconAlt` | string | No | `"Arrow"` | - | Alt text for arrow icon |
| `manyBenefits` | component[] | No | - | 6 | Left panel benefit cards |
| `randomFactsIconUrl` | media (image) | No | - | - | Left panel: icon shown with random facts |
| `randomFactsIconAlt` | string | No | `"Credit fact icon"` | - | Alt text for random facts icon |
| `randomFacts` | component[] | No | - | 10 | Left panel random fact items |
| `poweredByBannerText` | string | No | `"Powered by"` | - | Left panel: powered-by banner label |
| `poweredByBannerPartnerLogo` | media (image) | No | - | - | Partner logo in powered-by banner |
| `poweredByBannerPartnerLogoAlt` | string | No | `"ABCD Logo"` | - | Alt text for partner logo |
| `poweredByBannerDecorativeIcon` | media (image) | No | - | - | Shield/decorative icon in powered-by banner |
| `carouselPanels` | component[] | No | - | 10 | Centre carousel panels (unsecured / secured / bank) |
| `securedBenefits` | component[] | No | - | 10 | Secured card benefits sidebar items |
| `unsecuredBenefits` | component[] | No | - | 10 | Unsecured card benefits sidebar items |

---

## API Endpoints

### Base URL
```
/api/cards-dashboard-page
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/cards-dashboard-page` | List all dashboard configs |
| GET | `/api/cards-dashboard-page/:id` | Get single dashboard config |
| POST | `/api/cards-dashboard-page` | Create dashboard config |
| PUT | `/api/cards-dashboard-page/:id` | Update dashboard config |
| DELETE | `/api/cards-dashboard-page/:id` | Delete dashboard config |

### Query Parameters
```
?populate=*
?filters[subProduct][$eq]=credit
```

### cURL Example

```bash
curl -s \
  'http://localhost:1337/api/cards-dashboard-page?filters[subProduct][$eq]=credit&populate=*'
```

---

## Complete JSON Structure with enabled/order fields

> **Note:** `enabled` is at section level. `order` is inside each array item to control item ordering.

```json
{
  "data": {
    "subProduct": "credit",

    "benefitsSectionTitle": "One platform, many benefits",
    "factsSectionTitle": "Some random facts",
    "disclaimerText": "To refer to the Terms & Conditions",
    "disclaimerLinkText": "Tap here",

    "carouselPanelCycleInterval": 60000,
    "carouselAnimationDuration": 1500,

    "navigationTabs": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "label": "string (required)",
          "menuItems": {
            "enabled": true,
            "content": [
              {
                "order": 1,
                "id": "string (required)",
                "title": "string (required)",
                "description": "string",
                "icon": { "media_object (required)" },
                "navigateToUrl": "string (required)"
              }
            ]
          },
          "promoBanners": {
            "enabled": true,
            "content": [
              {
                "order": 1,
                "backgroundColor": "string",
                "preTitle": "string",
                "preTitleColor": "string",
                "title": "string (required)",
                "ctaText": "string",
                "ctaUrl": "string",
                "image": { "media_object" },
                "imageAlt": "string"
              }
            ]
          },
          "footerBannerQrCode": { "media_object" },
          "footerBannerText": "string",
          "footerBannerAppStoreButtons": { "media_object" },
          "footerBannerAppStoreButtonsAlt": "string"
        }
      ]
    },

    "offeringsTitle": "Our offerings",
    "offerings": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "title": "string (required)",
          "description": "text (required)",
          "image": { "media_object (required)" },
          "cardType": "secured | unsecured"
        }
      ]
    },

    "stillExploringTitle": "Still Exploring?",
    "stillExploringSubtitle": "Apply for a credit card with our partner banks",
    "stillExploringCards": {
      "data": [
        {
          "id": "integer",
          "attributes": {
            "bankName": "string (required)",
            "bankId": "string (required)",
            "logo": { "media_object (required)" },
            "logoAlt": "string (required)",
            "redirectUrl": "string (required) — base URL only, no UTM params",
            "utmParams": {
              "utm_source": "string",
              "utm_medium": "string",
              "utm_campaign": "string"
            },
            "redirectErrorText": "string",
            "gradient": { "media_object" },
            "buttonText": "string",
            "variant": "red | orange | blue | green",
            "cardType": "bank",
            "order": "integer",
            "benefits": [
              {
                "id": "integer",
                "order": 1,
                "label": "string (required)"
              }
            ]
          }
        }
      ]
    },

    "ownStepTitlePrefix": "Own a credit card in just",
    "ownStepSteps": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "stepNumber": "integer (required)",
          "text": "string (required)",
          "icon": { "media_object (required)" },
          "iconAlt": "string",
          "stepNumberIcon": { "media_object" },
          "backgroundImage": { "media_object" }
        }
      ]
    },

    "learnAboutUsText": "How did you learn about us?",
    "learnAboutUsArrowIcon": { "media_object" },
    "learnAboutUsArrowIconAlt": "Arrow",

    "manyBenefits": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "heading": "string (required)",
          "description": "text (required)",
          "icon": { "media_object (required)" },
          "borderColor": "string"
        }
      ]
    },

    "randomFactsIconUrl": { "media_object" },
    "randomFactsIconAlt": "Credit fact icon",
    "randomFacts": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "heading": "string (required)",
          "description": "text (required)"
        }
      ]
    },

    "poweredByBannerText": "Powered by",
    "poweredByBannerPartnerLogo": { "media_object" },
    "poweredByBannerPartnerLogoAlt": "ABCD Logo",
    "poweredByBannerDecorativeIcon": { "media_object" },

    "carouselPanels": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "type": "unsecured | secured | bank (required)",
          "bankId": "string (optional — required when type is 'bank', e.g. 'idfc', 'bob')",
          "bankName": "string (optional — required when type is 'bank', e.g. 'IDFC Bank')",
          "tabLabel": "string (required)",
          "sectionLabel": "string",
          "title": "string (required)",
          "heading": "string",
          "subheading": "string",
          "ctaLabel": "string",
          "allBenefitsLabel": "string",
          "cardCycleInterval": "integer",
          "staticCardImage": { "media_object (for secured/bank panels)" },
          "carouselCards": {
            "enabled": true,
            "content": [
              {
                "order": 1,
                "id": "string (required)",
                "image": { "media_object (required)" },
                "imageAlt": "string"
              }
            ]
          },
          "featureBadges": {
            "enabled": true,
            "content": [
              {
                "order": 1,
                "id": "string (required)",
                "label": "string (required)",
                "icon": { "media_object (required)" }
              }
            ]
          },
          "benefits": {
            "enabled": true,
            "content": [
              {
                "order": 1,
                "id": "string (required)",
                "label": "string (required)",
                "icon": { "media_object (required)" }
              }
            ]
          }
        }
      ]
    },

    "securedBenefits": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "title": "string (required)",
          "subtitle": "string",
          "description": "text (required)",
          "image": { "media_object (required)" },
          "backgroundImage": { "media_object" },
          "borderColorVariant": "purple | blue | green | orange",
          "backgroundColorVariant": "purple | blue | green | orange"
        }
      ]
    },

    "unsecuredBenefits": {
      "enabled": true,
      "content": [
        {
          "order": 1,
          "id": "string (required)",
          "title": "string (required)",
          "subtitle": "string",
          "description": "text (required)",
          "image": { "media_object (required)" },
          "backgroundImage": { "media_object" },
          "readMoreText": "string"
        }
      ]
    }
  }
}
```

---

## Components Detail

### 1. cards-dashboard.navigation-tab
**Max Items:** 6

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `label` | string | Yes | - |
| `menuItems` | component[] | Yes | - |
| `promoBanners` | component[] | No | - |
| `footerBannerQrCode` | media (image) | No | - |
| `footerBannerText` | string | No | - |
| `footerBannerAppStoreButtons` | media (image) | No | - |
| `footerBannerAppStoreButtonsAlt` | string | No | - |
| `order` | integer | Yes | - |

---

### 2. cards-dashboard.nav-menu-item
**Max Items:** 8 per tab

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | string | No | - |
| `icon` | media (image) | Yes | - |
| `navigateToUrl` | string | Yes | - |
| `order` | integer | Yes | - |

---

### 3. cards-dashboard.nav-promo-banner
**Max Items:** 3 per tab

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `backgroundColor` | string | No | - |
| `preTitle` | string | No | - |
| `preTitleColor` | string | No | - |
| `title` | string | Yes | - |
| `ctaText` | string | No | - |
| `ctaUrl` | string | No | - |
| `image` | media (image) | No | - |
| `imageAlt` | string | No | - |
| `order` | integer | Yes | - |

---

### 4. cards-dashboard.offering-card
**Max Items:** 6

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | text | Yes | - |
| `image` | media (image) | Yes | - |
| `cardType` | enum | No | `unsecured` | Values: `secured`, `unsecured` |
| `order` | integer | Yes | - |

---

### 5. cards-dashboard.still-exploring-card

> `stillExploringCards` is a **component[]** embedded directly in the `credit_card_dashboards` collection. Cards are managed inline within the dashboard entry in Strapi — no separate collection or relation is involved.

---

### 6. cards-dashboard.card-benefit-badge

> **Two variants** — used in different contexts:
> - **`still-exploring` benefits** (`id` + `label` only — icons are shared hardcoded assets)
> - **Carousel panel `featureBadges` and `benefits`** (`id` + `label` + `icon` media)

#### 6a. cards-dashboard.still-exploring-benefit (id + label only)
**Max Items:** 5 per still-exploring card

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `label` | string | Yes | - |
| `order` | integer | Yes | - |

#### 6b. cards-dashboard.panel-benefit-badge (id + label + icon)
**Max Items:** 5 per carousel panel (featureBadges), 6 per carousel panel (benefits)

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `label` | string | Yes | - |
| `icon` | media (image) | Yes | - |
| `order` | integer | Yes | - |

---

### 7. cards-dashboard.own-step-item
**Max Items:** 6

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `stepNumber` | integer | Yes | - |
| `text` | string | Yes | - |
| `icon` | media (image) | Yes | - |
| `iconAlt` | string | No | - |
| `stepNumberIcon` | media (image) | No | - |
| `backgroundImage` | media (image) | No | - |
| `order` | integer | Yes | - |

---

### 8. cards-dashboard.many-benefit-card
**Max Items:** 6

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `heading` | string | Yes | - |
| `description` | text | Yes | - |
| `icon` | media (image) | Yes | - |
| `borderColor` | string | No | `"#E6E6E6"` |
| `order` | integer | Yes | - |

---

### 9. cards-dashboard.random-fact
**Max Items:** 10

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `heading` | string | Yes | - |
| `description` | text | Yes | - |
| `order` | integer | Yes | - |

---

### 10. cards-dashboard.carousel-panel
**Max Items:** 10

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `type` | enum | Yes | - | Values: `unsecured`, `secured`, `bank` |
| `bankId` | string | No | - | **Bank panels only.** Stable bank identifier (e.g. `idfc`, `bob`). Used by the BFF to key the panel as `bank-{bankId}` for unique identification and to pass through to the apply flow. Required when `type` is `bank`. |
| `bankName` | string | No | - | **Bank panels only.** Display name of the bank (e.g. `IDFC Bank`). Passed through to analytics and the apply flow. |
| `tabLabel` | string | Yes | - |
| `sectionLabel` | string | No | - |
| `title` | string | Yes | - |
| `heading` | string | No | - |
| `subheading` | string | No | - |
| `ctaLabel` | string | No | `"Apply now"` |
| `allBenefitsLabel` | string | No | `"All benefits"` |
| `cardCycleInterval` | integer | No | `1500` | Only used for `unsecured` type |
| `staticCardImage` | media (image) | No | - | Used for `secured` and `bank` types |
| `carouselCards` | component[] | No | - | Used for `unsecured` type. Max 5 |
| `featureBadges` | component[] | No | - | Max 5 |
| `benefits` | component[] | No | - | Max 6 |
| `order` | integer | Yes | - |

---

### 11. cards-dashboard.carousel-card
**Max Items:** 5 per unsecured panel

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `image` | media (image) | Yes | - |
| `imageAlt` | string | No | - |
| `order` | integer | Yes | - |

---

### 12. cards-dashboard.secured-benefit-card
**Max Items:** 10

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | - |
| `description` | text | Yes | - |
| `image` | media (image) | Yes | - |
| `backgroundImage` | media (image) | No | - |
| `borderColorVariant` | enum | No | `purple` | Values: `purple`, `blue`, `green`, `orange` |
| `backgroundColorVariant` | enum | No | `purple` | Values: `purple`, `blue`, `green`, `orange` |
| `order` | integer | Yes | - |

---

### 13. cards-dashboard.unsecured-benefit-card
**Max Items:** 10

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | - |
| `description` | text | Yes | - |
| `image` | media (image) | Yes | - |
| `backgroundImage` | media (image) | No | - |
| `readMoreText` | string | No | `"Read more"` |
| `order` | integer | Yes | - |

---

## Restrictions Summary Table

| Section | Component | Max Items |
|---------|-----------|-----------|
| Navigation Tabs | navigation-tab | 6 |
| Nav Menu Items (per tab) | nav-menu-item | 8 |
| Nav Promo Banners (per tab) | nav-promo-banner | 3 |
| Offering Cards | offering-card | 6 |
| Still Exploring Cards | `still-exploring-card` (component) | No hard limit (recommend ≤ 10) |
| Card Benefit Badges (per card) | card-benefit-badge | 5 |
| Own Step Items | own-step-item | 6 |
| Many Benefit Cards | many-benefit-card | 6 |
| Random Facts | random-fact | 10 |
| Carousel Panels | carousel-panel | 10 |
| Carousel Cards (per unsecured panel) | carousel-card | 5 |
| Feature Badges (per carousel panel) | card-benefit-badge | 5 |
| Carousel Panel Benefits | card-benefit-badge | 6 |
| Secured Benefit Cards | secured-benefit-card | 10 |
| Unsecured Benefit Cards | unsecured-benefit-card | 10 |

---

## Section Defaults

### General

| Field | Default Value |
|-------|---------------|
| `benefitsSectionTitle` | `"One platform, many benefits"` |
| `factsSectionTitle` | `"Some random facts"` |
| `disclaimerText` | `"To refer to the Terms & Conditions"` |
| `disclaimerLinkText` | `"Tap here"` |
| `carouselPanelCycleInterval` | `60000` (60 seconds) |
| `carouselAnimationDuration` | `1500` (1.5 seconds) |

---

### Offerings Section

| Field | Default Value |
|-------|---------------|
| `offeringsTitle` | `"Our offerings"` |

---

### Still Exploring Section

| Field | Default Value |
|-------|---------------|
| `stillExploringTitle` | `"Still Exploring?"` |
| `stillExploringSubtitle` | `"Apply for a credit card with our partner banks"` |

---

### Own Step Section

| Field | Default Value |
|-------|---------------|
| `ownStepTitlePrefix` | `"Own a credit card in just"` |

---

### Learn About Us Section

| Field | Default Value |
|-------|---------------|
| `learnAboutUsText` | `"How did you learn about us?"` |
| `learnAboutUsArrowIconAlt` | `"Arrow"` |

---

### Random Facts Section

| Field | Default Value |
|-------|---------------|
| `randomFactsIconAlt` | `"Credit fact icon"` |

---

### Powered By Banner Section

| Field | Default Value |
|-------|---------------|
| `poweredByBannerText` | `"Powered by"` |
| `poweredByBannerPartnerLogoAlt` | `"ABCD Logo"` |

---

## API Response Example

> **Note:** Strapi returns data as a **flat object** — no `attributes` wrapper.
> Media fields are flat `{ id, documentId, url, mime }`. A `documentId` string is present alongside numeric `id`.

```json
{
  "data": [
    {
      "id": 1,
      "documentId": "xzmiemwpjb3af3h5jwg9so71",
      "subProduct": "credit",
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z",
      "publishedAt": "2024-01-01T00:00:00.000Z",

      "benefitsSectionTitle": "One platform, many benefits",
      "factsSectionTitle": "Some random facts",
      "disclaimerText": "To refer to the Terms & Conditions",
      "disclaimerLinkText": "Tap here",
      "carouselPanelCycleInterval": 60000,
      "carouselAnimationDuration": 1500,

      "offeringsTitle": "Our offerings",
      "stillExploringTitle": "Still Exploring?",
      "stillExploringSubtitle": "Apply for a credit card with our partner banks",
      "ownStepTitlePrefix": "Own a credit card in just",
      "learnAboutUsText": "How did you learn about us?",
      "learnAboutUsArrowIconAlt": "Arrow",
      "randomFactsIconAlt": "Credit fact icon",
      "poweredByBannerText": "Powered by",
      "poweredByBannerPartnerLogoAlt": "ABCD Logo",

      "learnAboutUsArrowIcon": { "id": 1, "documentId": "abc1", "url": "/uploads/arrow-right-red.svg", "mime": "image/svg+xml" },
      "randomFactsIconUrl": { "id": 2, "documentId": "abc2", "url": "/uploads/credit-fact.png", "mime": "image/png" },
      "poweredByBannerPartnerLogo": { "id": 3, "documentId": "abc3", "url": "/uploads/credit-logo.png", "mime": "image/png" },
      "poweredByBannerDecorativeIcon": { "id": 4, "documentId": "abc4", "url": "/uploads/powered-by-shield-icon.png", "mime": "image/png" },

      "navigationTabs": [
        {
          "id": 1,
          "order": 1,
          "tabId": "invest",
          "label": "Invest",
          "menuItems": [
            { "id": 1, "order": 1, "tabItemId": "mutual-funds", "title": "Mutual Funds", "description": "For long term wealth", "navigateToUrl": "https://...", "icon": { "id": 10, "documentId": "abc10", "url": "/uploads/icon-mutual-funds.png", "mime": "image/png" } },
            { "id": 2, "order": 2, "tabItemId": "digital-gold", "title": "Digital Gold", "description": "Buy 24K pure digital gold", "navigateToUrl": "https://...", "icon": { "id": 11, "documentId": "abc11", "url": "/uploads/icon-gold.png", "mime": "image/png" } }
          ],
          "promoBanners": [
            { "id": 1, "order": 1, "backgroundColor": "#fff4ce", "preTitle": "DIGITAL GOLD", "preTitleColor": "#845800", "title": "Start your gold investment journey with as little as Rs.10", "ctaText": "Start Now", "ctaUrl": "https://..." }
          ],
          "footerBannerText": "Scan here to start investing on the ABCD app",
          "footerBannerQrCode": { "id": 20, "documentId": "abc20", "url": "/uploads/qrcode-abcd-app.webp", "mime": "image/webp" },
          "footerBannerAppStoreButtons": { "id": 21, "documentId": "abc21", "url": "/uploads/app-store-buttons.svg", "mime": "image/svg+xml" },
          "footerBannerAppStoreButtonsAlt": "App Store buttons"
        }
      ],

      "offerings": [
        {
          "id": 1,
          "order": 1,
          "cardId": "card-1",
          "title": "Build Your Credit with FD-Backed Cards",
          "description": "Start building your credit history with FD-backed secured credit cards.",
          "cardType": "secured",
          "image": { "id": 30, "documentId": "abc30", "url": "/uploads/credit-card-1.png", "mime": "image/png" }
        },
        {
          "id": 2,
          "order": 2,
          "cardId": "card-2",
          "title": "Credit Cards Selected for You",
          "description": "Choose from 100+ credit cards from leading banks, tailored to your eligibility.",
          "cardType": "unsecured",
          "image": { "id": 31, "documentId": "abc31", "url": "/uploads/credit-card-2.png", "mime": "image/png" }
        }
      ],

      "stillExploringCards": [
        {
          "id": 1,
          "documentId": "still-idfc-001",
          "bankName": "IDFC Bank",
          "bankId": "idfc",
          "logoAlt": "IDFC Bank",
          "redirectUrl": "https://www.idfcfirst.bank.in/credit-card/ntb-diy/apply",
          "utmParams": {
            "utm_source": "Partner",
            "utm_medium": "AdityaBirlaCapital",
            "utm_campaign": "AdityaBirlaCapital___.YXBzMTph..."
          },
          "redirectErrorText": "Unable to open IDFC First Bank. Please try again.",
          "buttonText": "Apply Now",
          "variant": "red",
          "cardType": "bank",
          "order": 1,
          "logo": { "id": 40, "documentId": "abc40", "url": "/uploads/idfc-bank.svg", "mime": "image/svg+xml" },
          "gradient": { "id": 41, "documentId": "abc41", "url": "/uploads/exploring-gradient-red.png", "mime": "image/png" },
          "benefits": [
            { "id": 1, "order": 1, "benefitId": "1", "label": "100% Digital Journey" },
            { "id": 2, "order": 2, "benefitId": "2", "label": "Easy Application Process" },
            { "id": 3, "order": 3, "benefitId": "3", "label": "Attractive Benefits" }
          ]
        },
        {
          "id": 2,
          "documentId": "still-bob-001",
          "bankName": "Bank of Baroda",
          "bankId": "bob",
          "logoAlt": "Bank of Baroda",
          "redirectUrl": "https://instant.mycard.bobcard.tech/",
          "utmParams": {
            "utm_source": "Col_ABCD",
            "utm_medium": "ABCD_App",
            "utm_campaign": "BOBCARD_acquisition"
          },
          "redirectErrorText": "Unable to open Bank of Baroda. Please try again.",
          "buttonText": "Apply Now",
          "variant": "orange",
          "cardType": "bank",
          "order": 2,
          "logo": { "id": 42, "documentId": "abc42", "url": "/uploads/bank-of-baroda.svg", "mime": "image/svg+xml" },
          "gradient": { "id": 43, "documentId": "abc43", "url": "/uploads/exploring-gradient-yellow.png", "mime": "image/png" },
          "benefits": [
            { "id": 4, "order": 1, "benefitId": "1", "label": "100% Digital Journey" },
            { "id": 5, "order": 2, "benefitId": "2", "label": "Easy Application Process" },
            { "id": 6, "order": 3, "benefitId": "3", "label": "Attractive Benefits" }
          ]
        }
      ],

      "ownStepSteps": [
        { "id": 1, "order": 1, "stepId": "step-1", "stepNumber": 1, "text": "Start with a few quick personal details", "iconAlt": "Account icon", "icon": { "id": 60, "documentId": "abc60", "url": "/uploads/account.svg", "mime": "image/svg+xml" }, "stepNumberIcon": { "id": 61, "documentId": "abc61", "url": "/uploads/one-step.svg", "mime": "image/svg+xml" }, "backgroundImage": { "id": 62, "documentId": "abc62", "url": "/uploads/owncard-bg.svg", "mime": "image/svg+xml" } },
        { "id": 2, "order": 2, "stepId": "step-2", "stepNumber": 2, "text": "Select that fits your lifestyle", "iconAlt": "Document icon", "icon": { "id": 63, "documentId": "abc63", "url": "/uploads/credit-card-svg.svg", "mime": "image/svg+xml" }, "stepNumberIcon": { "id": 64, "documentId": "abc64", "url": "/uploads/two-step.svg", "mime": "image/svg+xml" }, "backgroundImage": { "id": 62, "documentId": "abc62", "url": "/uploads/owncard-bg.svg", "mime": "image/svg+xml" } },
        { "id": 3, "order": 3, "stepId": "step-3", "stepNumber": 3, "text": "Add your work and address details", "iconAlt": "Verify icon", "icon": { "id": 65, "documentId": "abc65", "url": "/uploads/briefcase-variant.svg", "mime": "image/svg+xml" }, "stepNumberIcon": { "id": 66, "documentId": "abc66", "url": "/uploads/three-step.svg", "mime": "image/svg+xml" }, "backgroundImage": { "id": 62, "documentId": "abc62", "url": "/uploads/owncard-bg.svg", "mime": "image/svg+xml" } },
        { "id": 4, "order": 4, "stepId": "step-4", "stepNumber": 4, "text": "Complete your KYC", "iconAlt": "Check icon", "icon": { "id": 67, "documentId": "abc67", "url": "/uploads/check-decagram.svg", "mime": "image/svg+xml" }, "stepNumberIcon": { "id": 68, "documentId": "abc68", "url": "/uploads/four-step.svg", "mime": "image/svg+xml" }, "backgroundImage": { "id": 62, "documentId": "abc62", "url": "/uploads/owncard-bg.svg", "mime": "image/svg+xml" } }
      ],

      "manyBenefits": [
        { "id": 1, "order": 1, "benefitId": "benefit-1", "heading": "Choose your own cards", "description": "From the list of recommended cards for you", "borderColor": "#E6E6E6", "icon": { "id": 70, "documentId": "abc70", "url": "/uploads/own-card.svg", "mime": "image/svg+xml" } },
        { "id": 2, "order": 2, "benefitId": "benefit-2", "heading": "9+ lenders onboard", "description": "To give you endless options to choose from", "borderColor": "#E6E6E6", "icon": { "id": 71, "documentId": "abc71", "url": "/uploads/lenders.svg", "mime": "image/svg+xml" } },
        { "id": 3, "order": 3, "benefitId": "benefit-3", "heading": "Cashback and rewards", "description": "Select the cards that suit you", "borderColor": "#E6E6E6", "icon": { "id": 72, "documentId": "abc72", "url": "/uploads/card-rewards.svg", "mime": "image/svg+xml" } }
      ],

      "randomFacts": [
        { "id": 1, "order": 1, "factId": "fact-1", "heading": "Credit cards would circle the Earth 3.5 times", "description": "If you lined up all the credit cards currently in circulation in the world, they'd wrap around the Earth 3.5 times!" },
        { "id": 2, "order": 2, "factId": "fact-2", "heading": "First credit card was issued in 1950", "description": "The Diners Club card was the first credit card, introduced in 1950, revolutionizing consumer spending." },
        { "id": 3, "order": 3, "factId": "fact-3", "heading": "Rewards points are worth real money", "description": "Average credit card user can earn $1000+ in rewards annually just by using their card wisely." }
      ],

      "carouselPanels": [
        {
          "id": 1,
          "order": 1,
          "panelId": "unsecured",
          "type": "unsecured",
          "tabLabel": "Unsecured Cards",
          "sectionLabel": "Premium & Cashback Cards",
          "title": "Get Rewarded Every Time You Spend!",
          "ctaLabel": "Apply now",
          "allBenefitsLabel": "All benefits",
          "cardCycleInterval": 1500,
          "carouselCards": [
            { "id": 1, "order": 1, "cardId": "c1", "imageAlt": "Zenith+", "image": { "data": { "id": 80, "attributes": { "url": "/uploads/credit-card.png" } } } },
            { "id": 2, "order": 2, "cardId": "c2", "imageAlt": "Axis ACE", "image": { "data": { "id": 81, "attributes": { "url": "/uploads/zenith-card.png" } } } }
          ],
          "featureBadges": [
            { "id": 1, "order": 1, "badgeId": "digital", "label": "100% Digital Journey", "icon": { "data": { "id": 90, "attributes": { "url": "/uploads/digital.png" } } } },
            { "id": 2, "order": 2, "badgeId": "easy-apply", "label": "Easy Application Process", "icon": { "data": { "id": 91, "attributes": { "url": "/uploads/application.png" } } } },
            { "id": 3, "order": 3, "badgeId": "benefits", "label": "Attractive Benefits", "icon": { "data": { "id": 92, "attributes": { "url": "/uploads/stars.png" } } } }
          ],
          "benefits": [
            { "id": 1, "order": 1, "benefitId": "cashback", "label": "Cashback", "icon": { "data": { "id": 93, "attributes": { "url": "/uploads/cashback.png" } } } },
            { "id": 2, "order": 2, "benefitId": "lounge", "label": "Lounge", "icon": { "data": { "id": 94, "attributes": { "url": "/uploads/export-lounge.png" } } } },
            { "id": 3, "order": 3, "benefitId": "dining", "label": "Dining", "icon": { "data": { "id": 95, "attributes": { "url": "/uploads/dining.png" } } } },
            { "id": 4, "order": 4, "benefitId": "shopping", "label": "Shopping", "icon": { "data": { "id": 96, "attributes": { "url": "/uploads/shopping.png" } } } }
          ]
        },
        {
          "id": 2,
          "order": 2,
          "panelId": "secured",
          "type": "secured",
          "tabLabel": "Secured Cards",
          "sectionLabel": "New to credit?",
          "title": "Start with FD-backed secured card",
          "heading": "Secured Credit Cards",
          "subheading": "Build your credit score with an FD-backed card.",
          "ctaLabel": "Apply now",
          "allBenefitsLabel": "All benefits",
          "staticCardImage": { "data": { "id": 82, "attributes": { "url": "/uploads/secured.png" } } },
          "featureBadges": [],
          "benefits": [
            { "id": 5, "order": 1, "benefitId": "cashback", "label": "Cashback", "icon": { "data": { "id": 93, "attributes": { "url": "/uploads/cashback.png" } } } },
            { "id": 6, "order": 2, "benefitId": "lounge", "label": "Lounge", "icon": { "data": { "id": 94, "attributes": { "url": "/uploads/export-lounge.png" } } } }
          ]
        },
        {
          "id": 3,
          "order": 3,
          "panelId": "bank-idfc",
          "type": "bank",
          "bankId": "idfc",
          "bankName": "IDFC Bank",
          "tabLabel": "IDFC Bank",
          "sectionLabel": "Partner Bank",
          "title": "IDFC Bank",
          "heading": "Partner Bank",
          "subheading": "Explore top cards from IDFC Bank.",
          "ctaLabel": "Apply now",
          "allBenefitsLabel": "All benefits",
          "staticCardImage": { "data": { "id": 83, "attributes": { "url": "/uploads/bank-backed.png" } } },
          "featureBadges": [
            { "id": 7, "order": 1, "badgeId": "digital", "label": "100% Digital Journey", "icon": { "data": { "id": 90, "attributes": { "url": "/uploads/digital.png" } } } }
          ],
          "benefits": [
            { "id": 9, "order": 1, "benefitId": "cashback", "label": "Cashback", "icon": { "data": { "id": 93, "attributes": { "url": "/uploads/cashback.png" } } } }
          ]
        },
        {
          "id": 4,
          "order": 4,
          "panelId": "bank-bob",
          "type": "bank",
          "bankId": "bob",
          "bankName": "Bank of Baroda",
          "tabLabel": "Bank of Baroda",
          "sectionLabel": "Bank of Baroda Credit Cards",
          "title": "Bank of Baroda",
          "heading": "Bank of Baroda Credit Cards",
          "subheading": "Explore top cards from Bank of Baroda.",
          "ctaLabel": "Apply now",
          "allBenefitsLabel": "All benefits",
          "staticCardImage": { "data": { "id": 84, "attributes": { "url": "/uploads/bank-backed.png" } } },
          "featureBadges": [
            { "id": 10, "order": 1, "badgeId": "digital", "label": "100% Digital Journey", "icon": { "data": { "id": 90, "attributes": { "url": "/uploads/digital.png" } } } }
          ],
          "benefits": [
            { "id": 11, "order": 1, "benefitId": "cashback", "label": "Cashback", "icon": { "data": { "id": 93, "attributes": { "url": "/uploads/cashback.png" } } } }
          ]
        }
      ],

      "securedBenefits": [
        { "id": 1, "order": 1, "benefitId": "merchant-offers", "title": "Merchant offers", "subtitle": "Instant discounts", "description": "Total yearly savings of ₹6,600 on 4+ brands", "borderColorVariant": "purple", "backgroundColorVariant": "purple", "image": { "data": { "id": 100, "attributes": { "url": "/uploads/app-shop.svg" } } }, "backgroundImage": { "data": { "id": 101, "attributes": { "url": "/uploads/secured-benefits-gradient.svg" } } } },
        { "id": 2, "order": 2, "benefitId": "welcome", "title": "Welcome offer", "subtitle": "Activation benefit", "description": "Welcome offer worth ₹5,000 on over 10 brands", "borderColorVariant": "purple", "backgroundColorVariant": "purple", "image": { "data": { "id": 102, "attributes": { "url": "/uploads/rocket-2.svg" } } }, "backgroundImage": { "data": { "id": 101, "attributes": { "url": "/uploads/secured-benefits-gradient.svg" } } } }
      ],

      "unsecuredBenefits": [
        { "id": 1, "order": 1, "benefitId": "rewards", "title": "Rewards", "subtitle": "Earn points on eligible spends", "description": "Collect reward points on everyday purchases and redeem them as per issuer rules.", "readMoreText": "Read more", "image": { "data": { "id": 110, "attributes": { "url": "/uploads/card-reward.svg" } } }, "backgroundImage": { "data": { "id": 111, "attributes": { "url": "/uploads/unsecured-benefits-Ygradient.svg" } } } },
        { "id": 2, "order": 2, "benefitId": "travel", "title": "Travel", "subtitle": "Travel-friendly perks", "description": "Get travel-related offers and privileges on eligible travel spends (where applicable).", "readMoreText": "Read more", "image": { "data": { "id": 112, "attributes": { "url": "/uploads/airport-location.svg" } } }, "backgroundImage": { "data": { "id": 113, "attributes": { "url": "/uploads/unsecured-benefits-gradient.svg" } } } }
      ]
    }
  ],
  "meta": {}
}
```

---

## Populate Query for Full Response

```
/api/cards-dashboard-page?filters[subProduct][$eq]=credit&populate[navigationTabs][populate][menuItems][populate]=*&populate[navigationTabs][populate][promoBanners][populate]=*&populate[navigationTabs][populate][footerBannerQrCode]=*&populate[navigationTabs][populate][footerBannerAppStoreButtons]=*&populate[learnAboutUsArrowIcon]=*&populate[randomFactsIconUrl]=*&populate[poweredByBannerPartnerLogo]=*&populate[poweredByBannerDecorativeIcon]=*&populate[offerings][populate]=*&populate[stillExploringCards][populate][logo]=*&populate[stillExploringCards][populate][gradient]=*&populate[stillExploringCards][populate][benefits][populate]=*&populate[ownStepSteps][populate]=*&populate[manyBenefits][populate]=*&populate[randomFacts]=*&populate[carouselPanels][populate][carouselCards][populate]=*&populate[carouselPanels][populate][featureBadges][populate]=*&populate[carouselPanels][populate][benefits][populate]=*&populate[carouselPanels][populate][staticCardImage]=*&populate[securedBenefits][populate]=*&populate[unsecuredBenefits][populate]=*
```

Or use deep populate:
```
/api/cards-dashboard-page?filters[subProduct][$eq]=credit&populate=deep
```

---

## Carousel Panel Types — Field Usage Matrix

> Different panel `type` values use different fields. This table clarifies which fields apply per type.

| Field | `unsecured` | `secured` | `bank` |
|-------|:-----------:|:---------:|:------:|
| `bankId` | ❌ | ❌ | ✅ (required) |
| `bankName` | ❌ | ❌ | ✅ (required) |
| `tabLabel` | ✅ | ✅ | ✅ |
| `sectionLabel` | ✅ | ✅ | ✅ |
| `title` | ✅ | ✅ | ✅ |
| `heading` | ❌ | ✅ | ✅ |
| `subheading` | ❌ | ✅ | ✅ |
| `ctaLabel` | ✅ | ✅ | ✅ |
| `allBenefitsLabel` | ✅ | ✅ | ✅ |
| `cardCycleInterval` | ✅ | ❌ | ❌ |
| `staticCardImage` | ❌ | ✅ | ✅ |
| `carouselCards` | ✅ | ❌ | ❌ |
| `featureBadges` | ✅ | ❌ | ✅ |
| `benefits` | ✅ | ✅ | ✅ |

---


## Related Documentation

| Document | Purpose |
|----------|---------|
| [Credit_Card_Landing_Page_CMS_Schema.md](./Credit_Card_Landing_Page_CMS_Schema.md) | CMS schema for the credit card landing page |

---