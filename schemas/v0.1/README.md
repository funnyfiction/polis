# PoLiS Core v0.1 JSON Schemas

All schemas use JSON Schema Draft 2020-12.

- `manifest.schema.json` — package entry point and component/asset registry.
- `identity.schema.json` — mandatory root identity document.
- `component.schema.json` — generic envelope for optional components.
- `visual-identity.schema.json` — core visual identity component.
- `provenance.schema.json` — provenance and rights metadata.

JSON Schema validation alone cannot verify cross-file conditions. An importer MUST additionally verify that manifest paths are unique, all declared files exist, no undeclared archive entries violate package policy, file sizes and SHA-256 digests match, `liveable.id` and `liveable.type` match `identity.json`, and every visual reference resolves to a declared asset.
