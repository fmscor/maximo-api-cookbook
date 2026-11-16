# Maximo API Cookbook

Practical, copy-and-run recipes for the IBM Maximo REST/JSON API, for Maximo Manage on IBM Maximo Application Suite (MAS).

> **Work in progress.** Recipes go up one at a time, each tested on Maximo Manage first. Watch or star the repo to follow along.

Each recipe states the goal, the request, a sample response and the gotchas I've run into. Every request is also in the Postman collection, so you can try it without writing code.

## Who this is for

- Integration developers and Maximo admins starting with the REST API
- Functional consultants and analysts who want to pull or check data without waiting on a developer
- Non-technical team members: start with the [plain-English glossary](glossary.md)

## Recipes

| # | Recipe | What you'll learn | Status |
|---|---|---|---|
| 01 | [Authentication and API keys](recipes/01-authentication.md) | Connecting to Manage with an API key, and checking who you are | Ready |
| 02 | Querying records | `oslc.select`, `oslc.where`, `oslc.orderBy` and `lean=1` | Coming soon |
| 03 | Creating and updating work orders | POST, PATCH with `x-method-override`, and changing status | Coming soon |
| 04 | Bulk loads and paging | `x-method-override: BULK`, `oslc.pageSize` and following `nextPage` | Coming soon |

Each recipe gets its link here once it's tested and published.

## Quick start with Postman

New to Postman? Follow [Setting up Postman](docs/setting-up-postman.md) first.

1. Import `postman/maximo-api-cookbook.postman_collection.json` into Postman. Requests are added as each recipe is published.
2. Set the collection variables: `baseUrl` (e.g. `https://<workspace>.manage.<instance>.<domain>/maximo`) and `siteid`.
3. Put your API key in a Postman environment as `apikey`.
4. Run **01 Who am I** first. If it returns your user, you're connected.

Never commit your API key. Keep it in a Postman environment or a local variable, not in the collection.

## Conventions

- Every recipe is written and tested for Maximo Manage on MAS. Coming from Maximo 7.6? The [glossary](glossary.md) maps the terms, but don't assume the requests work as-is on 7.6.1.x.
- Examples use the Maximo demo data (site `BEDFORD`). Replace it with your own site.
- All requests use `lean=1`, which returns plain JSON without namespace prefixes.
- Object structures are the out-of-the-box ones (`MXAPIWODETAIL`, `MXAPIASSET`). In MAS, the user behind the API key needs object structure security grants for each one.
- Test in a non-production environment first.

## Reference

- [Maximo REST API documentation (IBM)](https://ibm-maximo-dev.github.io/maximo-restapi-documentation/overview/overview)

## About

Maintained by Fernando Corcuera, Principal Maximo Consultant at FMSC Consulting Ltd. Suggestions and corrections are welcome: open an issue.

© 2026 FMSC Consulting Ltd. Released under the [MIT License](LICENSE).

Not affiliated with or endorsed by IBM. Maximo is a trademark of IBM.
