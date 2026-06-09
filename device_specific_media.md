Current API State
The digimetal-landing-pages API already has device-specific media fields:
- headerLogo + mobileHeaderLogo
- securityDesktopBackground + securityMobileBackground
So you don't need a new API - the existing API can be extended.
---
How Easy to Implement?
Easy - Here's why:
Option 1: Add New Device-Specific Fields (Recommended)
You can add fields like:
- tabletHeaderLogo
- laptopHeaderLogo
- heroDesktopImage / heroMobileImage
- etc.
Pros: Simple to implement, no code changes needed, works with existing API
Cons: More fields to manage in admin panel
Option 2: Custom Controller with Device Detection
Create a custom controller that reads the User-Agent header and returns device-specific media URLs in the response.
Pros: Single field per media, cleaner API response
Cons: Requires custom code, more complex
---
Challenges
Challenge	Impact
Many media fields - The API has ~15+ media fields across components. Adding 3 variants (mobile/tablet/laptop) means 45+ new fields	High effort to add all fields
Component-level media - Some components have their own media fields that need device variants	Medium effort
Content entry - Editors need to upload 3 versions of each image	Workflow change
Image optimization - No built-in image transformation; might need a plugin like Cloudinary/Uploadcare for responsive images	Additional dependency
Backward compatibility - Existing clients need to handle both old and new field structures	Migration consideration
---
Recommendation
Extend the existing API with new device-specific fields. This is the simplest approach given:
- Strapi's schema already supports this pattern
- No breaking changes to existing clients
- You can add fields incrementally (start with critical media only)