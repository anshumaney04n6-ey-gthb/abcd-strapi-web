# MMV Buy Fallback CMS Requirements

---

**Date:** 2026-03-15  
**Purpose:** Sync UAT Strapi with LOCAL configuration for MMV Buy fallback journey content

## Table of Contents

1. [Overview](#overview)
2. [Content Keys (Buy Flow)](#content-keys-buy-flow)
3. [Pages (Phase 1)](#pages-phase-1)
	- [Page - Capture Vehicle Make](#page---capture-vehicle-make)
	- [Page - Capture Vehicle Model](#page---capture-vehicle-model)
	- [Page - Capture Vehicle Fuel](#page---capture-vehicle-fuel)
	- [Page - Capture Vehicle Variant](#page---capture-vehicle-variant)
	- [Page - Capture Registration Year](#page---capture-registration-year)
	- [Page - Capture Registration RTO](#page---capture-registration-rto)
	- [Page - Capture Registration Pincode](#page---capture-registration-pincode)
4. [Sample API Response](#sample-api-response)


---

## 1. MMV_BUY Page Overview

**Content Type:** `insurance-journey-pages`  
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys (Buy Flow)

| UI Page Name | CMS Key | Content Type |
|--------------|---------|--------------|
| Capture Vehicle Make | `captureVehicleMake` | page |
| Capture Vehicle Model | `captureVehicleModel` | page |
| Capture Vehicle Fuel | `captureVehicleFuel` | page |
| Capture Vehicle Variant | `captureVehicleVariant` | page |
| Capture Registration Year | `captureRegistrationYear` | page |
| Capture Registration RTO | `captureRegistrationRTO` | page |
| Capture Registration Pincode | `captureRegistrationPincode` | page |

---


### Page - Capture Vehicle Make

**CMS Key:** `captureVehicleMake`  
**Fallback Constant:** `DEFAULT_CAPTURE_VEHICLE_MAKE_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── popularBrands (Array, Repeatable)
    │   ├── order (Integer)
    │   ├── id (String)
    │   ├── brandName (String)
    │   ├── brandIconName (String,Optional)
    │   └── brandLogoUrl (String,Optional)
    ├── popularBrands4W (Array, Repeatable)
    │   ├── order (Integer)
    │   ├── id (String)
    │   ├── brandName (String)
    │   ├── brandIconName (String,Optional)
    │   └── brandLogoUrl (String,Optional)
    └── popularBrands2W (Array, Repeatable)
        ├── order (Integer)
        ├── id (String)
        ├── brandName (String)
        ├── brandIconName (String,Optional)
        └── brandLogoUrl (String,Optional)
```

#### Sample JSON Data
```json
{
	"captureVehicleMake": {
		"enabled": true,
		"content": 
			{
				"title": "{VehicleType} insurance",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with selecting a car brand",
				"popularBrands": [
					{ 
						"order": 1, 
						"id": "1",
						"brandName": "Maruti Suzuki",
						"brandIconName": "MarutiSuzuki", 
						"brandLogoUrl": "/assets/vehicle-brands/MarutiSuzuki.png" 
					},
					{ 
						"order": 2, 
						"id": "2", 
						"brandName": "Hyundai", 
						"brandIconName": "Hyundai", 
						"brandLogoUrl": "/assets/vehicle-brands/hyundai-logo.png" 
					},
					{ 
						"order": 3, 
						"id": "3", 
						"brandName": "Tata Motors", 
						"brandIconName": "Tata", 
						"brandLogoUrl": "/assets/vehicle-brands/tatamotorslogo.png" 
					},
					{ 
						"order": 4, 
						"id": "4", 
						"brandName": "Mahindra", 
						"brandIconName": "Mahindra", 
						"brandLogoUrl": "/assets/vehicle-brands/Mahindra.png" 
					},
					{ 
						"order": 5, 
						"id": "5", 
						"brandName": "Toyota", 
						"brandIconName": "Toyota", 
						"brandLogoUrl": "/assets/vehicle-brands/Toyotalogo.png" 
					},
					{ 
						"order": 6, 
						"id": "6", 
						"brandName": "Kia", 
						"brandIconName": "Kia", 
						"brandLogoUrl": "/assets/vehicle-brands/Kialogo.png" 
					},
					{ 
						"order": 7, 
						"id": "7", 
						"brandName": "Honda", 
						"brandIconName": "Honda", 
						"brandLogoUrl": "/assets/vehicle-brands/Hondalogo.png" 
					},
					{ 
						"order": 8, 
						"id": "8", 
						"brandName": "MG Motors", 
						"brandIconName": "MG", 
						"brandLogoUrl": "/assets/vehicle-brands/MGMotorlogo.png" 
					}
				],
				"popularBrands4W": [
					{ 
						"order": 1, 
						"id": "1", 
						"brandName": "Maruti Suzuki", 
						"brandIconName": "MarutiSuzuki", 
						"brandLogoUrl": "/assets/vehicle-brands/MarutiSuzuki.png" 
					},
					{ 
						"order": 2, 
						"id": "2", 
						"brandName": "Hyundai", 
						"brandIconName": "Hyundai", 
						"brandLogoUrl": "/assets/vehicle-brands/hyundai-logo.png" 
					},
					{ 
						"order": 3, 
						"id": "3", 
						"brandName": "Tata Motors", 
						"brandIconName": "Tata", 
						"brandLogoUrl": "/assets/vehicle-brands/tatamotorslogo.png" 
					},
					{ 
						"order": 4, 
						"id": "4", 
						"brandName": "Mahindra", 
						"brandIconName": "Mahindra", 
						"brandLogoUrl": "/assets/vehicle-brands/Mahindra.png" 
					},
					{ 
						"order": 5, 
						"id": "5", 
						"brandName": "Toyota", 
						"brandIconName": "Toyota", 
						"brandLogoUrl": "/assets/vehicle-brands/Toyotalogo.png" 
					},
					{ 
						"order": 6, 
						"id": "6", 
						"brandName": "Kia", 
						"brandIconName": "Kia", 
						"brandLogoUrl": "/assets/vehicle-brands/Kialogo.png" 
					},
					{ 
						"order": 7, 
						"id": "7", 
						"brandName": "Honda", 
						"brandIconName": "Honda", 
						"brandLogoUrl": "/assets/vehicle-brands/Hondalogo.png" 
					},
					{ 
						"order": 8, 
						"id": "8", 
						"brandName": "MG Motors", 
						"brandIconName": "MG", 
						"brandLogoUrl": "/assets/vehicle-brands/MGMotorlogo.png" 
					}
				],
				"popularBrands2W": [
					{ 
						"order": 1, 
						"id": "1", 
						"brandName": "Hero MotoCorp", 
						"brandIconName": "Hero", 
						"brandLogoUrl": "/assets/vehicle-brands/Hero-MotoCorp-Logo.png" 
					},
					{ 
						"order": 2, 
						"id": "2", 
						"brandName": "Honda", 
						"brandIconName": "Honda", 
						"brandLogoUrl": "/assets/vehicle-brands/Hondalogo.png" 
					},
					{ 
						"order": 3, 
						"id": "3", 
						"brandName": "Bajaj", 
						"brandIconName": "Bajaj", 
						"brandLogoUrl": "/assets/vehicle-brands/Bajaj-Logo.png" 
					},
					{ 
						"order": 4, 
						"id": "4", 
						"brandName": "TVS", 
						"brandIconName": "TVS", 
						"brandLogoUrl": "/assets/vehicle-brands/TVS-Motor-Company.png" 
					},
					{ 
						"order": 5, 
						"id": "5", 
						"brandName": "Royal Enfield", 
						"brandIconName": "RoyalEnfield", 
						"brandLogoUrl": "/assets/vehicle-brands/royal-enfeild.png" 
					},
					{ 
						"order": 6, 
						"id": "6", 
						"brandName": "Yamaha", 
						"brandIconName": "Yamaha", 
						"brandLogoUrl": "/assets/vehicle-brands/Yamaha-Logo.png" 
					},
					{ 
						"order": 7, 
						"id": "7", 
						"brandName": "Suzuki", 
						"brandIconName": "Suzuki", 
						"brandLogoUrl": "/assets/vehicle-brands/Suzuki.png" 
					},
					{ 
						"order": 8, 
						"id": "8", 
						"brandName": "KTM", 
						"brandIconName": "KTM", 
						"brandLogoUrl": "/assets/vehicle-brands/ktm.png" 
					}
				]
			}
	   }
	}
}
```

---

### Page - Capture Vehicle Model

**CMS Key:** `captureVehicleModel`  
**Fallback Constant:** `DEFAULT_CAPTURE_VEHICLE_MODEL_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    └── helpAriaLabel (String)
```

#### Sample JSON Data
```json
{
	"captureVehicleModel": {
		"enabled": true,
		"content": 
			{
				"title": "{VehicleType} insurance",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with selecting a car model"
			}
		
	}
}
```

---


### Page - Capture Vehicle Fuel

**CMS Key:** `captureVehicleFuel`  
**Fallback Constant:** `DEFAULT_CAPTURE_VEHICLE_FUEL_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    └── helpAriaLabel (String)
```

#### Sample JSON Data
```json
{
	"captureVehicleFuel":{
	   "enabled": true,
	   "content": 
		  {
			"title": "{VehicleType} insurance",
			"submitButtonText": "Continue",
			"helpAriaLabel": "Get help with selecting fuel type"
		  }
	   
	}	    
}
```


---

### Page - Capture Vehicle Variant

**CMS Key:** `captureVehicleVariant`  
**Fallback Constant:** `DEFAULT_CAPTURE_VEHICLE_VARIANT_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    └── helpAriaLabel (String)
```

#### Sample JSON Data
```json
{
	"captureVehicleVariant": {
		"enabled": true,
		"content": 
			{
				"title": "{VehicleType} insurance",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with selecting a car variant"
			}
		
	}
}
```



---

### Page - Capture Registration Year

**CMS Key:** `captureRegistrationYear`  
**Fallback Constant:** `DEFAULT_CAPTURE_REGISTRATION_YEAR_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── minYear (Integer)
    ├── maxYear (Integer)
    └── yearsPerPage (Integer)
```

#### Sample JSON Data
```json
{
	"captureRegistrationYear": {
		"enabled": true,
		"content": 
			{
				"title": "{VehicleType} insurance",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with selecting registration year",
				"minYear": 2000,
				"maxYear": 2026,
				"yearsPerPage": 16
			}
	}
}
```

---

### Page - Capture Registration RTO

**CMS Key:** `captureRegistrationRTO`  
**Fallback Constant:** `DEFAULT_CAPTURE_REGISTRATION_RTO_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    └── searchPlaceholder (String)
```

#### Sample JSON Data
```json
{
	"captureRegistrationRTO": {
		"enabled": true,
		"content": 
			{
				"title": "{VehicleType} insurance",
				"submitButtonText": "Continue",
				"helpAriaLabel": "Get help with selecting registration RTO",
				"searchPlaceholder": "Search RTO location"
			}
	}
}
```


---

### Page - Capture Registration Pincode

**CMS Key:** `captureRegistrationPincode`  
**Fallback Constant:** `DEFAULT_CAPTURE_REGISTRATION_PINCODE_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Object)
    ├── title (String)
    ├── submitButtonText (String)
    ├── heading (String)
    ├── helpAriaLabel (String)
    ├── inputLabel (String)
    ├── inputPlaceholder (String)
    └── invalidPincodeMessage (String)
```

#### Sample JSON Data
```json
{
	"captureRegistrationPincode": {
		"enabled": true,
		"content": 
			{
				"title": "{VehicleType} insurance",
				"submitButtonText": "Continue",
				"heading": "Enter your residential pincode",
				"helpAriaLabel": "Get help with entering registration pincode",
				"inputLabel": "Pincode",
				"inputPlaceholder": "Enter pincode",
				"invalidPincodeMessage": "Enter a valid 6-digit pincode"
			}
		
	}
}
```


---

## Sample API Response

```json
{
	"data":
		{
			
				"captureVehicleMake": {
					"enabled": true,
					"content": [
						{
							"title": "{VehicleType} insurance",
							"submitButtonText": "Continue",
							"helpAriaLabel": "Get help with selecting a car brand",
							"popularBrands": [
								{
									"order": 1,
									"id": "1",
									"brandName": "Maruti Suzuki",
									"brandIconName": "MarutiSuzuki",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/MarutiSuzuki.png')"
								},
								{
									"order": 2,
									"id": "2",
									"brandName": "Hyundai",
									"brandIconName": "Hyundai",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/hyundai-logo.png')"
								},
								{
									"order": 3,
									"id": "3",
									"brandName": "Tata Motors",
									"brandIconName": "Tata",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/tatamotorslogo.png')"
								},
								{
									"order": 4,
									"id": "4",
									"brandName": "Mahindra",
									"brandIconName": "Mahindra",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Mahindra.png')"
								},
								{
									"order": 5,
									"id": "5",
									"brandName": "Toyota",
									"brandIconName": "Toyota",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Toyotalogo.png')"
								},
								{
									"order": 6,
									"id": "6",
									"brandName": "Kia",
									"brandIconName": "Kia",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Kialogo.png')"
								},
								{
									"order": 7,
									"id": "7",
									"brandName": "Honda",
									"brandIconName": "Honda",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Hondalogo.png')"
								},
								{
									"order": 8,
									"id": "8",
									"brandName": "MG Motors",
									"brandIconName": "MG",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/MGMotorlogo.png')"
								}
							],
							"popularBrands4W": [
								{
									"order": 1,
									"id": "1",
									"brandName": "Maruti Suzuki",
									"brandIconName": "MarutiSuzuki",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/MarutiSuzuki.png')"
								},
								{
									"order": 2,
									"id": "2",
									"brandName": "Hyundai",
									"brandIconName": "Hyundai",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/hyundai-logo.png')"
								},
								{
									"order": 3,
									"id": "3",
									"brandName": "Tata Motors",
									"brandIconName": "Tata",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/tatamotorslogo.png')"
								},
								{
									"order": 4,
									"id": "4",
									"brandName": "Mahindra",
									"brandIconName": "Mahindra",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Mahindra.png')"
								},
								{
									"order": 5,
									"id": "5",
									"brandName": "Toyota",
									"brandIconName": "Toyota",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Toyotalogo.png')"
								},
								{
									"order": 6,
									"id": "6",
									"brandName": "Kia",
									"brandIconName": "Kia",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Kialogo.png')"
								},
								{
									"order": 7,
									"id": "7",
									"brandName": "Honda",
									"brandIconName": "Honda",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Hondalogo.png')"
								},
								{
									"order": 8,
									"id": "8",
									"brandName": "MG Motors",
									"brandIconName": "MG",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/MGMotorlogo.png')"
								}
							],
							"popularBrands2W": [
								{
									"order": 1,
									"id": "1",
									"brandName": "Hero MotoCorp",
									"brandIconName": "Hero",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Hero-MotoCorp-Logo.png')"
								},
								{
									"order": 2,
									"id": "2",
									"brandName": "Honda",
									"brandIconName": "Honda",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Hondalogo.png')"
								},
								{
									"order": 3,
									"id": "3",
									"brandName": "Bajaj",
									"brandIconName": "Bajaj",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Bajaj-Logo.png')"
								},
								{
									"order": 4,
									"id": "4",
									"brandName": "TVS",
									"brandIconName": "TVS",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/TVS-Motor-Company.png')"
								},
								{
									"order": 5,
									"id": "5",
									"brandName": "Royal Enfield",
									"brandIconName": "RoyalEnfield",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/royal-enfeild.png')"
								},
								{
									"order": 6,
									"id": "6",
									"brandName": "Yamaha",
									"brandIconName": "Yamaha",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Yamaha-Logo.png')"
								},
								{
									"order": 7,
									"id": "7",
									"brandName": "Suzuki",
									"brandIconName": "Suzuki",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/Suzuki.png')"
								},
								{
									"order": 8,
									"id": "8",
									"brandName": "KTM",
									"brandIconName": "KTM",
									"brandLogoUrl": "getAssetPath('/assets/vehicle-brands/ktm.png')"
								}
							]
						}
					]
				},
				"captureVehicleModel": {
					"enabled": true,
					"content": {
						"title": "{VehicleType} insurance",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with selecting a car model"
					}
				},
				"captureVehicleFuel": {
					"enabled": true,
					"content": {
						"title": "{VehicleType} insurance",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with selecting fuel type"
					}
				},
				"captureVehicleVariant": {
					"enabled": true,
					"content": {
						"title": "{VehicleType} insurance",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with selecting a car variant"
					}
				},
				"captureRegistrationYear": {
					"enabled": true,
					"content": {
						"title": "{VehicleType} insurance",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with selecting registration year",
						"minYear": 2000,
						"maxYear": 2026,
						"yearsPerPage": 16
					}
				},
				"captureRegistrationRTO": {
					"enabled": true,
					"content": {
						"title": "{VehicleType} insurance",
						"submitButtonText": "Continue",
						"helpAriaLabel": "Get help with selecting registration RTO",
						"searchPlaceholder": "Search RTO location"
					}
				},
				"captureRegistrationPincode": {
					"enabled": true,
					"content": {
						"title": "{VehicleType} insurance",
						"submitButtonText": "Continue",
						"heading": "Enter your residential pincode",
						"helpAriaLabel": "Get help with entering registration pincode",
						"inputLabel": "Pincode",
						"inputPlaceholder": "Enter pincode",
						"invalidPincodeMessage": "Enter a valid 6-digit pincode"
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

