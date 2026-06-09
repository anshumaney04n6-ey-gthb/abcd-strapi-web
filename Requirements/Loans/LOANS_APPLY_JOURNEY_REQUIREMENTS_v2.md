# Loans CMS Requirements v2 - Loans Apply Journey

**Date:** 2026-04-28 
**Status:** IMPLEMENTED  
**Collection Type:** `loans-apply-journey`

---

## 1. Components

### 1.1 Apply Journey Sections

| Key | Component | Purpose |
|-----|-----------|---------|
| `panVerification` | `apply-pan-verification` | PAN and full-name capture screen with consent text and validation messages |
| `basicDetails` | `apply-basic-details` | Personal details form with income, address, and validation messages |
| `loader` | `apply-loader` | Offer curation loader screen shown while BRE/lender evaluation is in progress |
| `breOfferScreen` | `apply-bre-offer` | Single best-offer card shown after BRE evaluation with loader, EMI details, and CTA |
| `lreMarketplaceScreen` | `apply-lre-marketplace` | Multi-lender marketplace listing with KFS/APR definitions, ineligible lenders, and no-offer state |

### 1.2 Reusable Components

| Component | Used In |
|-----------|---------|
| `definition-item` | `lreMarketplaceScreen.definitions[]` |
| `no-offer-lender-icon` | `lreMarketplaceScreen.noOfferLenderIcons[]` |
| `lender-logo` | `lreMarketplaceScreen.lenderLogos`, `lreMarketplaceScreen.lenderLogosListView` |

---

## 2. Schema

### 2.1 `panVerification`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `subtitle` | string | No |
| `introText` | string | Yes |
| `ctaText` | string | Yes |
| `secondaryLinkText` | string | No |
| `panLabel` | string | Yes |
| `panPlaceholder` | string | No |
| `fullNameLabel` | string | Yes |
| `fullNamePlaceholder` | string | No |
| `termsShortText` | string | No |
| `termsFullText` | string | No |
| `termsAndConditionsLink` | string | No |
| `privacyPolicyLink` | string | No |
| `lendingPartnersLink` | string | No |
| `invalidPanError` | string | No |
| `invalidNameError` | string | No |
| `termsNotAcceptedError` | string | No |
| `panNotFoundError` | string | No |
| `softRejectError` | string | No |
| `technicalError` | string | No |

### 2.2 `basicDetails`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `subtitle` | string | No |
| `stepLabel` | string | Yes |
| `stepNumber` | string | Yes |
| `formTitle` | string | Yes |
| `formSubtitle` | string | Yes |
| `emailLabel` | string | Yes |
| `emailPlaceholder` | string | No |
| `dobLabel` | string | Yes |
| `dobPlaceholder` | string | No |
| `genderLabel` | string | Yes |
| `employmentTitle` | string | Yes |
| `monthlyIncomeLabel` | string | Yes |
| `monthlyIncomePlaceholder` | string | No |
| `incomeMin` | integer | Yes |
| `incomeMax` | integer | Yes |
| `addressTitle` | string | Yes |
| `pincodeLabel` | string | Yes |
| `pincodePlaceholder` | string | No |
| `addressLine1Placeholder` | string | Yes |
| `addressLine2Placeholder` | string | Yes |
| `cityPlaceholder` | string | Yes |
| `statePlaceholder` | string | Yes |
| `ctaText` | string | Yes |
| `invalidEmailError` | string | No |
| `genderNotSelectedError` | string | No |
| `employmentNotSelectedError` | string | No |
| `incomeMinError` | string | No |
| `incomeMaxError` | string | No |
| `invalidPincodeError` | string | No |
| `technicalError` | string | No |

### 2.3 `loader`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `subtitleLine1` | string | Yes |
| `subtitleLine2` | string | Yes |
| `waitPrefixText` | string | Yes |
| `waitHighlightSeconds` | number | No |
| `waitSuffixText` | string | Yes |
| `safeVisualPath` | string | Yes |
| `waitIconPath` | string | Yes |
| `sheetVisualPath` | string | Yes |


### 2.4 `breOfferScreen`

| Field | Type | Required |
|-------|------|:--------:|
| `pageTitle` | string | Yes |
| `continueCtaText` | string | Yes |
| `loaderTitle` | string | Yes |
| `loaderSubtitleTop` | string | Yes |
| `loaderSubtitleBottom` | string | Yes |
| `loaderIconAlt` | string | Yes |
| `offerCardCongratsText` | string | Yes |
| `offerCardCongratsIconLeft` | string | Yes |
| `offerCardCongratsIconRight` | string | Yes |
| `offerCardDescription` | string | Yes |
| `offerCardEmiLabelText` | string | Yes |
| `infoBannerText` | string | Yes |
| `disclaimerText` | string | Yes |
| `footerInfoText` | string | Yes |
| `footerClockIconAlt` | string | Yes |
| `loaderIconPath` | string (asset URL) | Yes |
| `offerCardImagesrc` | string (asset URL) | Yes |
| `offerCardImagealt` | string | Yes |
| `clockIconPath` | string (asset URL) | Yes |

### 2.5 `lreMarketplaceScreen`

| Field | Type | Required |
|-------|------|:--------:|
| `pageTitle` | string | Yes |
| `sectionTitle` | string | Yes |
| `rankingText` | string | Yes |
| `viewAllText` | string | Yes |
| `sidebarOfferLimit` | number | Yes |
| `applyNowText` | string | Yes |
| `viewKfsText` | string | Yes |
| `amountDisclaimerText` | string | Yes |
| `loanAmountLabel` | string | Yes |
| `monthlyEmiLabel` | string | Yes |
| `tenureLabel` | string | Yes |
| `aprLabel` | string | Yes |
| `infoRowText` | string | Yes |
| `definitionsTitle` | string | Yes |
| `definitionsCloseTextMobile` | string | Yes |
| `definitionsCloseTextDesktop` | string | Yes |
| `ineligibleLendersTitle` | string | Yes |
| `noOfferTitle` | string | Yes |
| `noOfferDescription` | string | Yes |
| `noOfferCloseText` | string | Yes |
| `definitions` | definition-item[] | Yes |
| `noOfferLenderIcons` | no-offer-lender-icon[] | No |
| `lenderLogos` | lender-logo | No |
| `lenderLogosListView` | lender-logo[] | No |

**definition-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `label` | string | Yes |
| `highlightedTerm` | string | Yes |
| `description` | string | Yes |

**no-offer-lender-icon:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `src` | string | Yes |
| `alt` | string | Yes |


**lender-logo:**
| Field | Type | Required |
|-------|------|:--------:|
| `Ring` | string | Yes |
| `Fibe` | string | Yes |
| `Prefr` | string | Yes |
| `ABCL` | string | Yes |
| `abcl` | string | Yes |


---

## 3. Expected API Response

**Endpoint:** `GET /api/loans-apply-journey?filters[subProduct][$eq]=personal&populate=*`

```json
{
  "data": {
    "panVerification": {
      "title": "Personal loan",
      "introText": "Enter following details",
      "ctaText": "Apply Now",
      "secondaryLinkText": "How did you learn about us?",
      "panLabel": "PAN",
      "panPlaceholder": "Enter PAN",
      "fullNameLabel": "Full name as per PAN",
      "fullNamePlaceholder": "Enter your full name",
      "termsShortText": "I agree to the ",
      "termsFullText": "I agree to the Terms and Conditions and Privacy Policy of Aditya Birla Capital Digital and its lending partners (Lenders/LSPs). I hereby, authorize them to collect, store, verify, process, and access my credit information from credit bureaus to process my loan application. I confirm that I am eligible to apply and that my household's annual income is above ₹3 lakh.",
      "termsAndConditionsLink": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
      "privacyPolicyLink": "https://www.adityabirlacapital.com/abcd/privacy-policy",
      "lendingPartnersLink": "https://www.adityabirlacapital.com/abcd/lending-partners",
      "invalidPanError": "Please enter a valid PAN in uppercase (e.g., ABCDE1234F)",
      "invalidNameError": "Characters should be minimum 3 letters",
      "termsNotAcceptedError": "Please accept terms & conditions",
      "panNotFoundError": "PAN details not found. Please recheck and try again",
      "softRejectError": "We are unable to proceed with your application",
      "technicalError": "Something went wrong. Please retry"
    },
    "basicDetails": {
      "title": "Personal loan",
      "stepLabel": "Basic details",
      "stepNumber": "Step 1/5",
      "formTitle": "Verify your personal details",
      "formSubtitle": "For your loan application please enter accurate information that matches your KYC document.",
      "emailLabel": "Email (Required)",
      "emailPlaceholder": "Enter email address",
      "dobLabel": "Date of birth (Required)",
      "dobPlaceholder": "DD/MM/YYYY",
      "genderLabel": "Gender",
      "employmentTitle": "Select employment type",
      "monthlyIncomeLabel": "Monthly income",
      "monthlyIncomePlaceholder": "Enter monthly income",
      "incomeMin": 25000,
      "incomeMax": 500000,
      "addressTitle": "Residential address",
      "pincodeLabel": "Pincode (Required)",
      "pincodePlaceholder": "Enter pincode",
      "addressLine1Placeholder": "House no., Building name (Required)",
      "addressLine2Placeholder": "Road name, area, colony (Required)",
      "cityPlaceholder": "City (Required)",
      "statePlaceholder": "State (Required)",
      "ctaText": "Verify details",
      "invalidEmailError": "Please enter a valid Email Address",
      "genderNotSelectedError": "Please select your gender",
      "employmentNotSelectedError": "Please select employment type",
      "incomeMinError": "Minimum monthly income should be ₹25,000",
      "incomeMaxError": "Maximum monthly income should be ₹5,00,000",
      "invalidPincodeError": "Please enter a valid 6-digit pincode",
      "technicalError": "Something went wrong. Please retry"
    },
    "loader": {
      "title": "Curating Loan Offer for you",
      "subtitleLine1": "Please wait,",
      "subtitleLine2": "it will take just few more seconds",
      "waitPrefixText": "Please wait as this may take",
      "waitHighlightSeconds": 45,
      "waitSuffixText": "to complete",
      "safeVisualPath": "/assets/error-pages/pl-loader-safe.webp",
      "waitIconPath": "/assets/error-pages/brewaitIcon.svg",
      "sheetVisualPath": "/assets/error-pages/brefile1.svg"
    },
    "breOfferScreen": {
  "pageTitle": "Personal loans",
  "continueCtaText": "Continue",
  "loaderTitle": "Curating Loan Offer for you",
  "loaderSubtitleTop": "Please wait,",
  "loaderSubtitleBottom": "it will take just few more seconds",
  "loaderIconAlt": "loading",
  "offerCardCongratsText": "Congratulations",
  "offerCardCongratsIconLeft": "🎉",
  "offerCardCongratsIconRight": "🎉",
  "offerCardDescription": "we have Instant Personal Loan Offer up to",
  "offerCardEmiLabelText": "Monthly EMI starts from",
  "offerCardImagealt": "Offer image",
  "infoBannerText": "Get loan amount in your bank in a few minutes",
  "disclaimerText": "This offer is indicative*",
  "footerInfoText": "Get loan amount in your bank in a few minutes",
  "footerClockIconAlt": "Clock",
  "loaderIconPath": "/assets/personal-loan/icons/offerloading.png",
  "offerCardImagesrc": "/assets/personal-loan/icons/offercash.svg",
  "clockIconPath": "/assets/personal-loan/icons/clock.png"
},
"lreMarketplaceScreen": {
  "pageTitle": "Personal loans",
  "sectionTitle": "Loan offers for you",
  "rankingText": "Ranking based on loan amount provided by lenders",
  "viewAllText": "View all",
  "sidebarOfferLimit": 2,
  "applyNowText": "Apply now",
  "viewKfsText": "View KFS",
  "amountDisclaimerText": "Amount is indicative*",
  "loanAmountLabel": "Loan amount",
  "monthlyEmiLabel": "Monthly EMI",
  "tenureLabel": "Tenure",
  "aprLabel": "APR",
  "infoRowText": "What is KFS & APR?",
  "definitionsTitle": "Important definitions",
  "definitionsCloseTextMobile": "Close",
  "definitionsCloseTextDesktop": "Got it",
  "ineligibleLendersTitle": "Lenders checked",
  "noOfferTitle": "No offers available",
  "noOfferDescription": "These lenders were unable to provide an offer at this time.",
  "noOfferCloseText": "Close",
  "definitions": [
    {
      "id": "kfs",
      "label": "KFS",
      "highlightedTerm": "Key Facts Statement (KFS)",
      "description": "is a summary of important loan terms like interest rate, fees, and repayment details."
    },
    {
      "id": "apr",
      "label": "APR",
      "highlightedTerm": "Annual Percentage Rate (APR)",
      "description": "for loans is the inclusive annualized rate that reflects the total cost of borrowing, including interest, fees, and operational expenses."
    }
  ],
  "noOfferLenderIcons": [],
  "lenderLogos": {
    "Ring": "/assets/personal-loan/icons/ring-logo.png",
    "Fibe": "/assets/personal-loan/icons/fibe-logo.png",
    "Prefr": "/assets/personal-loan/icons/prefr-logo.png",
    "ABCL": "/assets/personal-loan/icons/abc.png",
    "abcl": "/assets/personal-loan/icons/abc.png"
  },
  "lenderLogosListView": {
      "Ring": getAssetPath("/assets/personal-loan/icons/ring-logo.png"),
      "Fibe": getAssetPath("/assets/personal-loan/icons/fibe-logo.png"),
      "Prefr": getAssetPath("/assets/personal-loan/icons/prefr-logo.png"),
      "ABCL": getAssetPath("/assets/personal-loan/icons/abc.png"),
      "abcl": getAssetPath("/assets/personal-loan/icons/abc.png"),
    }
}
  }
}
```

---

## 4. Notes

| Item | Detail |
|------|--------|
| Fallback source | `src/app/personal/customer/@orchestratorContent/apply/content/fallback.ts` |
| CMS transformer | `src/app/personal/customer/@orchestratorContent/apply/content/index.ts` |
| Fallback behavior | If CMS is unavailable or content is empty, `FALLBACK_APPLY_JOURNEY_CONTENT` is returned |
| Supported response shape | Transformer supports both Strapi `data: []` and `data: {}` styles |