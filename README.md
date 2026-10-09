# Acme Pets API specs

The API descriptions for the Acme Pets platform, one folder per API, kept in
one repository so changes get reviewed in one place and the docs in
Confluence stay in sync with what's merged here.

> This is a demo repository for trying
> [SpecPage](https://github.com/Mattddixo/SpecPage-docs), an OpenAPI,
> Swagger and AsyncAPI docs macro for Confluence Cloud. Acme Pets isn't a
> real company and none of the servers exist, so Try it out requests won't
> get answers.

## What's here

| API | Spec | Format | Owner |
| --- | --- | --- | --- |
| Pet Store | [`openapi.yaml`](openapi.yaml) | OpenAPI 3.0, one file | Pets team |
| Orders | [`apis/orders/openapi.yaml`](apis/orders/openapi.yaml) | OpenAPI 3.1, split across files | Commerce team |
| Payments | [`apis/payments/openapi.json`](apis/payments/openapi.json) | OpenAPI 3.0, JSON | Payments team |
| Inventory | [`apis/inventory/swagger.yaml`](apis/inventory/swagger.yaml) | Swagger 2.0 (legacy) | Warehouse team |
| Order events | [`events/notifications/asyncapi.yaml`](events/notifications/asyncapi.yaml) | AsyncAPI 3.0 (Kafka) | Commerce team |

```
openapi.yaml                 Pet Store (kept at the top level for older links)
apis/
  orders/
    openapi.yaml             the file to point tools at
    paths/                   one file per URL
    schemas/                 Orders-only types
  payments/openapi.json
  inventory/swagger.yaml
events/
  notifications/asyncapi.yaml
shared/                      error format, money and paging, used by several APIs
  schemas/  parameters/  responses/
redocly.yaml                 lint rules, run by CI on every pull request
```

The Orders API is split across files and pulls in the shared types with
relative `$ref`s, for example `$ref: ../../../shared/schemas/Money.yaml`.
Always point tools at an API's main file (`apis/orders/openapi.yaml`), never
at a part such as `paths/orders.yaml`, which isn't a complete spec on its own.

## Versions

- `main` is what's live.
- Branch `v1` is the Pet Store's first version (1.0.0). `main` is 2.0.0,
  which removed an endpoint and added a required parameter.
- Branch `release-orders-1.0` is the first Orders release (1.0.0). `main`
  has 1.1.0, which only adds things.
- Branch `orders-v2` is work in progress on Orders 2.0, which changes how
  totals are sent: a breaking change for anyone using the API.

## Using it with SpecPage

1. In Confluence settings, open SpecPage and add a Git connection: provider
   GitHub, allowed repository `Mattddixo/Specpagetest`.
2. Add a SpecPage macro to a page, choose Git, pick the connection, and pick
   a spec from the File path suggestions. Or paste a link to a spec file on
   GitHub into the page, for example
   https://github.com/Mattddixo/Specpagetest/blob/main/apis/orders/openapi.yaml.
3. Things to try:
   - The Orders macro shows it merged 15 files into one document.
   - Click Changes on the Pet Store and enter `v1`, or on Orders and enter
     `release-orders-1.0` (additions only) or `orders-v2` (breaking changes).
   - Put several macros on one page, one per API, or open the space's API
     list to see them all.

## Changing an API

See [CONTRIBUTING.md](CONTRIBUTING.md).
