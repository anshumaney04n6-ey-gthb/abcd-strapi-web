# KYC Buy Fallback CMS Requirements

---

**Date:** 2026-04-16  
**Purpose:** Define CMS schema and fallback configuration for KYC-related Buy flow components

## Table of Contents

1. [Overview](#1-kyc-buy-page-overview)
2. [Content Keys (Buy Flow)](#content-keys-buy-flow)
3. [Components (Phase 1)](#components-phase-1)
	- [Component - CaptureCkycSuccess](#component---captureckycsuccess)
	- [Component - CollectAddressProof](#component---collectaddressproof)
	- [Component - CaptureAddressDetails](#component---captureaddressdetails)
3. [Sample Entry (Seed Data)](#sample-entry-seed-data)
4. [Sample API Response](#sample-api-response)


---

## 1. KYC Buy Page Overview

**Content Type:** `insurance-journey-pages`  
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys (Buy Flow)

| Component Name | CMS Key | Content Type |
|-----------|---------|--------------|
| Capture CKYC Success | `captureCkycSuccess` | page  |
| Collect Address Proof | `collectAddressProof` | page  |
| Capture Address Details | `captureAddressDetails` | page  |

---

## Components (Phase 1)

### Component - CaptureCkycSuccess

**CMS Key:** `captureCkycSuccess`  
**Fallback Constant:** `DEFAULT_CAPTURE_CKYC_SUCCESS_CONTENT`  

#### Component Structure

```
├── enabled (Boolean)
└── content (component)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── successHeading (String)
    ├── successSubtext (String, optional)
   
    
```

#### Sample JSON Data

```json
{
	"captureCkycSuccess": {
		"enabled": true,
		"content":
		 {
			"title": "KYC Verification",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with KYC verification",
			"successHeading": "Your CKYC is successful!",
			"successSubtext": "Your identity has been verified successfully."
		}
	}
}
```

---

### Component - CollectAddressProof

**CMS Key:** `collectAddressProof`  
**Fallback Constant:** `DEFAULT_COLLECT_ADDRESS_PROOF_CONTENT`  

#### Component Structure

```
├── enabled (Boolean)
└── content (component)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── pageHeading (String)
    ├── pageSubtext (String)
    ├── documentTypeLabel (String)
    ├── acceptedFormatsText (String)
    ├── aadhaarLabel (String)
    ├── passportLabel (String)
    ├── drivingLicenseLabel (String)
    ├── aadhaarUploadHeader (String)
    ├── aadhaarUploadSubtext (String)
    ├── passportUploadHeader (String)
    ├── passportUploadSubtext (String)
    ├── passportNumberLabel (String)
    ├── passportNumberPlaceholder (String)
    ├── passportExpiryLabel (String)
    ├── passportExpiryPlaceholder (String)
    ├── dlUploadHeader (String)
    ├── dlUploadSubtext (String)
    ├── frontUploadLabel (String)
    ├── backUploadLabel (String)
    ├── uploadPromptText (String)
    ├── errorUnsupportedFormat (String)
    ├── errorFileTooLarge (String)
    ├── errorUploadFailed (String)
    ├── kycFailedHeading (String)
    ├── kycFailedSubtext (String)
    └── kycFailedTryAgainText (String)
```



#### Sample JSON Data

```json
{
	"collectAddressProof": {
		"enabled": true,
		"content": {
			"title": "Upload Documents",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with document upload",
			"pageHeading": "KYC Verification",
			"pageSubtext": "Please upload your KYC document to complete verification.",
			"documentTypeLabel": "Select document type",
			"acceptedFormatsText": "Accepted formats: PDF, JPG, PNG (max 5 MB per file)",
			"aadhaarLabel": "Aadhaar Card",
			"passportLabel": "Passport",
			"drivingLicenseLabel": "Driving License",
			"aadhaarUploadHeader": "Aadhaar verification",
			"aadhaarUploadSubtext": "Please upload the front and back of your Aadhaar.",
			"passportUploadHeader": "Passport verification",
			"passportUploadSubtext": "Please upload the front and back of your Passport.",
			"passportNumberLabel": "Passport Number",
			"passportNumberPlaceholder": "Enter passport number",
			"passportExpiryLabel": "Passport Expiry",
			"passportExpiryPlaceholder": "DD/MM/YYYY",
			"dlUploadHeader": "Driving license verification",
			"dlUploadSubtext": "Please upload the front and back of your Driving License.",
			"frontUploadLabel": "Front",
			"backUploadLabel": "Back",
			"uploadPromptText": "Upload",
			"errorUnsupportedFormat": "Unsupported format (Use PDF/JPG/PNG only)",
			"errorFileTooLarge": "File too large (File is over 5 MB)",
			"errorUploadFailed": "Something went wrong",
			"kycFailedHeading": "CKYC validation failed",
			"kycFailedSubtext": "We couldn't verify your documents.\nYou can recheck and submit them again.",
			"kycFailedTryAgainText": "Try Again"
		}
	}
}
```

---

### Component - CaptureAddressDetails

**CMS Key:** `captureAddressDetails`  
**Fallback Constant:** `DEFAULT_CAPTURE_ADDRESS_DETAILS_CONTENT`  

#### Component Structure

```
├── enabled (Boolean)
└── content (component)
    ├── title (String)
    ├── submitButtonText (String)
    └── helpAriaLabel (String)
```

#### Sample JSON Data

```json
{
	"captureAddressDetails": {
		"enabled": true,
		"content": {
			"title": "Address details",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with address details"
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
			"captureCkycSuccess": {
				"enabled": true,
				"content": {
					"title": "KYC Verification",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with KYC verification",
					"successHeading": "Your CKYC is successful!",
					"successSubtext": "Your identity has been verified successfully."
				}
			},
			"captureKycFailed": {
				"enabled": true,
				"content": {
					"title": "KYC Verification",
					"uploadButtonText": "Upload documents manually",
					"retryButtonText": "Retry",
					"helpAriaLabel": "Get help with KYC",
					"failureHeading": "CKYC validation failed",
					"failureSubtext": "We could not verify your identity via CKYC.",
					"contactSheetTitle": "Need help?",
					"contactSheetSubtext": "Please contact your insurer for assistance with KYC verification."
				}
			},
			"collectAddressProof": {
				"enabled": true,
				"content": {
					"title": "Upload Documents",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with document upload",
					"pageHeading": "KYC Verification",
					"pageSubtext": "Please upload your KYC document to complete verification.",
					"documentTypeLabel": "Select document type",
					"acceptedFormatsText": "Accepted formats: PDF, JPG, PNG (max 5 MB per file)",
					"aadhaarLabel": "Aadhaar Card",
					"passportLabel": "Passport",
					"drivingLicenseLabel": "Driving License",
					"aadhaarUploadHeader": "Aadhaar verification",
					"aadhaarUploadSubtext": "Please upload the front and back of your Aadhaar.",
					"passportUploadHeader": "Passport verification",
					"passportUploadSubtext": "Please upload the front and back of your Passport.",
					"passportNumberLabel": "Passport Number",
					"passportNumberPlaceholder": "Enter passport number",
					"passportExpiryLabel": "Passport Expiry",
					"passportExpiryPlaceholder": "DD/MM/YYYY",
					"dlUploadHeader": "Driving license verification",
					"dlUploadSubtext": "Please upload the front and back of your Driving License.",
					"frontUploadLabel": "Front",
					"backUploadLabel": "Back",
					"uploadPromptText": "Upload",
					"errorUnsupportedFormat": "Unsupported format (Use PDF/JPG/PNG only)",
					"errorFileTooLarge": "File too large (File is over 5 MB)",
					"errorUploadFailed": "Something went wrong",
					"kycFailedHeading": "CKYC validation failed",
					"kycFailedSubtext": "We couldn't verify your documents.\nYou can recheck and submit them again.",
					"kycFailedTryAgainText": "Try Again"
				}
			},
			"captureAddressDetails": {
				"enabled": true,
				"content": {
					"title": "Address details",
					"submitButtonText": "Continue",
					"helpAriaLabel": "Get help with address details"
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


