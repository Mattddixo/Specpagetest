# SpecPage demo API

A small OpenAPI spec for trying [SpecPage](https://github.com/Mattddixo/Spinning-tops), an OpenAPI and Swagger docs macro for Confluence Cloud.

- `openapi.yaml` is a pet store API (the server isn't real, so Try it out requests won't get answers).
- Tag `v1.0.0` is the first version. `main` is 2.0.0, which removes an endpoint, adds a required parameter and changes a few other things, so comparing `main` with `v1.0.0` in SpecPage shows a breaking-change report.

## Using it in Confluence

1. In Confluence settings, open SpecPage and add a Git connection: provider GitHub, auth "None", allowed repo `Mattddixo/Specpagetest`.
2. Paste https://github.com/Mattddixo/Specpagetest/blob/main/openapi.yaml into a page. It turns into the SpecPage macro with the settings filled in.
3. On the published page, click Changes and enter `v1.0.0`.
