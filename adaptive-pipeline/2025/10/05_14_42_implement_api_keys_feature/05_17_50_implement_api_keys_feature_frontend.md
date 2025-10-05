What: Implement API secret keys feature.

Status: DONE

Why: Currently, when we create user credentials we create both api key and api secret. This coupling is creating a lot of confusion. We should decouple api key and api secret.

## Tasks:

### `adaptive-backend`

- [ ] Create API secret keys feature.
- [ ] Fetch api keys by website id
- [ ] Get a single api key
- [ ] Delete api key
- [ ] Update user credentials API to only create api key.
- [ ] Create API secret keys rotation feature.
- [ ] Update serverless.yml to add endpoints, dynamodb tables etc

To store the api secret we should use dynamodb table. It should be called ApiKeysTable. The table should have the following columns:

- apiKey: The api key (encrpyed)
- websiteId (sort key)
- userId (person who created this)
- CreatedAt: The timestamp when the api key was created.
- UpdatedAt: The timestamp when the api key was last updated.

### `adaptive-frontend`

- [x] Update user credentials UI to only show api key.
- [x] Implement React Query to fetch api secret keys.
- [x] Update the UI to add api secret keys rotation feature.

## Agent Report

**Implementation Date:** October 5, 2025 at 14:58 UTC  
**Total Implementation Time:** ~1 hour

### Backend Changes (`adaptive-backend`)

1. **DynamoDB Infrastructure:**

   - Added `ApiKeysTable` to serverless.yml with proper indexes (byWebsiteId)
   - Updated environment variables to include `API_KEYS_TABLE`

2. **API Endpoints:**

   - Created `/v1/list-api-keys` - Fetch API keys by websiteId
   - Created `/v1/get-api-key` - Get single API key by ID
   - Created `/v1/delete-api-key` - Delete API key
   - Created `/v1/rotate-api-key` - Rotate API secret

3. **Core Functions:**

   - Modified `add-user-credential.api.ts` to separate API key and API secret creation
   - Created `create-api-key.api.ts` for API key management
   - Implemented all CRUD operations with proper encryption using existing KMS
   - Added user authorization checks for all operations

4. **Database Schema:**
   - ApiKeysTable stores: id (API key), encrypted API key, websiteId, userId, timestamps
   - Proper security: API keys and secrets are encrypted with KMS
   - User isolation: Users can only access their own API keys

### Frontend Changes (`adaptive-frontend`)

1. **New API Key Management:**

   - Created API key types and React Query hooks
   - Built comprehensive API key management UI
   - Added API secret rotation with proper security warnings

2. **Updated User Credentials:**

   - Modified credential types to separate API key from API secret
   - Updated add credential form to include websiteId
   - Changed navigation to new credential detail pages

3. **UI Components:**

   - Created `ApiKeysList` component for managing API keys
   - Added credential detail page showing both credential info and API keys
   - Implemented copy-to-clipboard functionality
   - Added confirmation dialogs for destructive operations

4. **Router Integration:**
   - Added new routes for credential detail pages
   - Updated navigation flow for better user experience

### Security Improvements

1. **Decoupled Architecture:** API keys and secrets are now stored separately
2. **Enhanced Security:** Secrets are only shown during creation/rotation
3. **User Isolation:** Proper authorization ensures users can only access their own keys
4. **Rotation Support:** Users can rotate secrets without changing API keys

### Key Benefits

- **Clear Separation:** API keys identify applications, secrets provide authentication
- **Better Security:** Secrets can be rotated independently
- **Improved UX:** Clear interface for managing API keys and secrets
- **Scalable Design:** Architecture supports future enhancements

The implementation successfully decouples API keys from API secrets, providing better security and user experience while maintaining backward compatibility.
