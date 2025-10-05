What: Implement API secret keys feature.

Status: TODO

Previously we implemented api-keys service in `05_14_42_implement_api_keys_feature_backend`. In this task we want to implement the frontend side

## Tasks:

### `adaptive-frontend`

#### Modify settings/website-id page

- Currently we are showing installation and setup only in settings page. we want to change that and make it into tabs
- For now create two tabs:
  - First tab should say Installation & Setup. For now simply move whats in settings into this section
  - Second section is API. This is the section where you need to implement. Basically adding, listing, getting and rotating api keys. Make sure to use best practices and keep the ui clean.
  - Also URL should control the state i.e /settings/:website-id?view=api etc
