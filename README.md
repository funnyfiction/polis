# PoLiS — Portable Liveables Interchange Standard

**Public Standard Proposal v0.1.0**  
**Status:** Initial public proposal  
**Package extension:** `.polis`

PoLiS is an open, platform-independent interchange standard for the portable identity of digital entities (Liveables) across virtual worlds, applications, and generative systems.

A Liveable may be an AI character, NPC, animal, plant, object, or another persistent digital entity. It does not need to be intelligent or autonomous.

> **Identity travels. Platforms remain independent.**

## Core package technology

- JSON — structured, human-readable serialization.
- JSON Schema Draft 2020-12 — public validation contract.
- TAR — package container.
- Zstandard — package compression.
- SHA-256 — component and asset integrity.

A `.polis` file is a Zstandard-compressed TAR archive. `manifest.json` and `identity.json` are required at the archive root. Optional component JSON files are grouped under `components/`; binary assets are grouped under `assets/`. Single-file categories are not wrapped in unnecessary directories.

## Repository status

This repository contains the initial public proposal and draft validation schemas. It is not yet a ratified or finalized standard. Schema and package rules may change before a stable release.

## Contents

- [Specification](SPECIFICATION.md)
- [JSON Schemas](schemas/v0.1/)
- [Examples](examples/)
- [License](LICENSE)

## Contributing

Issues and pull requests are welcome. Please identify whether a proposal changes the normative data model, package structure, validation behavior, or only an implementation recommendation.

## Licensing

The specification (`SPECIFICATION.md`), repository documentation, and JSON Schemas in `schemas/` are licensed under **CC BY 4.0**. Copyright © 2026 Gene Semerenko. Published by FunnyFiction. Any future reference implementation source code will be licensed separately under **Apache License 2.0**. Example Liveable data and media assets must carry their own explicit license or usage permissions; the specification license does not grant rights to those assets.

## Governance

FunnyFiction is the publishing home for PoLiS. It is currently an independent project organization, not a statement that a separately registered legal entity exists.

PoLiS development is intended to be transparent and open to community participation:

- Specification changes are proposed and discussed publicly through GitHub issues and pull requests.
- Normative changes are reviewed and documented before release.
- Published versions are identified by explicit version numbers and should remain available as historical releases; changes are made in subsequent versions rather than silently rewriting the meaning of an existing release.
- The project welcomes contributions from independent developers and organizations.
- The specification is published under CC BY 4.0, which permits reuse and adaptation under its attribution terms. Anyone may maintain an independent fork, subject to the license and applicable trademark rights.

The project founder and original author is Gene Semerenko. The governance process may evolve as the community and project mature; any such changes should be documented publicly.
