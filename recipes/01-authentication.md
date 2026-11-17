# 01 · Authentication and API keys

**Goal:** connect to Maximo Manage on MAS from Postman or any tool, and confirm who you are logged in as.

> Tested on: Maximo Manage on MAS 9.1

New to Postman? Start with [Setting up Postman](../docs/setting-up-postman.md).

## Steps

1. In Manage, open the **API Keys** application and create a key for the integration user. I say integration user but if you are just testing it, you can use your own user as long as you have the appropriate access.
2. Send the key in an `apikey` header on every request.

```http
GET https://<workspace>.manage.<instance>.<domain>/maximo/api/whoami
apikey: <your-api-key>
```

A **200 OK** with your user's details means you're connected.

## Sample response (trimmed)

```json
{
  "personId": "MXINTADM",
  "displayName": "Integration Admin",
  "defaultSite": "BEDFORD",
  "langcode": "EN"
}
```

## Gotchas

- **401 on every call:** wrong header name. It's `apikey`, not `Authorization: Bearer`.
- **Request never reaches Manage on a corporate network:** Postman may be using the system proxy. Untick **Settings > Proxy > Use the system proxy**.
- **403 on an object structure:** object structure security is on by default in MAS Manage. Grant the user access to that object structure through a security group.
- **Keys are secrets.** Store them in a Postman environment or a vault, never in the collection, a script or a screenshot.
- Use `/maximo/api/...`. Examples online that use `/maximo/oslc/...` were written for older versions.
