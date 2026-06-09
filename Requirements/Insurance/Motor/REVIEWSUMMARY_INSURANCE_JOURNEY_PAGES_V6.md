# Review Summary Insurance Journey Pages

---

**Date:** 2026-05-11  
**Purpose:** Sync UAT Strapi with LOCAL configuration for Review Summary journey content

## Table of Contents

1. [Overview](#1-review-summary-page-overview)
2. [Content Keys](#content-keys)
3. [Page Structure](#page-structure)
	- [Page - Review Summary](#page---review-summary)
4. [Sample API Response](#sample-api-response)

---

## 1. Review Summary Page Overview

**Content Type:** `insurance-journey-pages`  
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys

| Page Name | CMS Key | Content Type |
|-----------|---------|--------------|
| Review Summary | `reviewSummary` | page |

---

## Page Structure

### Page - Review Summary

**CMS Key:** `reviewSummary`  
**Fallback Constant:** `DEFAULT_REVIEW_SUMMARY_CONTENT`

#### Page Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── termsPreText (String)
    ├── termsLinkText (String)
    ├── termsUrl (String)
    ├── privacyLinkText (String)
    └── privacyUrl (String)
```

#### Sample JSON Data
```json
{
	"reviewSummary": {
		"enabled": true,
		"content": {
			"title": "Select Plan",
			"submitButtonText": "Buy now",
			"helpAriaLabel": "Get help with review summary details",
			"termsPreText": "By clicking on Buy now you are agreeing to",
			"termsLinkText": "Terms & Conditions",
			"termsUrl": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
			"privacyLinkText": "Privacy Policy",
			"privacyUrl": "https://www.adityabirlacapital.com/abc-digital/privacy-policy"
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
			"reviewSummary": {
				"enabled": true,
				"content": {
					"title": "Select Plan",
					"submitButtonText": "Buy now",
					"helpAriaLabel": "Get help with review summary details",
					"termsPreText": "By clicking on Buy now you are agreeing to",
					"termsLinkText": "Terms & Conditions",
					"termsUrl": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
					"privacyLinkText": "Privacy Policy",
					"privacyUrl": "https://www.adityabirlacapital.com/abc-digital/privacy-policy"
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

