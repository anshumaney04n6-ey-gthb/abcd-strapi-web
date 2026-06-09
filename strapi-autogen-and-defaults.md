Strapi 5.1 autogenerates "id" field. So no need to add "id" in schema.
Also, "documentId" is a reserved keyword in strapi 5.1 . So, avoid using it during development.

Add necessary human understandable meaningful defaults to the strapi 5.1 schema as well.
Do this even if the attribute has "required" property.
First preference : Pick defaults from requirements file shared in chat.
Second preference : If not found, then add necessary human understandable meaningful defaults to the strapi 5.1 schema

For JSON payload, skip media files. Create/Update full JSON containing all mandatory + optional fields.
Save the JSON payload in existing directory : "/workspaces/abcd-strapi-web/payload"

For APIs check this folder : "/workspaces/abcd-strapi-web/abcd_strapi_dost_portal/src/api"
For components check this folder : "/workspaces/abcd-strapi-web/abcd_strapi_dost_portal/src/components"

There should be complete logical separation of this API with other APIs. Keep separate API folders and
component folder. No reuse of other API component is encouraged. If required, you can reuse the same API
component.

Create checklist for tasks.