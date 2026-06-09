# PreQuote Buy Fallback CMS Requirements

---

**Date:** 2026-04-06
**Purpose:** Sync UAT Strapi with LOCAL configuration for PreQuote Buy fallback journey content

## Table of Contents

1. [Overview](#1-prequote-buy-page-overview)
2. [Content Keys (Buy Flow)](#content-keys-buy-flow)
3. [Pages (Phase 1)](#pages-phase-1)
	- [Page - Capture Vehicle Expiry](#page---capture-vehicle-expiry)
	- [Page - Capture Own Damage Policy Expired](#page---capture-own-damage-policy-expired)
	- [Page - Capture Own Damage Date](#page---capture-own-damage-date)
	- [Page - Capture Vehicle Claim](#page---capture-vehicle-claim)
	- [Page - No Claim Bonus](#page---no-claim-bonus)
	- [Page - Capture Policy Type Details](#page---capture-policy-type-details)
	- [Page - Capture Policy Claim Details](#page---capture-policy-claim-details)
4.  [Sample API Response](#sample-api-response)[Summary](#summary)


---


## 1. PreQuote Buy Page Overview

**Content Type:** `insurance-buy-page`
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys (Buy Flow)

| Page Name | CMS Key | Content Type |
|-----------|---------|--------------|
| Capture Vehicle Expiry | `captureVehicleExpiry` | page |
| Capture Own Damage Policy Expired | `captureOwnDamagePolicyExpired` | page |
| Capture Own Damage Date | `captureOwnDamageDate` | page |
| Capture Vehicle Claim | `captureVehicleClaim` | page |
| No Claim Bonus | `noClaimBonus` | page |
| Capture Policy Type Details | `capturePolicyTypeDetails` | page |
| Capture Policy Claim Details | `capturePolicyClaimDetails` | page |

---

## Pages (Phase 1)

### Page - Capture Vehicle Expiry

**CMS Key:** `captureVehicleExpiry`
**Fallback Constant:** `DEFAULT_CAPTURE_VEHICLE_EXPIRY_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    └── questions (Object)
        └── policyExpired (Object)
            ├── id (String)
            ├── question (String)
            └── options (Array, Repeatable)
                ├── order (Integer)
                ├── label (String)
                └── value (String)
```

#### Sample JSON Data
```json
{
	"captureVehicleExpiry": {
		"enabled": true,
		"content": 
			{
				"title": "Policy Details",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with vehicle policy details",
				"questions": {
					"policyExpired": {
						"id": "policy-expired-question",
						"question": "Has your policy expired?",
						"options": [
							{ "order": 1, "label": "Yes", "value": "yes" },
							{ "order": 2, "label": "No", "value": "no" }
						]
					}
				}
			}
		
	}
}
```

---

### Page - Capture Own Damage Policy Expired

**CMS Key:** `captureOwnDamagePolicyExpired`
**Fallback Constant:** `DEFAULT_CAPTURE_OWN_DAMAGE_POLICY_EXPIRED_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    └── questions (Object)
        └── ownDamagePolicyExpired (Object)
            ├── id (String)
            ├── question (String)
            ├── subtext (String, Optional)
            └── options (Array, Repeatable)
                ├── order (Integer)
                ├── label (String)
                └── value (String)
```

#### Sample JSON Data
```json
{
	"captureOwnDamagePolicyExpired": {
		"enabled": true,
		"content": 
			{
				"title": "Car insurance",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with own damage policy details",
				"questions": {
					"ownDamagePolicyExpired": {
						"id": "own-damage-policy-expired-question",
						"question": "Has your own damage policy expired?",
						"subtext": "Your policy may be expired. Accurate information means better cover and quicker claims.",
						"options": [
							{ "order": 1, "label": "Yes", "value": "yes" },
							{ "order": 2, "label": "No", "value": "no" }
						]
					}
				}
			}
	}
}
```

---

### Page - Capture Own Damage Date

**CMS Key:** `captureOwnDamageDate`
**Fallback Constant:** `DEFAULT_CAPTURE_OWN_DAMAGE_DATE_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── infoBannerMessage (String)
    ├── infoBannerIcon (String,Optional)
    ├── questionText (String)
    ├── dateInputLabel (Integer)
    ├── dateInputPlaceholder (Integer)
    └── defaultLogoUrl (String,Optional)
```

#### Sample JSON Data
```json
{
	"captureOwnDamageDate": {
		"enabled": true,
		"content": 
			{
				"title": "Car insurance",
				"submitButtonText": "Confirm",
				"helpAriaLabel": "Get help with own damage policy expiry date",
				"infoBannerMessage": "Verify expiry date to keep your policy active",
				"infoBannerIcon": "white-alert-rhombus",
				"questionText": "What is your Own Damage policy expiry date?",
				"dateInputLabel": "DD/MM/YYYY",
				"dateInputPlaceholder": "DD/MM/YYYY",
				"defaultLogoUrl": "/assets/landing/motor-policy-icon.png"
			}
		
	}
}
```

---

### Page - Capture Vehicle Claim

**CMS Key:** `captureVehicleClaim`
**Fallback Constant:** `DEFAULT_CAPTURE_VEHICLE_CLAIM_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    └── questions (Object)
        └── previousClaim (Object)
            ├── id (String)
            ├── question (String)
            └── options (Array, Repeatable)
                ├── order (Integer)
                ├── label (String)
                └── value (String)
```

#### Sample JSON Data
```json
{
	"captureVehicleClaim": {
		"enabled": true,
		"content": 
			{
				"title": "Claim History",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with vehicle claim history",
				"questions": {
					"previousClaim": {
						"id": "previousclaim-question",
						"question": "Have you made a claim in the previous year?",
						"options": [
							{ "order": 1, "label": "Yes", "value": "yes" },
							{ "order": 2, "label": "No", "value": "no" }
						]
					}
				}
			}
		
	}
}
```

---

### Page - No Claim Bonus

**CMS Key:** `noClaimBonus`
**Fallback Constant:** `DEFAULT_NO_CLAIM_BONUS_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── infoTooltipLabel (String)
    ├── showInfoBanner (Boolean)
    ├── infoBannerMessage (String)
    └── noClaimBonusOptions (Array, Repeatable)
        ├── order (Integer)
        ├── id (String)
        ├── label (String)
        └── description (String)
```

#### Sample JSON Data
```json
{
	"noClaimBonus": {
		"enabled": true,
		"content": 
			{
				"title": "Car insurance",
				"submitButtonText": "Check price",
				"helpAriaLabel": "Get help with no claim bonus",
				"infoTooltipLabel": "No Claim Bonus (NCB) is a discount offered by insurers for not making claims.",
				"showInfoBanner": true,
				"infoBannerMessage": "If you select the wrong NCB, the discount amount will be adjusted during claims",
				"noClaimBonusOptions": [
					{
						"order": 1,
						"id": "ncb-0",
						"label": "0%",
						"description": "First time buyer or made a claim"
					},
					{
						"order": 2,
						"id": "ncb-20",
						"label": "20%",
						"description": "No claims in last 1 year"
					},
					{
						"order": 3,
						"id": "ncb-25",
						"label": "25%",
						"description": "No claims in last 2 years"
					},
					{
						"order": 4,
						"id": "ncb-35",
						"label": "35%",
						"description": "No claims in last 3 years"
					},
					{
						"order": 5,
						"id": "ncb-45",
						"label": "45%",
						"description": "No claims in last 4 years"
					},
					{
						"order": 6,
						"id": "ncb-50",
						"label": "50%",
						"description": "No claims in last 5+ years"
					}
				]
			}
		
	}
}
```

---

### Page - Capture Policy Type Details

**CMS Key:** `capturePolicyTypeDetails`
**Fallback Constant:** `DEFAULT_CAPTURE_POLICY_TYPE_DETAILS_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── headerTitle (String)
    └── planData (Object)
        ├── comprehensive (Object)
        │   ├── label (String)
        │   └── benefits (Array of Strings)
        └── thirdParty (Object)
            ├── label (String)
            └── benefits (Array of Strings)
```

#### Sample JSON Data
```json
{
	"capturePolicyTypeDetails": {
		"enabled": true,
		"content": 
			{
				"order": 1,
				"title": "Select Policy Type",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with selecting policy type",
				"headerTitle": "What was your previous policy's plan type?",
				"planData": {
					"comprehensive": {
						"label": "Comprehensive cover",
						"benefits": [
							"Covers Damage to your vehicle",
							"Covers Damages caused by your Vehicle to any Third-Party",
							"Cashless claims at 9000+ garages"
						]
					},
					"thirdParty": {
						"label": "Third-party",
						"benefits": [
							"Only covers damages to third-party vehicles",
							"Protects you from third-party liabilities"
						]
					}
				}
			}
		
	}
}
```

---

### Page - Capture Policy Claim Details

**CMS Key:** `capturePolicyClaimDetails`
**Fallback Constant:** `DEFAULT_CAPTURE_POLICY_CLAIM_DETAILS_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    └── questions (Object)
        └── policyExpiredOver90Days (Object)
            ├── id (String)
            ├── question (String)
            ├── subtext (String, Optional)
            └── options (Array, Repeatable)
                ├── order (Integer)
                ├── label (String)
                └── value (String)
```

#### Sample JSON Data
```json
{
	"capturePolicyClaimDetails": {
		"enabled": true,
		"content": 
			{
				"title": "Policy Expiry Details",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with policy expiry details",
				"questions": {
					"policyExpiredOver90Days": {
						"id": "policy-expired-over-90-days-question",
						"question": "Has your policy expired for more than 90 days?",
						"subtext": "Your policy may be expired, Accurate information will help us fetch the right quote",
						"options": [
							{ "order": 1, "label": "Yes", "value": "yes" },
							{ "order": 2, "label": "No", "value": "no" }
						]
					}
				}
			}
		
	}
}
```

---

## Sample API Response

```json
{
	"data": [
		{
			"id": 1,
			"subProduct": "motor",
			"buy": {
				"captureVehicleExpiry": {
					"enabled": true,
					"content": {
						"title": "Policy Details",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with vehicle policy details",
						"questions": {
							"policyExpired": {
								"id": "policy-expired-question",
								"question": "Has your policy expired?",
								"options": [
									{ "label": "Yes", "value": "yes" },
									{ "label": "No", "value": "no" }
								]
							}
						}
					}
				},
				"captureOwnDamagePolicyExpired": {
					"enabled": true,
					"content": {
						"title": "Car insurance",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with own damage policy details",
						"questions": {
							"ownDamagePolicyExpired": {
								"id": "own-damage-policy-expired-question",
								"question": "Has your own damage policy expired?",
								"subtext": "Your policy may be expired. Accurate information means better cover and quicker claims.",
								"options": [
									{ "label": "Yes", "value": "yes" },
									{ "label": "No", "value": "no" }
								]
							}
						}
					}
				},
				"captureOwnDamageDate": {
					"enabled": true,
					"content": {
						"title": "Car insurance",
						"submitButtonText": "Confirm",
						"helpAriaLabel": "Get help with own damage policy expiry date",
						"infoBannerMessage": "Verify expiry date to keep your policy active",
						"infoBannerIcon": "white-alert-rhombus",
						"questionText": "What is your Own Damage policy expiry date?",
						"dateInputLabel": "DD/MM/YYYY",
						"dateInputPlaceholder": "DD/MM/YYYY",
						"defaultLogoUrl": "/assets/landing/motor-policy-icon.png"
					}
				},
				"captureVehicleClaim": {
					"enabled": true,
					"content": {
						"title": "Claim History",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with vehicle claim history",
						"questions": {
							"previousClaim": {
								"id": "previousclaim-question",
								"question": "Have you made a claim in the previous year?",
								"options": [
									{ "label": "Yes", "value": "yes" },
									{ "label": "No", "value": "no" }
								]
							}
						}
					}
				},
				"noClaimBonus": {
					"enabled": true,
					"content": {
						"title": "Car insurance",
						"submitButtonText": "Check price",
						"helpAriaLabel": "Get help with no claim bonus",
						"infoTooltipLabel": "No Claim Bonus (NCB) is a discount offered by insurers for not making claims.",
						"showInfoBanner": true,
						"infoBannerMessage": "If you select the wrong NCB, the discount amount will be adjusted during claims",
						"noClaimBonusOptions": [
							{
								"id": "ncb-0",
								"label": "0%",
								"description": "First time buyer or made a claim"
							},
							{
								"id": "ncb-20",
								"label": "20%",
								"description": "No claims in last 1 year"
							},
							{
								"id": "ncb-25",
								"label": "25%",
								"description": "No claims in last 2 years"
							},
							{
								"id": "ncb-35",
								"label": "35%",
								"description": "No claims in last 3 years"
							},
							{
								"id": "ncb-45",
								"label": "45%",
								"description": "No claims in last 4 years"
							},
							{
								"id": "ncb-50",
								"label": "50%",
								"description": "No claims in last 5+ years"
							}
						]
					}
				},
				"capturePolicyTypeDetails": {
					"enabled": true,
					"content": {
						"title": "Select Policy Type",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with selecting policy type",
						"headerTitle": "What was your previous policy's plan type?",
						"planData": {
							"comprehensive": {
								"label": "Comprehensive cover",
								"benefits": [
									"Covers Damage to your vehicle",
									"Covers Damages caused by your Vehicle to any Third-Party",
									"Cashless claims at 9000+ garages"
								]
							},
							"thirdParty": {
								"label": "Third-party",
								"benefits": [
									"Only covers damages to third-party vehicles",
									"Protects you from third-party liabilities"
								]
							}
						}
					}
				},
				"capturePolicyClaimDetails": {
					"enabled": true,
					"content": {
						"title": "Policy Expiry Details",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with policy expiry details",
						"questions": {
							"policyExpiredOver90Days": {
								"id": "policy-expired-over-90-days-question",
								"question": "Has your policy expired for more than 90 days?",
								"subtext": "Your policy may be expired, Accurate information will help us fetch the right quote",
								"options": [
									{ "label": "Yes", "value": "yes" },
									{ "label": "No", "value": "no" }
								]
							}
						}
					}
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

