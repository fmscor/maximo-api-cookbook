# 02 · Querying records

**Goal:** pull only the records and fields you need, in plain JSON.

> Tested on: _not yet (draft, testing on Maximo Manage 9.0)_

## The request

Work orders waiting for approval at site BEDFORD, newest first:

```http
GET https://<workspace>.manage.<instance>.<domain>/maximo/api/os/mxapiwodetail?lean=1
    &oslc.select=wonum,description,status,assetnum,reportdate
    &oslc.where=siteid="BEDFORD" and status="WAPPR"
    &oslc.orderBy=-reportdate
    &oslc.pageSize=20
apikey: <your-api-key>
```

(Shown on several lines for reading. In practice it's one URL, and tools like Postman encode the quotes and spaces for you.)

In the Postman collection this is **02 Query work orders**. The site comes from the collection variable `siteid`.

## What each parameter does

| Parameter | Purpose |
|---|---|
| `lean=1` | Plain JSON, no `spi:`/`rdf:` prefixes. Use it on every call |
| `oslc.select` | Only the fields you list. Without it you get every field, which is slow |
| `oslc.where` | The filter. Strings in double quotes, combine with `and` / `or` |
| `oslc.orderBy` | `-field` sorts descending, `+field` ascending |
| `oslc.pageSize` | Records per page (see recipe 04 for paging) |

## Useful `oslc.where` patterns

```text
status in ["APPR","INPRG"]
reportdate>="2026-01-01T00:00:00-05:00"
description="%pump%"                     (contains "pump")
assetnum="11430" and siteid="BEDFORD"
```

Child fields: `oslc.select=wonum,asset.description` pulls a field from the related asset in one call.

## Sample response (trimmed)

```json
{
  "member": [
    {
      "wonum": "1012",
      "description": "Replace pump seal",
      "status": "WAPPR",
      "assetnum": "11430",
      "href": "https://<workspace>.manage.<instance>.<domain>/maximo/api/os/mxapiwodetail/_QkVERk9SRC8xMDEy"
    }
  ],
  "responseInfo": { "href": "..." }
}
```

Keep the `href`: it's how you update this exact record (recipe 03).

## Gotchas

- Field names in `oslc.select` and `oslc.where` are lowercase attribute names.
- Use `oslc.select=*` only while exploring. Never use it in an integration.
- Date filters need the full ISO format with a time zone offset.
