# PL Dashboard CMS — New Field

## Content-Type: personal-loan-dashboard-pages

**Collection Name:** `personal-loan-dashboard-pages`
**Singular Name:** `personal-loan-dashboard-pages`
**Plural Name:** `personal-loan-dashboard-pages`
**Draft & Publish:** Enabled

**Component:** `dashboard.calculator-labels` (nested under `plCalculatorSidebar.labels`)

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/personal-loan-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/personal-loan-dashboard-pages` | List all dashboards |
| GET | `/api/personal-loan-dashboard-pages/:id` | Get single dashboard by ID |
| POST | `/api/personal-loan-dashboard-pages` | Create new dashboard |
| PUT | `/api/personal-loan-dashboard-pages/:id` | Update dashboard content |
| DELETE | `/api/personal-loan-dashboard-pages/:id` | Delete dashboard |

late=*
```

---

## New Field

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `resultsDisclaimerText` | string | Yes | `"The values mentioned are for indicative purposes only."` |

Add this single key to the `dashboard.calculator-labels` component. No other changes.

---

## API Response Example

```json
{
  "plCalculatorSidebar": {
    "ranges": {
      "tenureMin": 12,
      "tenureMax": 60,
      "tenureDefault": 36,
      "loanAmountMin": 50000,
      "loanAmountMax": 1000000,
      "loanAmountDefault": 800000,
      "emiAmountMin": 1000,
      "emiAmountMax": 25000,
      "emiAmountDefault": 9500,
      "roiMin": 10,
      "roiMax": 30,
      "roiDefault": 10.99
    },
    "labels": {
      "headerTitle": "Personal Loan",
      "emiCalculatorHeaderTitle": "Personal loan EMI calculator",
      "loanAmountCalculatorHeaderTitle": "Personal loan amount calculator",
      "helperBannerText": "Use this calculator to plan your instalments better",
      "homeTitle": "Our Calculators",
      "homeSubtitle": "Select a calculator you would like to proceed with",
      "emiCalculatorOptionTitle": "EMI Calculator",
      "loanAmountCalculatorOptionTitle": "Loan Amount Calculator",
      "tenureLabel": "Tenure",
      "tenureSuffix": "in months",
      "loanAmountLabel": "Loan Amount",
      "emiAmountLabel": "EMI Amount",
      "roiLabel": "Rate of interest",
      "roiSuffix": "%*",
      "currencySymbol": "₹",
      "totalPayableLabel": "Total payable amount",
      "estimatedEmiLabel": "Your estimated EMI amount",
      "estimatedLoanAmountLabel": "Your estimated loan amount",
      "principalAmountLabel": "Principal Amount",
      "interestAmountLabel": "Interest Amount",
      "calculateButtonText": "Calculate",
      "applyNowButtonText": "Apply Now",
      "disclaimerText": "Disclaimer : The aforementioned values, calculations and results are for illustrative and informational purposes only, and may vary basis various parameters laid down by Aditya Birla Capital Limited.",
      "resultsDisclaimerText": "The values mentioned are for indicative purposes only.",
      "tenureValidationMessage": "Loan tenure needs to be in the range of {min} to {max} months",
      "loanAmountValidationMessage": "Loan amount needs to be in the range of {min} to {max}",
      "emiAmountValidationMessage": "EMI amount needs to be in the range of {min} to {max}",
      "roiValidationMessage": "ROI should be in the range of {min}-{max}%"
    },
    "icons": {
      "helperBannerIcon": "/assets/personal-loan/icons/helperbannericon.webp",
      "emiCalculatorIcon": "/assets/personal-loan/icons/plcalculator.webp",
      "loanAmountCalculatorIcon": "/assets/personal-loan/icons/plcoins.webp"
    }
  }
}
```
