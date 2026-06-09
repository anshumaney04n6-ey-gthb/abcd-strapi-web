# Proposal Buy Fallback CMS Requirements

---

**Date:** 2026-04-08  
**Purpose:** Sync UAT Strapi with LOCAL configuration for Proposal Buy fallback journey content

## Table of Contents

1. [Overview](#1-renewalflow-buy-page-overview)
2. [Content Keys (Buy Flow)](#content-keys-buy-flow)
3. [Pages (Phase 1)](#pages-phase-1)
	- [Page - Capture Vehicle Additional Details](#page---capture-vehicle-additional-details)
	- [Page - Capture Odometer Readings](#page---capture-odometer-readings)
	- [Page - Capture Owner Details](#page---capture-owner-details)
	- [Page - Capture Nominee Details](#page---capture-nominee-details)
	- [Page - Capture Previous Policy Details](#page---capture-previous-policy-details)
	- [Page - Capture Third Party Policy Details](#page---capture-third-party-policy-details)
4. [Sample API Response](#sample-api-response)


---


## 1. Renewalflow Buy Page Overview

**Content Type:** `insurance-journey-pages`  
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys (Buy Flow)

| Page Name | CMS Key | Content Type |
|-----------|---------|--------------|
| Capture Vehicle Additional Details | `captureVehicleAdditionalDetails` | page |
| Capture Odometer Readings | `captureOdometerReadings` | page |
| Capture Owner Details | `captureOwnerDetails` | page |
| Capture Nominee Details | `captureNomineeDetails` | page |
| Capture Previous Policy Details | `capturePreviousPolicyDetails` | page |
| Capture Third Party Policy Details | `captureThirdPartyPolicyDetails` | page |

---


## Pages (Phase 1)


### Page - Capture Vehicle Additional Details

**CMS Key:** `captureVehicleAdditionalDetails`  
**Fallback Constant:** `DEFAULT_CAPTURE_VEHICLE_ADDITIONAL_DETAILS_CONTENT`

#### Page Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── heading (String)
    ├── showRegistrationNumberField (Boolean)
    ├── showEngineNumberField (Boolean)
    ├── showChassisNumberField (Boolean)
    ├── showRegistrationDateField (Boolean)
    ├── registrationDatePickerEnabled (Boolean)
    ├── registrationNumberDisabled (Boolean)
    ├── engineNumberDisabled (Boolean)
    ├── chassisNumberDisabled (Boolean)
    ├── registrationDateDisabled (Boolean)
    ├── showRadioField (Boolean)
    ├── radioLabel (String)
    └── radioOptions (Array, repeatable)
        ├── order (Integer)
        ├── value (String)
        └── label (String)
```

#### Sample JSON Data
```json
{
	"captureVehicleAdditionalDetails": {
		"enabled": true,
		"content": {
			"title": "{VehicleType} insurance",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with vehicle additional details",
			"heading": "Car Details",
			"showRegistrationNumberField": true,
			"showEngineNumberField": true,
			"showChassisNumberField": true,
			"showRegistrationDateField": true,
			"registrationDatePickerEnabled": true,
			"registrationNumberDisabled": false,
			"engineNumberDisabled": false,
			"chassisNumberDisabled": false,
			"registrationDateDisabled": false,
			"showRadioField": true,
			"radioLabel": "Was your vehicle purchased with a loan?",
			"radioOptions": [
				{ "order": 1, "value": "yes", "label": "Yes" },
				{ "order": 2, "value": "no", "label": "No" }
			]
		}
	}
}
```


### Page - Capture Odometer Readings

**CMS Key:** `captureOdometerReadings`  
**Fallback Constant:** `DEFAULT_CAPTURE_ODOMETER_READINGS_CONTENT`

#### Page Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── heading (String)
    ├── showOdometerReadingField (Boolean)
    ├── showReadingDateField (Boolean)
    ├── odometerMaxLimit (Integer)
    ├── odometerReadingDisabled (Boolean)
    ├── readingDateDisabled (Boolean)
    ├── readingDatePickerEnabled (Boolean)
    └── promoBar (Object)
        ├── text (String)
        └── icon (Object)
            ├── src (String)
            ├── alt (String)
            └── style (Object)
                ├── width (Integer)
                └── height (Integer)
              
              
```

#### Sample JSON Data
```json
{
	"captureOdometerReadings": {
		"enabled": true,
		"content": {
			"title": "{VehicleType} insurance",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with odometer reading details",
			"heading": "Car details",
			"showOdometerReadingField": true,
			"showReadingDateField": true,
			"odometerMaxLimit": 999999,
			"odometerReadingDisabled": false,
			"readingDateDisabled": false,
			"readingDatePickerEnabled": true,
			"promoBar": {
				"text": "We need your car info as you have selected a pay as you\ndrive policy.",
				"icon": {
					"src": "/assets/motor/alert-rhombus-badge.svg",
					"alt": "alert-rhombus-badge",
					"style": { "width": 12, "height": 12 }
				}
			}
		}
	}
}
```


### Page - Capture Owner Details

**CMS Key:** `captureOwnerDetails`  
**Fallback Constant:** `DEFAULT_CAPTURE_OWNER_DETAILS_CONTENT`

#### Page Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── heading (String)
    ├── showNameField (Boolean)
    ├── showMobileField (Boolean)
    ├── showDobField (Boolean)
    ├── showEmailField (Boolean)
    ├── showPanField (Boolean)
    ├── showGenderField (Boolean)
    ├── showMaritalStatusField (Boolean)
    ├── showOccupationField (Boolean)
    ├── nameDisabled (Boolean)
    ├── dobDisabled (Boolean)
    ├── dobPickerEnabled (Boolean)
    ├── emailDisabled (Boolean)
    ├── panRequired (Boolean)
    ├── panDisabled (Boolean)
    ├── genderDisabled (Boolean)
    ├── maritalStatusDisabled (Boolean)
    ├── occupationDisabled (Boolean)
    ├── genderDropdownTitle (String)
    ├── maritalStatusDropdownTitle (String)
    ├── occupationDropdownTitle (String)
    ├── genderOptions (Array, repeatable)
    │   ├── order (Integer)
    │   ├── id (String)
    │   ├── label (String)
    │   └── value (String)
    ├── maritalStatusOptions (Array, repeatable)
    │   ├── order (Integer)
    │   ├── id (String)
    │   ├── label (String)
    │   └── value (String)
    └── occupationOptions (Array, repeatable)
        ├── order (Integer)
        ├── id (String)
        ├── label (String)
        └── value (String)
```

#### Sample JSON Data
```json
{
	"captureOwnerDetails": {
		"enabled": true,
		"content": {
			"title": "{VehicleType} insurance",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with owner details",
			"heading": "Owner's details",
			"showNameField": true,
			"showMobileField": true,
			"showDobField": true,
			"showEmailField": true,
			"showPanField": true,
			"showGenderField": true,
			"showMaritalStatusField": true,
			"showOccupationField": true,
			"dobPickerEnabled": true,
			"panRequired": true,
			"genderDropdownTitle": "Gender",
			"maritalStatusDropdownTitle": "Marital status",
			"occupationDropdownTitle": "Occupation",
			"genderOptions": [
				{ "order": 1, "id": "male", "label": "Male", "value": "male" },
				{ "order": 2, "id": "female", "label": "Female", "value": "female" },
				{ "order": 3, "id": "other", "label": "Other", "value": "other" }
			],
			"maritalStatusOptions": [
				{ "order": 1, "id": "single", "label": "Single", "value": "single" },
				{ "order": 2, "id": "married", "label": "Married", "value": "married" },
				{ "order": 3, "id": "divorced", "label": "Divorced", "value": "divorced" },
				{ "order": 4, "id": "widowed", "label": "Widowed", "value": "widowed" }
			],
			"occupationOptions": [
				{ "order": 1, "id": "architect", "label": "Architect", "value": "architect" },
				{ "order": 2, "id": "engineer", "label": "Engineer", "value": "engineer" },
				{ "order": 3, "id": "doctor", "label": "Doctor", "value": "doctor" },
				{ "order": 4, "id": "lawyer", "label": "Lawyer", "value": "lawyer" },
				{ "order": 5, "id": "teacher", "label": "Teacher", "value": "teacher" },
				{ "order": 6, "id": "business", "label": "Business", "value": "business" }
			]
		}
	}
}
```


### Page - Capture Nominee Details

**CMS Key:** `captureNomineeDetails`  
**Fallback Constant:** `DEFAULT_CAPTURE_NOMINEE_DETAILS_CONTENT`

#### Page Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── heading (String)
    ├── showNameField (Boolean)
    ├── showAgeField (Boolean)
    ├── showRelationshipField (Boolean)
    ├── nameDisabled (Boolean)
    ├── ageDisabled (Boolean)
    ├── relationshipDisabled (Boolean)
    ├── relationshipDropdownTitle (String)
    └── relationshipOptions (Array, repeatable)
        ├── order (Integer)
        ├── id (String)
        ├── label (String)
        └── value (String)
```

#### Sample JSON Data
```json
{
	"captureNomineeDetails": {
		"enabled": true,
		"content": {
			"title": "{VehicleType} insurance",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with nominee details",
			"heading": "Nominee details",
			"showNameField": true,
			"showAgeField": true,
			"showRelationshipField": true,
			"relationshipDropdownTitle": "Relationship",
			"relationshipOptions": [
				{ "order": 1, "id": "spouse", "label": "Spouse", "value": "spouse" },
				{ "order": 2, "id": "child", "label": "Child", "value": "child" },
				{ "order": 3, "id": "parent", "label": "Parent", "value": "parent" },
				{ "order": 4, "id": "sibling", "label": "Sibling", "value": "sibling" },
				{ "order": 5, "id": "other", "label": "Other", "value": "other" }
			]
		}
	}
}
```


### Page - Capture Previous Policy Details

**CMS Key:** `capturePreviousPolicyDetails`  
**Fallback Constant:** `DEFAULT_CAPTURE_PREVIOUS_POLICY_DETAILS_CONTENT`

#### Page Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── showExpiryDateField (Boolean)
    ├── showInsurerField (Boolean)
    ├── showPolicyNumberField (Boolean)
    ├── showNcbField (Boolean)
    ├── expiryDateDisabled (Boolean)
    ├── insurerNameDisabled (Boolean)
    ├── policyNumberDisabled (Boolean)
    ├── ncbValueDisabled (Boolean)
    ├── showSavingsBanner (Boolean)
    ├── savingsBannerText (String)
    ├── insurerOptions (Array, repeatable)
    │   ├── order (Integer)
    │   ├── id (String)
    │   ├── label (String)
    │   └── value (String)
    └── ncbOptions (Array, repeatable)
        ├── order (Integer)
        ├── id (String)
        ├── label (String)
        └── value (String)
```

#### Sample JSON Data
```json
{
	"capturePreviousPolicyDetails": {
		"enabled": true,
		"content": {
			"title": "{VehicleType} insurance",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with previous policy details",
			"showExpiryDateField": true,
			"showInsurerField": true,
			"showPolicyNumberField": true,
			"showNcbField": true,
			"showSavingsBanner": false,
			"savingsBannerText": "Woohoo! You just saved Rs350!",
			"insurerOptions": [
				{ "order": 1, "id": "insurer-1", "label": "ABCD Insurance", "value": "abcd" },
				{ "order": 2, "id": "insurer-2", "label": "XYZ Insurance", "value": "xyz" },
				{ "order": 3, "id": "insurer-3", "label": "PQR Insurance", "value": "pqr" }
			],
			"ncbOptions": [
				{ "order": 1, "id": "ncb-0", "label": "0%", "value": "0" },
				{ "order": 2, "id": "ncb-20", "label": "20%", "value": "20" },
				{ "order": 3, "id": "ncb-25", "label": "25%", "value": "25" },
				{ "order": 4, "id": "ncb-35", "label": "35%", "value": "35" },
				{ "order": 5, "id": "ncb-45", "label": "45%", "value": "45" },
				{ "order": 6, "id": "ncb-50", "label": "50%", "value": "50" }
			]
		}
	}
}
```


### Page - Capture Third Party Policy Details

**CMS Key:** `captureThirdPartyPolicyDetails`  
**Fallback Constant:** `DEFAULT_CAPTURE_THIRD_PARTY_POLICY_DETAILS_CONTENT`

#### Page Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── heading (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── showInsurerField (Boolean)
    ├── showPolicyNumberField (Boolean)
    ├── showStartDateField (Boolean)
    ├── showExpiryDateField (Boolean)
    ├── insurerNameDisabled (Boolean)
    ├── policyNumberDisabled (Boolean)
    ├── startDateDisabled (Boolean)
    ├── expiryDateDisabled (Boolean)
    ├── startDatePickerEnabled (Boolean)
    ├── expiryDatePickerEnabled (Boolean)
    ├── insurerOptions (Array, repeatable)
    │   ├── order (Integer)
    │   ├── id (String)
    │   ├── label (String)
    │   └── value (String)
    └── promoBar (Object)
        ├── text (String)
        └── icon (Object)
            ├── src (String)
            ├── alt (String)
            └── style (Object)
                ├── width (Integer)
                └── height (Integer)
```

#### Sample JSON Data
```json
{
	"captureThirdPartyPolicyDetails": {
		"enabled": true,
		"content": {
			"title": "{VehicleType} insurance",
			"heading": "Third-party policy details",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with third-party policy details",
			"showInsurerField": true,
			"showPolicyNumberField": true,
			"showStartDateField": true,
			"showExpiryDateField": true,
			"startDatePickerEnabled": true,
			"expiryDatePickerEnabled": true,
			"insurerOptions": [
				{ "id": "insurer-1", "order": 1, "label": "ABCD Insurance", "value": "abcd" },
				{ "id": "insurer-2", "order": 2, "label": "XYZ Insurance", "value": "xyz" }
			],
			"promoBar": {
				"text": "We need your car info as you have selected a pay as you\ndrive policy.",
				"icon": {
					"src": "/assets/motor/alert-rhombus-badge.svg",
					"alt": "alert-rhombus-badge",
					"style": { "width": 12, "height": 12 }
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
			"captureVehicleAdditionalDetails": {
				"enabled": true,
				"content": {
					"title": "{VehicleType} insurance",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with vehicle additional details",
					"heading": "Car Details",
					"showRegistrationNumberField": true,
					"showEngineNumberField": true,
					"showChassisNumberField": true,
					"showRegistrationDateField": true,
					"registrationDatePickerEnabled": true,
					"registrationNumberDisabled": false,
					"engineNumberDisabled": false,
					"chassisNumberDisabled": false,
					"registrationDateDisabled": false,
					"showRadioField": true,
					"radioLabel": "Was your vehicle purchased with a loan?",
					"radioOptions": [
						{ "order": 1, "value": "yes", "label": "Yes" },
						{ "order": 2, "value": "no", "label": "No" }
					]
				}
			},
			"captureOdometerReadings": {
				"enabled": true,
				"content": {
					"title": "{VehicleType} insurance",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with odometer reading details",
					"heading": "Car details",
					"showOdometerReadingField": true,
					"showReadingDateField": true,
					"odometerMaxLimit": 999999,
					"odometerReadingDisabled": false,
					"readingDateDisabled": false,
					"readingDatePickerEnabled": true,
					"promoBar": {
						"text": "We need your car info as you have selected a pay as you\ndrive policy.",
						"icon": {
							"src": "/assets/motor/alert-rhombus-badge.svg",
							"alt": "alert-rhombus-badge",
							"style": { "width": 12, "height": 12 }
						}
					}
				}
			},
			"captureOwnerDetails": {
				"enabled": true,
				"content": {
					"title": "{VehicleType} insurance",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with owner details",
					"heading": "Owner's details",
					"showNameField": true,
					"showMobileField": true,
					"showDobField": true,
					"showEmailField": true,
					"showPanField": true,
					"showGenderField": true,
					"showMaritalStatusField": true,
					"showOccupationField": true,
					"dobPickerEnabled": true,
					"panRequired": true,
					"genderDropdownTitle": "Gender",
					"maritalStatusDropdownTitle": "Marital status",
					"occupationDropdownTitle": "Occupation",
					"genderOptions": [
						{ "order": 1, "id": "male", "label": "Male", "value": "male" },
						{ "order": 2, "id": "female", "label": "Female", "value": "female" },
						{ "order": 3, "id": "other", "label": "Other", "value": "other" }
					],
					"maritalStatusOptions": [
						{ "order": 1, "id": "single", "label": "Single", "value": "single" },
						{ "order": 2, "id": "married", "label": "Married", "value": "married" },
						{ "order": 3, "id": "divorced", "label": "Divorced", "value": "divorced" },
						{ "order": 4, "id": "widowed", "label": "Widowed", "value": "widowed" }
					],
					"occupationOptions": [
						{ "order": 1, "id": "architect", "label": "Architect", "value": "architect" },
						{ "order": 2, "id": "engineer", "label": "Engineer", "value": "engineer" },
						{ "order": 3, "id": "doctor", "label": "Doctor", "value": "doctor" },
						{ "order": 4, "id": "lawyer", "label": "Lawyer", "value": "lawyer" },
						{ "order": 5, "id": "teacher", "label": "Teacher", "value": "teacher" },
						{ "order": 6, "id": "business", "label": "Business", "value": "business" }
					]
				}
			},
			"captureNomineeDetails": {
				"enabled": true,
				"content": {
					"title": "{VehicleType} insurance",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with nominee details",
					"heading": "Nominee details",
					"showNameField": true,
					"showAgeField": true,
					"showRelationshipField": true,
					"relationshipDropdownTitle": "Relationship",
					"relationshipOptions": [
						{ "order": 1, "id": "spouse", "label": "Spouse", "value": "spouse" },
						{ "order": 2, "id": "child", "label": "Child", "value": "child" },
						{ "order": 3, "id": "parent", "label": "Parent", "value": "parent" },
						{ "order": 4, "id": "sibling", "label": "Sibling", "value": "sibling" },
						{ "order": 5, "id": "other", "label": "Other", "value": "other" }
					]
				}
			},
			"capturePreviousPolicyDetails": {
				"enabled": true,
				"content": {
					"title": "{VehicleType} insurance",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with previous policy details",
					"showExpiryDateField": true,
					"showInsurerField": true,
					"showPolicyNumberField": true,
					"showNcbField": true,
					"showSavingsBanner": false,
					"savingsBannerText": "Woohoo! You just saved Rs350!",
					"insurerOptions": [
						{ "order": 1, "id": "insurer-1", "label": "ABCD Insurance", "value": "abcd" },
						{ "order": 2, "id": "insurer-2", "label": "XYZ Insurance", "value": "xyz" },
						{ "order": 3, "id": "insurer-3", "label": "PQR Insurance", "value": "pqr" }
					],
					"ncbOptions": [
						{ "order": 1, "id": "ncb-0", "label": "0%", "value": "0" },
						{ "order": 2, "id": "ncb-20", "label": "20%", "value": "20" },
						{ "order": 3, "id": "ncb-25", "label": "25%", "value": "25" },
						{ "order": 4, "id": "ncb-35", "label": "35%", "value": "35" },
						{ "order": 5, "id": "ncb-45", "label": "45%", "value": "45" },
						{ "order": 6, "id": "ncb-50", "label": "50%", "value": "50" }
					]
				}
			},
			"captureThirdPartyPolicyDetails": {
				"enabled": true,
				"content": {
					"title": "{VehicleType} insurance",
					"heading": "Third-party policy details",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with third-party policy details",
					"showInsurerField": true,
					"showPolicyNumberField": true,
					"showStartDateField": true,
					"showExpiryDateField": true,
					"startDatePickerEnabled": true,
					"expiryDatePickerEnabled": true,
					"insurerOptions": [
						{ "id": "insurer-1", "order": 1, "label": "ABCD Insurance", "value": "abcd" },
						{ "id": "insurer-2", "order": 2, "label": "XYZ Insurance", "value": "xyz" }
					],
					"promoBar": {
						"text": "We need your car info as you have selected a pay as you\ndrive policy.",
						"icon": {
							"src": "/assets/motor/alert-rhombus-badge.svg",
							"alt": "alert-rhombus-badge",
							"style": { "width": 12, "height": 12 }
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
