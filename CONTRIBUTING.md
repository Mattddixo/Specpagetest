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
5. When an API is released, keep a branch of that version named
   `release-<api>-<major.minor>`, for example `release-orders-1.1`, so later
   versions can be compared with it and fixes can go out for older clients.
