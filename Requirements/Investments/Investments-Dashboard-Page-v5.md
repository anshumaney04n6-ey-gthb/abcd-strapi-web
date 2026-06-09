# Investment Dashboard v5 - Field Changes Only

## Overview

This document includes only the fields to remove and add for v5.

---

## API Endpoints

### Base URL
```
/api/investments-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/investments-dashboard-pages` | List all dashboard pages |
| GET | `/api/investments-dashboard-pages/:id` | Get single dashboard page |
| POST | `/api/investments-dashboard-pages` | Create dashboard page |
| PUT | `/api/investments-dashboard-pages/:id` | Update dashboard page |
| DELETE | `/api/investments-dashboard-pages/:id` | Delete dashboard page |

### Query Parameters
```
?populate=*
?filters[subProduct][$eq]=fixed-deposits
?filters[partner][$eq]=default
```

---

## Field Change Mapping (With Arrows)

| Change Type | Mapping |
|-------------|---------|
| REMOVE | `bannerFD.amount` -> removed |
| REMOVE | `bannerFD.unit` -> removed |
| REMOVE | `bannerFD.prefix` -> removed |
| REMOVE | `bannerFD.heading` -> removed |
| REMOVE | `bannerFD.badge` -> removed |
| REMOVE | `bannerFD.buttonLabel` -> removed |
| REMOVE | `bannerFD.logoImagePath` -> removed |
| REMOVE | `bannerFD.bannerImagePath` -> removed |
| REMOVE | `bannerFD.backgroundImagePath` -> removed |
| REMOVE | `bannerFD.badgeIconPath` -> removed |
| REMOVE | `bannerFD.chevronIconPath` -> removed |
| REMOVE | `bannerFD.decorativeIconPath` -> removed |
| REMOVE | `bannerFD.gradientColor1` -> removed |
| REMOVE | `bannerFD.gradientColor2` -> removed |
| REMOVE | `bannerFD.items` -> removed |
| REMOVE | `bannerFD.cards` -> removed |
| REMOVE | `highlights.genericURL` -> removed |
| ADD | `highlights.items[].itemURL` -> added |

---

## Fields To Remove

| Parent Section | Field |
|----------------|-------|
| `bannerFD` (top-level) | `amount` |
| `bannerFD` (top-level) | `unit` |
| `bannerFD` (top-level) | `prefix` |
| `bannerFD` (top-level) | `heading` |
| `bannerFD` (top-level) | `badge` |
| `bannerFD` (top-level) | `buttonLabel` |
| `bannerFD` (top-level) | `logoImagePath` |
| `bannerFD` (top-level) | `bannerImagePath` |
| `bannerFD` (top-level) | `backgroundImagePath` |
| `bannerFD` (top-level) | `badgeIconPath` |
| `bannerFD` (top-level) | `chevronIconPath` |
| `bannerFD` (top-level) | `decorativeIconPath` |
| `bannerFD` (top-level) | `gradientColor1` |
| `bannerFD` (top-level) | `gradientColor2` |
| `bannerFD` (top-level) | `items` |
| `bannerFD` (top-level) | `cards` |
| `highlights` (section-level) | `genericURL` |

---

## Fields To Add

| Parent Section | Field | Type |
|----------------|-------|------|
| `highlights.items[]` | `itemURL` | `string` |

---

## Complete JSON Structure (v5)

```json
{
	"data": {
		"bannerFD": {
			"banners": [
				{
					"order": 1,
					"bannerFDId": "shivalik",
					"bankCode": "UTKSIN",
					"amount": "8.75",
					"unit": "p.a",
					"prefix": "Earn up to ",
					"heading": "Shivalik Small Finance Bank",
					"badge": "Highest Interest Rate",
					"buttonLabel": "Book now",
					"items": [
						{
							"order": 1,
							"bannerItemId": "item-1",
							"iconPath": "/icons/star-four-points.svg",
							"label": "Instant withdrawal",
							"description": "available"
						},
						{
							"order": 2,
							"bannerItemId": "item-2",
							"iconPath": "/icons/star-four-points.svg",
							"label": "₹5 lakh",
							"description": "insured by DICGC"
						},
						{
							"order": 3,
							"bannerItemId": "item-3",
							"iconPath": "/icons/star-four-points.svg",
							"label": "",
							"description": "RD's available"
						}
					],
					"cards": [
						{
							"order": 1,
							"bannerCardId": "card-1",
							"iconPath": "/icons/rbi.svg",
							"title": "RBI",
							"subtitle": "Regulated"
						},
						{
							"order": 2,
							"bannerCardId": "card-2",
							"iconPath": "/icons/cash-fast.svg",
							"title": "No new account",
							"subtitle": "needed"
						},
						{
							"order": 3,
							"bannerCardId": "card-3",
							"iconPath": "/icons/dicg.svg",
							"title": "Insured by",
							"subtitle": "DICGC"
						}
					],
					"logoImagePath": "/logos/banks/shivalik.svg",
					"bannerImagePath": "/images/locker.svg",
					"backgroundImagePath": "/images/bannerfd-group.webp",
					"badgeIconPath": "/icons/flash.svg",
					"chevronIconPath": "/icons/chevron-right.svg",
					"decorativeIconPath": "/images/ornament-leaf.svg",
					"gradientColor1": "rgba(79, 70, 122, 1)",
					"gradientColor2": "rgba(100, 85, 150, 0)"
				},
				{
					"order": 2,
					"bannerFDId": "suryoday",
					"bankCode": "SMCBIN",
					"amount": "8.05",
					"unit": "p.a",
					"prefix": "Earn up to ",
					"heading": "Suryoday Small Finance Bank",
					"badge": "Popular Choice",
					"buttonLabel": "Book now",
					"items": [
						{
							"order": 1,
							"bannerItemId": "item-1",
							"iconPath": "/icons/star-four-points.svg",
							"label": "Instant withdrawal",
							"description": "available"
						},
						{
							"order": 2,
							"bannerItemId": "item-2",
							"iconPath": "/icons/star-four-points.svg",
							"label": "₹5 lakh",
							"description": "insured by DICGC"
						},
						{
							"order": 3,
							"bannerItemId": "item-3",
							"iconPath": "/icons/star-four-points.svg",
							"label": "",
							"description": "RD's available"
						}
					],
					"cards": [
						{
							"order": 1,
							"bannerCardId": "card-1",
							"iconPath": "/icons/rbi.svg",
							"title": "RBI",
							"subtitle": "Regulated"
						},
						{
							"order": 2,
							"bannerCardId": "card-2",
							"iconPath": "/icons/cash-fast.svg",
							"title": "No new account",
							"subtitle": "needed"
						},
						{
							"order": 3,
							"bannerCardId": "card-3",
							"iconPath": "/icons/dicg.svg",
							"title": "Insured by",
							"subtitle": "DICGC"
						}
					],
					"logoImagePath": "/logos/banks/suryoday.svg",
					"bannerImagePath": "/images/locker.svg",
					"backgroundImagePath": "/images/bannerfd-group.webp",
					"badgeIconPath": "/icons/flash.svg",
					"chevronIconPath": "/icons/chevron-right.svg",
					"decorativeIconPath": "/images/ornament-leaf.svg",
					"gradientColor1": "rgba(115, 0, 48, 1)",
					"gradientColor2": "rgba(138, 11, 28, 0)"
				},
				{
					"order": 3,
					"bannerFDId": "premium",
					"bankCode": "premium",
					"amount": "7.75",
					"unit": "p.a",
					"prefix": "Earn up to ",
					"heading": "Premium Bank",
					"badge": "Limited Offer",
					"buttonLabel": "Book now",
					"items": [
						{
							"order": 1,
							"bannerItemId": "item-1",
							"iconPath": "/icons/star-four-points.svg",
							"label": "Instant withdrawal",
							"description": "available"
						},
						{
							"order": 2,
							"bannerItemId": "item-2",
							"iconPath": "/icons/star-four-points.svg",
							"label": "₹5 lakh",
							"description": "insured by DICGC"
						},
						{
							"order": 3,
							"bannerItemId": "item-3",
							"iconPath": "/icons/star-four-points.svg",
							"label": "",
							"description": "RD's available"
						}
					],
					"cards": [
						{
							"order": 1,
							"bannerCardId": "card-1",
							"iconPath": "/icons/rbi.svg",
							"title": "RBI",
							"subtitle": "Regulated"
						},
						{
							"order": 2,
							"bannerCardId": "card-2",
							"iconPath": "/icons/cash-fast.svg",
							"title": "No new account",
							"subtitle": "needed"
						},
						{
							"order": 3,
							"bannerCardId": "card-3",
							"iconPath": "/icons/dicg.svg",
							"title": "Insured by",
							"subtitle": "DICGC"
						}
					],
					"logoImagePath": "/logos/banks/shivalik.svg",
					"bannerImagePath": "/images/locker.svg",
					"backgroundImagePath": "/images/bannerfd-group.webp",
					"badgeIconPath": "/icons/flash.svg",
					"chevronIconPath": "/icons/chevron-right.svg",
					"decorativeIconPath": "/images/ornament-leaf.svg",
					"gradientColor1": "rgba(79, 70, 122, 1)",
					"gradientColor2": "rgba(100, 85, 150, 0)"
				}
			]
		},
		"highlights": {
			"title": "Special highlights",
			"showNavigation": true,
			"items": [
				{
					"highlightItemId": "rewards-fd",
					"title": "Earn rewards on your first FD",
					"description": "Get up to 250 ABCD Points\nRedeemable up to ₹1,000",
					"ctaText": "Book Now",
					"itemURL": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642",
					"imageSrc": "/assets/highlights/rupee-coin.webp",
					"imageAlt": "Reward coins",
					"patternImageSrc": "/assets/highlights/yellow-pattern.webp",
					"background": "linear-gradient(180deg, rgba(255, 255, 255, 0.2) 0%, rgba(255, 213, 108, 0.2) 100%), #ffffff"
				},
				{
					"highlightItemId": "smart-rd",
					"title": "Start a Smart RD",
					"description": "Invest monthly and grow your savings effortlessly",
					"ctaText": "Book now",
					"badgeText": "New",
					"itemURL": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642",
					"imageSrc": "/assets/highlights/smart-rd.svg",
					"imageAlt": "Smart RD calendar",
					"patternImageSrc": "/assets/highlights/red-pattern.webp",
					"background": "linear-gradient(180deg, rgba(255, 255, 255, 0.2) 0%, rgba(241, 101, 72, 0.2) 100%), #ffffff"
				},
				{
					"highlightItemId": "step-fd",
					"title": "Build your FD step-by-step",
					"description": "Begin with small amounts and grow systematically",
					"ctaText": "Book Now",
					"itemURL": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642",
					"imageSrc": "/images/locker.svg",
					"imageAlt": "FD growth illustration",
					"patternImageSrc": "/assets/highlights/yellow-pattern.webp",
					"background": "linear-gradient(180deg, rgba(255, 255, 255, 0.2) 0%, rgba(255, 218, 71, 0.2) 100%), #ffffff"
				}
			]
		}
	}
}
```
