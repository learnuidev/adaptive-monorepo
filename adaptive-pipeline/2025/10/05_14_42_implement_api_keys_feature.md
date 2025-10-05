What: Implement API secret keys feature.

Status: TODO

Why: Currently, when we create user credentials we create both api key and api secret. This coupling is creating a lot of confusion. We should decouple api key and api secret.

## Tasks:

### `adaptive-backend`

- [ ] Create API secret keys feature.
- [ ] Fetch api keys by website id
- [ ] Get a single api key
- [ ] Delete api key
- [ ] Update user credentials API to only create api key.
- [ ] Create API secret keys rotation feature.

To store the api secret we should use dynamodb table. It should be called ApiKeysTable. The table should have the following columns:

- apiKey: The api key (encrpyed)
- websiteId (sort key)
- userId (person who created this)
- CreatedAt: The timestamp when the api key was created.
- UpdatedAt: The timestamp when the api key was last updated.

### `adaptive-frontend`

- [ ] Update user credentials UI to only show api key.
- [ ] Implement React Query to fetch api secret keys.
- [ ] Update the UI to add api secret keys rotation feature.
