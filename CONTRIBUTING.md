# Changing an API

1. Branch from `main` and edit the spec. Keep each API in its own folder; put
   types used by more than one API in `shared/`.
2. Bump `info.version`:
   - patch (1.0.0 → 1.0.1) for wording and examples,
   - minor (1.0.0 → 1.1.0) for additions: new endpoints, new optional fields,
   - major (1.0.0 → 2.0.0) for anything that can break a client: removing or
     renaming things, making something required, changing a type.
3. Run the linter before pushing:
   ```
   npx @redocly/cli@2.54.3 lint
   ```
4. Open a pull request. CI runs the same lint, and the API's owners (see
   `.github/CODEOWNERS`) review it. Breaking changes need a migration note in
   the pull request description.
5. After merging a release, tag it `<api>-v<version>`, for example
   `orders-v1.1.0`, so it can be compared with later versions.
