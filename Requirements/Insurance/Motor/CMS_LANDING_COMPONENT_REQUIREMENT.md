# CMS Components Requirements

---

**Date:** 2026-04-08  
**Purpose:** Define CMS schema and fallback configuration for new components - GetStarted, LearnMoreCards, VehicleBannerCtaButtons, Widget, and AppPromo

## Table of Contents

1. [Overview](#overview)
2. [Source of Truth](#source-of-truth)
3. [Component Keys](#component-keys)
4. [Components (Phase 1)](#components-phase-1)
	- [Component - GetStarted](#component---getstarted)
	- [Component - LearnMoreCards](#component---learnmorecards)
	- [Component - Widget](#component---widget)
	- [Component - AppPromo](#component---apppromo)
6. [Sample Entry (Seed Data)](#sample-entry-seed-data)
7. [Sample API Response](#sample-api-response)
8. [Component Hierarchy](#component-hierarchy)

---

**Content Type:** `insurance-landing-page`  
**API Endpoint:** `GET /api/insurance-landing-pages?filters[subProduct][$eq]=motor&populate=*`

---

## Component Keys

| Component Name | CMS Key  | Content Type |
|----------------|---------|--------------|
| GetStarted | `getStarted`  | `component` |
| LearnMoreCards | `learnMoreCards`  | `component` |
| Widget | `widget`  | `component` |
| AppPromo | `appPromo`  | `component` |

---

## Components (Phase 1)

### Component - GetStarted

**CMS Key:** `getStarted`  
**Fallback Constant:** `DEFAULT_GET_STARTED_CONTENT`  
**Content Type:** `component`

#### Component Structure
```
├── enabled (Boolean)
└── content (Array, Repeatable)
    │   ├── order (Integer)
    │   ├── id (String)
    │   ├── label (String, optional)
    │   ├── description (String, optional)
    │   ├── tipMessage (String, optional)
    │   └── steps (Array, repeatable)
    │       ├── order (Integer)
    │       ├── id (String)
    │       ├── number (Integer)
    │       ├── title (String)
    │       ├── description (String)
    │       └── icon (String, optional)
```


#### Sample JSON Data
```json
{
  "getStarted": {
    "id": "getStarted",
    "enabled": true,
    "content": {
      "tabs": [
        {
          "id": "buy-online",
          "label": "How to Buy Insurance Online?",
          "description": "Buying a motor insurance policy through Aditya Birla Capital Digital is simple, secure, and completely digital.",
          "order": 1,
          "steps": [
            {
              "id": "login",
              "number": 1,
              "title": "Log in to the ABCD App or Website",
              "description": "Sign in with your existing credentials or register quickly as a new user to get started.",
              "icon": "${LANDING_ASSETS}/motor-login-icon.png",
              "order": 1
            },
            {
              "id": "vehicle-details",
              "number": 2,
              "title": "Enter Vehicle Details",
              "description": "Fill in important details like your vehicle's model, registration number, fuel type, and manufacturing year.",
              "icon": "${LANDING_ASSETS}/motor-vehicle-details-icon.png",
              "order": 2
            },
            {
              "id": "compare-plans",
              "number": 3,
              "title": "Compare Plans and Customise Add-Ons",
              "description": "Browse through available plans, compare features and premiums, and select relevant add-ons. Adjust the IDV (Insured Declared Value) to suit your needs.",
              "icon": "${LANDING_ASSETS}/motor-compare-plans-icon.png",
              "order": 3
            },
            {
              "id": "payment",
              "number": 4,
              "title": "Make Secure Online Payment",
              "description": "Use your preferred payment mode—debit/credit card, UPI, or net banking—for a fast and safe vehicle insurance online payment.",
              "icon": "${LANDING_ASSETS}/motor-payment-icon.png",
              "order": 4
            },
            {
              "id": "policy",
              "number": 5,
              "title": "Get Instant Policy Issuance",
              "description": "Once the payment is completed, your vehicle insurance policy is instantly generated and sent to your registered email and app inbox.",
              "icon": "${LANDING_ASSETS}/motor-policy-icon.png",
              "order": 5
            }
          ]
        },
        {
          "id": "renew",
          "label": "How to Renew Insurance?",
          "description": "Renewing your motor insurance policy with Aditya Birla Capital Digital is a smooth, paperless process.",
          "order": 2,
          "tipMessage": "Tip: Renew before expiry to retain your No Claim Bonus (NCB) and avoid vehicle inspection delays.",
          "steps": [
            {
              "id": "login-renew",
              "number": 1,
              "title": "Log In",
              "description": "Access your account on the ABCD app or website using your login credentials. New users can register in minutes",
              "icon": "${LANDING_ASSETS}/motor/motor-renew-login-icon.png",
              "order": 1
            },
            {
              "id": "navigate",
              "number": 2,
              "title": "Navigate to Motor Insurance Section",
              "description": "Go to the Motor Insurance tab under the Insurance category and choose your existing policy or browse new options.",
              "icon": "${LANDING_ASSETS}/motor/motor-renew-navigate-icon.png",
              "order": 2
            },
            {
              "id": "policy-details",
              "number": 3,
              "title": "Enter Previous Policy Details",
              "description": "Provide your old vehicle insurance policy number and vehicle details to fetch and compare the best renewal options available.",
              "icon": "${LANDING_ASSETS}/motor/motor-renew-policy-icon.png",
              "order": 3
            },
            {
              "id": "customize",
              "number": 4,
              "title": "Compare and Customise Your Plan",
              "description": "Modify your IDV, select suitable add-ons like NCB Protection, and finalise your preferred motor vehicle insurance coverage.",
              "icon": "${LANDING_ASSETS}/motor/motor-claim-vehicle-icon.png",
              "order": 4
            },
            {
              "id": "payment-renew",
              "number": 5,
              "title": "Make Secure Payment",
              "description": "Proceed with your vehicle insurance online payment using UPI, debit/credit card, or net banking. Once done, your renewed policy will be instantly shared with your email and app.",
              "icon": "${LANDING_ASSETS}/motor-renew-policy-icon.png",
              "order": 5
            }
          ]
        },
        {
          "id": "claim",
          "label": "How to Claim Insurance?",
          "description": "Filing a motor insurance claim today is simple and stress-free.",
          "order": 3,
          "steps": [
            {
              "id": "notify",
              "number": 1,
              "title": "Notify the Insurer",
              "description": "Intimate your insurer about the incident at the earliest through their toll-free number or email. Early notification helps in quicker processing of your claim.",
              "icon": "${LANDING_ASSETS}/motor/motor-renew-policy-icon.png",
              "order": 1
            },
            {
              "id": "vehicle-details-claim",
              "number": 2,
              "title": "Enter Vehicle Details",
              "description": "Fill in important details like your vehicle's model, registration number, fuel type, and manufacturing year.",
              "icon": "${LANDING_ASSETS}/motor/motor-claim-vehicle-icon.png",
              "order": 2
            },
            {
              "id": "repair",
              "number": 3,
              "title": "Vehicle Repair & Final Submission",
              "description": "You can get your vehicle repaired at a network garage for cashless service, or at a garage of your choice and later submit the final bill for reimbursement.",
              "icon": "${LANDING_ASSETS}/motor-renew-payment-icon.png",
              "order": 3
            },
            {
              "id": "settlement",
              "number": 4,
              "title": "Claim Settlement",
              "description": "Cashless Claims: The insurer directly settles the bill with the garage. Reimbursement Claims: You pay the repair costs upfront and the insurer reimburses you after verification.",
              "icon": "${LANDING_ASSETS}/motor/motor-claim-vehicle-icon.png",
              "order": 4
            }
          ]
        }
      ]
    }
  }
}
```

---

### Component - LearnMoreCards

**CMS Key:** `learnMoreCards`  
**Fallback Constant:** `DEFAULT_LEARN_MORE_CARDS_CONTENT`  
**Content Type:** `component`

#### Component Structure
```
├── enabled (Boolean)
└── content
    ├── order (Integer)
    ├── items (Array, repeatable)
        ├── background (String)
        ├── heading (String)
        ├── iconSrc (String)
        ├── iconAlt (String)
        └── body (Object)
           ├── type (String, enum: "paragraph", "table")
           ├── content (Array of Strings) - for type "paragraph"
           ├── headers (Array of Strings) - for type "table"
           └── rows (Array of Arrays) - for type "table"
```



#### Sample JSON Data
```json
{
	"learnMoreCards": {
		"enabled": true,
		"items": [
			{
				"order": 1,
				"id": "why-insurance-mandatory",
				"background": "linear-gradient(90deg, #FFE7E5 0%, #FFFFFF 100%)",
				"heading": "Why is Vehicle Insurance Mandatory \nin India?",
				"iconSrc": "${LANDING_ASSETS}/Learn1.png",
				"iconAlt": "Vehicle insurance",
				"body": {
					"type": "paragraph",
					"content": [
						"In India, having a valid motor vehicle insurance policy is not just a safety measure—it is a legal requirement under the Motor Vehicles Act, 1988.",
						"Every vehicle operating on public roads must be covered by at least a Third-Party Liability insurance policy, which ensures that if your vehicle causes injury, death, or property damage to another person, the financial responsibility is covered by your motor insurance provider.",
						"This law protects not only the victim of the accident but also the vehicle owner by absorbing hefty legal or compensation costs. Without valid vehicle insurance, any accident can lead to substantial out-of-pocket expenses and even legal trouble.",
						"Failure to carry a valid vehicle insurance policy can result in penalties, suspension of your driving licence, or even imprisonment.",
						"Whether you are buying a new vehicle or continuing with your current one, timely vehicle insurance renewal is a must.",
						"In short, motor insurance isn't just about protection—it's a legal necessity designed to keep all road users financially and legally secure."
					]
				}
			},
			{
				"order": 2,
				"id": "common-terminologies",
				"background": "linear-gradient(90deg, #FFF4D9 0%, #FFFFFF 100%)",
				"heading": "Common Motor \n Insurance Terminologies",
				"iconSrc": "${LANDING_ASSETS}/learn2.png",
				"iconAlt": "Common Terms",
				"body": {
					"type": "table",
					"headers": ["Term", "Meaning"],
					"rows": [
						"IDV (Insured Declared Value)", "The current market value of your vehicle. This is the maximum amount you can claim if your vehicle is lost or stolen. Choosing the right IDV directly impacts your premium and payout.",
						"Third-Party Liability", "A mandatory component of every motor insurance policy, it covers legal and financial liabilities if your vehicle causes injury, death, or property damage to others.",
						"Add-ons", "Optional features like Zero Depreciation, Engine Protection, and Roadside Assistance that increase your premium but improve coverage.",
						"Comprehensive Policy", "A policy that provides dual protection—own damage cover and third-party liability—making it the most inclusive form of vehicle insurance.",
						"Deductibles", "The portion of the claim amount you agree to pay from your pocket. Compulsory or Voluntary.",
						"No Claim Bonus (NCB)", "A discount of up to 50% on the renewal premium for every claim-free year."
					]
				}
			}
		]
	}
}
```

---

### Component - Widget

**CMS Key:** `widget`  
**Fallback Constant:** `DEFAULT_WIDGET_CONTENT`  
**Content Type:** `component`

#### Component Structure
```
├── enabled (Boolean)
└── content
    ├── navigationVariant (String, enum: "tabs", "buttons")
    ├── maxResendAttempts (Integer)
    ├── maxResendMessage (String)
    ├── consentConfig (Object)
    │   ├── label (String)
    │   ├── termsText (String)
    │   ├── termsUrl (String)
    │   ├── privacyText (String)
    │   └── privacyUrl (String)
    ├── widgetTrustBannerText (String)
    ├── widgetIsDisabled (Boolean)
    └── tabs (Array, repeatable)
        ├── order (Integer)
        ├── id (String)
        ├── label (String)
        ├── tabImage (String)
        ├── insuranceTitle (String)
        ├── icon (String)
        └── startingPrice (String)
```

#### Sample JSON Data
```json
{
	"widget": {
		"enabled": true,
		"navigationVariant": "buttons",
		"maxResendAttempts": 3,
		"maxResendMessage": "Maximum resend attempts reached. Please try again later.",
		"consentConfig": {
			"label": "I agree with the",
			"termsText": "Terms & Conditions",
			"termsUrl": "https://www.adityabirlacapital.com/abcd/terms-conditions",
			"privacyText": "Privacy Policy",
			"privacyUrl": "https://www.adityabirlacapital.com/abcd/privacy-policy"
		},
		"widgetTrustBannerText": "Verified partners. 100% transparent. Fully secure.",
		"widgetIsDisabled": false,
		"tabs": [
			{
				"id": "car",
				"label": "Car insurance",
				"order": 1,
				"tabImage": "${LANDING_ASSETS}/motor/car-side.svg",
				"insuranceTitle": "Get car insurance now!",
				"icon": "${LANDING_ASSETS}/motor/carIcon.png",
				"startingPrice": "₹2,000/year*"
			},
			{
				"id": "bike",
				"label": "Bike insurance",
				"order": 2,
				"tabImage": "${LANDING_ASSETS}/motor/motorbike.svg",
				"insuranceTitle": "Get bike insurance now!",
				"icon": "${LANDING_ASSETS}/motor/bikeIcon.png",
				"startingPrice": "₹1,500/year*"
			}
		]
	}
}
```

---

### Component - AppPromo

**CMS Key:** `appPromo`  
**Fallback Constant:** `DEFAULT_APP_PROMO_CONTENT`  
**Content Type:** `component`

#### Component Structure
```
├── enabled (Boolean)
└── content
    ├── title (String)
    ├── subtitle (String)
    ├── houseLogoSrc (String)
    ├── qrSrc (String)
    ├── phoneImageSrc (String)
    └── ctaButtons (Array, repeatable)
        ├── order (Integer)
        ├── label (String)
        ├── link (String)
        ├── iconSrc (String)
        └── iconAlt (String)
```




#### Sample JSON Data
```json
{
	"appPromo": {
		"enabled": true,
		"title": "Everything Finance\nas simple as\nABCD",
		"subtitle": "Download the ABCD app and start doing more with your money everyday",
		"houseLogoSrc": "${ASSETS_BASE}/vehicle-insurance/abcd-logo.png",
		"qrSrc": "${ASSETS_BASE}/vehicle-insurance/qr-code.png",
		"phoneImageSrc": "${ASSETS_BASE}/gold-loan/gl-finanace.png",
		"ctaButtons": [
			{
				"order": 1,
				"label": "App Store",
				"link": "https://apps.apple.com/",
				"iconSrc": "${ASSETS_BASE}/mobile-nav/apple.svg",
				"iconAlt": "Apple App Store"
			},
			{
				"order": 2,
				"label": "Google Play",
				"link": "https://play.google.com/store",
				"iconSrc": "${ASSETS_BASE}/mobile-nav/google.svg",
				"iconAlt": "Google Play Store"
			}
		]
	}
}
```

---