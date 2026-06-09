# Personal Loan Journey Pages - Complete Schema Documentation

## Content-Type: Personal Loan Journey Pages

**Collection Name:** `personal-loan-journey-pages`  
**Singular Name:** `personal-loan-journey-page`  
**Plural Name:** `personal-loan-journey-pages`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `partner` | string | No | `default` | - | Optional partner-specific variant |
| `breOfferScreen` | component | No | fallback | - | BRE offer screen configuration and messaging |
| `panVerification` | component | No | fallback | - | PAN verification step content and validations |
| `lreMarketplaceScreen` | component | No | fallback | - | LRE marketplace offer screen configuration |
| `permissionScreen` | component | No | fallback | - | App permissions request screen content |
| `basicDetails` | component | No | fallback | - | Basic details form configuration and labels |
| `loader` | component | No | fallback | - | Loader/waiting screen messaging and assets |
| `cooldownScreen` | component | No | fallback | - | Cooldown period screen (reapply after X days) |
| `softRejectScreen` | component | No | fallback | - | Soft reject screen (no offers available) |

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/personal-loan-journey-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/personal-loan-journey-pages` | List all journey pages |
| GET | `/api/personal-loan-journey-pages/:id` | Get single journey page by ID |
| POST | `/api/personal-loan-journey-pages` | Create new journey page |
| PUT | `/api/personal-loan-journey-pages/:id` | Update journey page content |
| DELETE | `/api/personal-loan-journey-pages/:id` | Delete journey page |

### Query Parameters

**Filtering by Partner:**
```
?filters[partner][$eq]=default
?populate=*
```

**Full Personal Loan Journey Query:**
```
GET /api/personal-loan-journey-pages?
  filters[partner][$eq]=default&
  populate=*
```

**Partner-Specific Content:**
```
GET /api/personal-loan-journey-pages?
  filters[partner][$eq]=partner_name&
  populate=*
```

### Response Payload Structure

**Success Response (200 OK):**
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123xyz",
    
        "partner": "default",
        "breOfferScreen": {
          "pageTitle": "Personal loans",
          "loaderTitle": "Curating Loan Offer for you",
          "loaderIconPath": {
            "url": "https://cdn.abcd.io/assets/personal-loan/icons/offerloading.webp"
          }
        },
        "panVerification": {
          "title": "Personal loan",
          "introText": "Enter following details",
          "panLabel": "PAN"
        }
      
    }
  ]
}
```


## Complete JSON Structure with Data Types

```json
{
  "data": {
    "partner": "string",

    "breOfferScreen": {
      "pageTitle": "string",
      "continueCtaText": "string",
      "loaderTitle": "string",
      "loaderSubtitleTop": "string",
      "loaderSubtitleBottom": "string",
      "loaderIconAlt": "string",
      "offerCardCongratsText": "string",
      "offerCardCongratsIconLeft": "media (emoji)",
      "offerCardCongratsIconRight": "media (emoji)",
      "offerCardDescription": "string",
      "offerCardEmiLabelText": "string",
      "infoBannerText": "string",
      "disclaimerText": "string",
      "footerInfoText": "string",
      "footerClockIconAlt": "string",
      "loaderIconPath": "media",
      "offerCardImagesrc": "media",
      "clockIconPath": "media"
    },

    "panVerification": {
      "title": "string",
      "subtitle": "string | null",
      "introText": "string",
      "ctaText": "string",
      "secondaryLinkText": "string",
      "panLabel": "string",
      "panPlaceholder": "string",
      "fullNameLabel": "string",
      "fullNamePlaceholder": "string",
      "termsShortText": "string",
      "termsFullText": "string (multiline)",
      "termsAndConditionsLink": "string (URL)",
      "privacyPolicyLink": "string (URL)",
      "lendingPartnersLink": "string (URL)",
      "invalidPanError": "string",
      "invalidNameError": "string",
      "termsNotAcceptedError": "string",
      "panNotFoundError": "string",
      "softRejectError": "string",
      "technicalError": "string"
    },

    "lreMarketplaceScreen": {
      "pageTitle": "string",
      "sectionTitle": "string",
      "rankingText": "string",
      "viewAllText": "string",
      "sidebarOfferLimit": "number",
      "applyNowText": "string",
      "viewKfsText": "string",
      "amountDisclaimerText": "string",
      "loanAmountLabel": "string",
      "monthlyEmiLabel": "string",
      "tenureLabel": "string",
      "aprLabel": "string",
      "infoRowText": "string",
      "definitionsTitle": "string",
      "definitionsCloseTextMobile": "string",
      "definitionsCloseTextDesktop": "string",
      "ineligibleLendersTitle": "string",
      "noOfferTitle": "string",
      "noOfferDescription": "string",
      "noOfferCloseText": "string",
      "viewMoreText": "string",
      "viewMoreLeftIcon": "media",
      "viewMoreLeftIconAlt": "string",
      "viewMoreRightIcon": "media",
      "viewMoreRightIconAlt": "string",
      "definitions": [
        {
          "definitionsId": "string",
          "label": "string",
          "highlightedTerm": "string",
          "description": "string"
        }
      ],
      "noOfferLenderIcons": [
        {
          "noOfferLenderId": "string",
          "src": "media",
          "alt": "string"
        }
      ],
      "lenderLogos": [
        {
          "lenderId": "number",
          "Lendername": "string",
          "src": "media",
          "alt": "string"
        }
      ],
      "lenderLogosListView": [
        {
          "lenderId": "number",
          "Lendername": "string",
          "src": "media",
          "alt": "string"
        }
      ]
    },

    "permissionScreen": {
      "pageTitle": "string",
      "title": "string",
      "subtitle": "string",
      "ctaText": "string",
      "poweredByText": "string",
      "redirectUrl": "string (URL)",
      "items": [
        {
          "permissionId": "string",
          "title": "string",
          "description": "string",
          "checked": "boolean"
        }
      ]
    },

    "basicDetails": {
      "title": "string",
      "subtitle": "string | null",
      "stepLabel": "string",
      "stepNumber": "string",
      "formTitle": "string",
      "formSubtitle": "string",
      "emailLabel": "string",
      "emailPlaceholder": "string",
      "dobLabel": "string",
      "dobPlaceholder": "string",
      "genderLabel": "string",
      "employmentTitle": "string",
      "monthlyIncomeLabel": "string",
      "monthlyIncomePlaceholder": "string",
      "incomeMin": "number",
      "incomeMax": "number",
      "addressTitle": "string",
      "pincodeLabel": "string",
      "pincodePlaceholder": "string",
      "addressLine1Placeholder": "string",
      "addressLine2Placeholder": "string",
      "cityPlaceholder": "string",
      "statePlaceholder": "string",
      "ctaText": "string",
      "invalidEmailError": "string",
      "genderNotSelectedError": "string",
      "employmentNotSelectedError": "string",
      "incomeMinError": "string",
      "incomeMaxError": "string",
      "invalidPincodeError": "string",
      "technicalError": "string",
      "addressFieldVisible": "boolean"
    },

    "loader": {
      "title": "string",
      "subtitleLine1": "string",
      "subtitleLine2": "string",
      "waitPrefixText": "string",
      "waitHighlightSeconds": "number",
      "waitSuffixText": "string",
      "safeVisualPath": "media",
      "waitIconPath": "media",
      "sheetVisualPath": "media"
    },

    "cooldownScreen": {
      "title": "string",
      "cooldownIconPath": "media",
      "cooldownIconAlt": "string",
      "cooldownDays": "number",
      "cooldownHeadline": "string (with {days} placeholder)",
      "cooldownMessage": "string (with {days} placeholder)",
      "primaryCtaText": "string",
      "connectExecutiveText": "string"
    },

    "softRejectScreen": {
      "title": "string",
      "iconPath": "media",
      "iconAlt": "string",
      "messageText": "string (multiline with \\n)",
      "supportingText": "string",
      "primaryCtaText": "string"
    }
  }
}
```

---

## Components Detail

### 1. journey.bre-offer-screen

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `pageTitle` | string | Yes | - |
| `continueCtaText` | string | Yes | - |
| `loaderTitle` | string | Yes | - |
| `loaderSubtitleTop` | string | Yes | - |
| `loaderSubtitleBottom` | string | Yes | - |
| `loaderIconAlt` | string | Yes | - |
| `offerCardCongratsText` | string | Yes | - |
| `offerCardCongratsIconLeft` | string (emoji) | No | "🎉" |
| `offerCardCongratsIconRight` | string (emoji) | No | "🎉" |
| `offerCardDescription` | string | Yes | - |
| `offerCardEmiLabelText` | string | Yes | - |
| `infoBannerText` | string | Yes | - |
| `disclaimerText` | string | Yes | - |
| `footerInfoText` | string | Yes | - |
| `footerClockIconAlt` | string | Yes | - |
| `loaderIconPath` | media | Yes | - |
| `offerCardImagesrc` | media | No | - |
| `clockIconPath` | media | No | - |

---

### 2. journey.pan-verification

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `subtitle` | string | No | null |
| `introText` | string | Yes | - |
| `ctaText` | string | Yes | - |
| `secondaryLinkText` | string | No | - |
| `panLabel` | string | Yes | - |
| `panPlaceholder` | string | Yes | - |
| `fullNameLabel` | string | Yes | - |
| `fullNamePlaceholder` | string | Yes | - |
| `termsShortText` | string | Yes | - |
| `termsFullText` | text | Yes | - |
| `termsAndConditionsLink` | string (URL) | Yes | - |
| `privacyPolicyLink` | string (URL) | Yes | - |
| `lendingPartnersLink` | string (URL) | Yes | - |
| `invalidPanError` | string | Yes | - |
| `invalidNameError` | string | Yes | - |
| `termsNotAcceptedError` | string | Yes | - |
| `panNotFoundError` | string | Yes | - |
| `softRejectError` | string | Yes | - |
| `technicalError` | string | Yes | - |

---

### 3. journey.definition-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `definitionId` | string | Yes | - |
| `label` | string | Yes | - |
| `highlightedTerm` | string | Yes | - |
| `description` | string | Yes | - |

---

### 4. journey.noOfferLenderId-Icon

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `noOfferLenderId` | string | No | - |
| `src` | media | No | - |
| `alt` | string | No | - |

---

### 5. journey.lender-logo

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `lenderId` | number | No | - |
| `Lendername` | string | No | - |
| `src` | media | No | - |
| `alt` | string | No | - |

---

### 6. journey.lre-marketplace-screen

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `pageTitle` | string | Yes | - |
| `sectionTitle` | string | Yes | - |
| `rankingText` | string | Yes | - |
| `viewAllText` | string | Yes | - |
| `sidebarOfferLimit` | number | Yes | 2 |
| `applyNowText` | string | Yes | - |
| `viewKfsText` | string | Yes | - |
| `amountDisclaimerText` | string | Yes | - |
| `loanAmountLabel` | string | Yes | - |
| `monthlyEmiLabel` | string | Yes | - |
| `tenureLabel` | string | Yes | - |
| `aprLabel` | string | Yes | - |
| `infoRowText` | string | Yes | - |
| `definitionsTitle` | string | Yes | - |
| `definitionsCloseTextMobile` | string | Yes | - |
| `definitionsCloseTextDesktop` | string | Yes | - |
| `ineligibleLendersTitle` | string | Yes | - |
| `noOfferTitle` | string | Yes | - |
| `noOfferDescription` | string | Yes | - |
| `noOfferCloseText` | string | Yes | - |
| `viewMoreText` | string | Yes | - |
| `viewMoreLeftIcon` | media | Yes | - |
| `viewMoreLeftIconAlt` | string | Yes | - |
| `viewMoreRightIcon` | media | Yes | - |
| `viewMoreRightIconAlt` | string | Yes | - |
| `definitions` | component[] | Yes | - |
| `noOfferLenderIcons` | component[] | No | [] |
| `lenderLogos` | component[] | Yes | - |
| `lenderLogosListView` | component[] | Yes | - |

---

### 7. journey.permission-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `permissionId` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | string | Yes | - |
| `checked` | boolean | No | false |

---

### 8. journey.permission-screen

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `pageTitle` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | Yes | - |
| `ctaText` | string | Yes | - |
| `poweredByText` | string | Yes | - |
| `redirectUrl` | string (URL) | No | - |
| `items` | component[] | Yes | - |

---

### 9. journey.basic-details

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `subtitle` | string | No | null |
| `stepLabel` | string | Yes | - |
| `stepNumber` | string | Yes | - |
| `formTitle` | string | Yes | - |
| `formSubtitle` | string | Yes | - |
| `emailLabel` | string | Yes | - |
| `emailPlaceholder` | string | Yes | - |
| `dobLabel` | string | Yes | - |
| `dobPlaceholder` | string | Yes | - |
| `genderLabel` | string | Yes | - |
| `employmentTitle` | string | Yes | - |
| `monthlyIncomeLabel` | string | Yes | - |
| `monthlyIncomePlaceholder` | string | Yes | - |
| `incomeMin` | number | Yes | 25000 |
| `incomeMax` | number | Yes | 500000 |
| `addressTitle` | string | Yes | - |
| `pincodeLabel` | string | Yes | - |
| `pincodePlaceholder` | string | Yes | - |
| `addressLine1Placeholder` | string | Yes | - |
| `addressLine2Placeholder` | string | Yes | - |
| `cityPlaceholder` | string | Yes | - |
| `statePlaceholder` | string | Yes | - |
| `ctaText` | string | Yes | - |
| `invalidEmailError` | string | Yes | - |
| `genderNotSelectedError` | string | Yes | - |
| `employmentNotSelectedError` | string | Yes | - |
| `incomeMinError` | string | Yes | - |
| `incomeMaxError` | string | Yes | - |
| `invalidPincodeError` | string | Yes | - |
| `technicalError` | string | Yes | - |
| `addressFieldVisible` | boolean | No | true |

---

### 10. journey.loader-screen

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `subtitleLine1` | string | Yes | - |
| `subtitleLine2` | string | Yes | - |
| `waitPrefixText` | string | Yes | - |
| `waitHighlightSeconds` | number | No | 45 |
| `waitSuffixText` | string | Yes | - |
| `safeVisualPath` | media | Yes | - |
| `waitIconPath` | media | Yes | - |
| `sheetVisualPath` | media | Yes | - |

---

### 11. journey.cooldown-screen

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `cooldownIconPath` | media | Yes | - |
| `cooldownIconAlt` | string | Yes | - |
| `cooldownDays` | number | Yes | 30 |
| `cooldownHeadline` | string | Yes | - |
| `cooldownMessage` | string | Yes | - |
| `primaryCtaText` | string | Yes | - |
| `connectExecutiveText` | string | Yes | - |

**Note:** Headline and message fields support `{days}` placeholder for dynamic values.

---

### 12. journey.soft-reject-screen

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `iconPath` | media | Yes | - |
| `iconAlt` | string | Yes | - |
| `messageText` | string | Yes | - |
| `supportingText` | string | Yes | - |
| `primaryCtaText` | string | Yes | - |
