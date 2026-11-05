# PoLiS Core — Public Standard Proposal v0.1.0

**Full name:** Portable Liveables Interchange Standard  
**Status:** Initial Public Standard Proposal  
**Schema dialect:** JSON Schema Draft 2020-12  
**License:** CC BY 4.0  
**Copyright:** © 2026 Gene Semerenko  
**Published by:** FunnyFiction

## 1. Abstract

PoLiS defines an open interchange format for describing, packaging, validating, and transferring the portable identity of digital entities called **Liveables**. It is designed for use across virtual worlds, AI applications, creative tools, and generative systems.

PoLiS separates portable identity and data from the platform-specific runtime that hosts or renders an entity. A package may carry identity, properties, state, personality, behavior declarations, cognition-related data, memories, relationships, continuity, visual identity, provenance, and media assets.

## 2. Terminology

- **Liveable:** a digital entity with an identity and potentially portable characteristics or state.
- **Package:** a `.polis` archive containing one Liveable's portable data.
- **Liveable ID:** stable identifier of the underlying entity, independent of package and runtime IDs.
- **Package ID:** identifier of one particular export artifact; each export receives a new package ID.
- **Runtime ID:** identifier assigned by a receiving platform to its local instance; not portable identity.
- **Component:** a structured JSON document describing one aspect of a Liveable.
- **Asset:** a binary resource such as an image, audio file, video, or 3D model.
- **Capability:** a semantic feature that a Liveable or consuming system may require or support.

## 3. Design principles

1. **Identity independence:** a Liveable ID is not a database or runtime ID.
2. **Universal applicability:** a Liveable may be an intelligent character, NPC, animal, plant, object, or another digital entity.
3. **Optional components:** a Liveable only carries components relevant to it.
4. **Platform independence:** the format does not prescribe a database, runtime, programming language, simulation engine, or AI provider.
5. **Continuity:** portable memories and history retain provenance and applicable transfer restrictions.
6. **Creative interoperability:** visual and other presentation references can be consumed by image, video, audio, and 3D tools.
7. **No transferred authority:** importing a package does not grant privileges or authority in a receiving World.

## 4. Universal Liveable model

Every package MUST contain an `identity.json` document at its root. Other components are optional.

### 4.1 Identity

Identity defines the stable identifier and semantic type of a Liveable. The `id` MUST remain stable across exports and migrations that represent the same underlying entity. The `type` is an open semantic identifier; implementations MUST NOT assume a closed global enumeration.

### 4.2 Properties and state

Properties describe characteristics; state describes a condition at a particular point in the source system. A receiving system decides whether and how imported state can be represented. Importing state MUST NOT silently override canonical state owned by the receiving system.

### 4.3 Personality, behavior, and cognition

These components are optional. Behavior data is declarative in Core v0.1. Packages MUST NOT include executable behavior code, scripts, or automatic command instructions. Cognition data does not require an LLM or any specific agent architecture.

### 4.4 Memories, relationships, and continuity

These components may describe accumulated experience and relationships. They SHOULD preserve source and provenance information. References to entities absent from the receiving platform SHOULD remain representable as unresolved references rather than being silently discarded. Exporters MUST respect data rights and restrictions; a memory is not automatically transferable merely because it is stored by a character platform.

### 4.5 Visual identity

Visual Identity is a core component. It describes defining visual characteristics and may reference assets with specific purposes, such as primary identity, face, full-body appearance, distinctive features, or alternate views. It can be consumed by generative systems as reference context. PoLiS does not guarantee identical generated output across models or tools.

### 4.6 Presentation and assets

Assets are binary resources stored separately from JSON components. Asset metadata in the manifest identifies paths, media types, sizes, and checksums.

### 4.7 Provenance and rights

Provenance and rights information SHOULD identify data origins, authorship, licenses, consent, and transfer restrictions where applicable. The package format does not itself establish ownership or grant rights.

## 5. Package format

A `.polis` package MUST be a TAR archive compressed with Zstandard. The archive MUST contain exactly one root `manifest.json` and one root `identity.json`.

Recommended layout:

```text
example.polis
├── manifest.json
├── identity.json
├── visual-identity.json
├── provenance.json
├── components/
│   ├── properties.json
│   ├── state.json
│   ├── personality.json
│   ├── behavior.json
│   ├── cognition.json
│   ├── memories.json
│   ├── relationships.json
│   ├── goals.json
│   └── history.json
└── assets/
    ├── portrait.webp
    └── voice.ogg
```

This layout is illustrative. Optional JSON components may be placed at the root or in `components/`; paths are declared by the manifest. Assets may be placed at the root or in `assets/`. Implementations SHOULD use the root for singleton metadata documents and directories for groups of related files. Empty directories have no semantic meaning.

## 6. Manifest

`manifest.json` is the package entry point. It declares the format version, package identity, Liveable identity summary, structured components, assets, capability requirements, and integrity metadata.

`package.id` identifies a particular export. `liveable.id` identifies the entity. These identifiers MUST NOT be conflated.

Each component descriptor MUST identify its path, media type, schema URI, required status, byte size, and SHA-256 digest. Each asset descriptor MUST identify its path, media type, required status, byte size, and SHA-256 digest.

The manifest itself is not included in its own component checksum list. A future signature profile may define a canonical signing input. Core v0.1 does not require digital signatures.

## 7. Validation and import

An importer MUST validate the manifest and identity document against the applicable JSON Schemas. It MUST verify each declared component and asset size and SHA-256 digest before trusting its contents. It MUST reject unsafe archive paths, duplicate paths, path traversal, unsupported compression, and archives exceeding implementation-defined safety limits.

Unknown optional components MAY be skipped with a warning. Unknown required components MUST prevent a full import. Unsupported capabilities MUST be reported. A parser successfully reading JSON does not mean that a Liveable was successfully imported.

Import outcomes may be full, partial, restricted, or rejected. Implementations SHOULD provide a report describing omitted components and capability degradation.

## 8. Clone and migration

**Clone** creates an independent copy while the source remains. **Migration** intends to continue the same Liveable identity on a destination platform and SHOULD include lineage and export revision metadata. PoLiS does not guarantee distributed synchronization or prevent two independently running branches from diverging.

## 9. World and runtime boundaries

PoLiS is an interchange format, not a World runtime specification. Importing a package MUST NOT automatically create canonical World events, place an entity, execute behavior, grant privileges, or mutate canonical state. The receiving platform decides whether and how to instantiate the imported Liveable under its own rules.

## 10. Security

Packages are untrusted input. Importers MUST apply limits to archive entry count, individual file size, total decompressed size, nesting/path length, and parser resource use. Paths MUST be normalized and checked to prevent path traversal and absolute-path writes. Importers MUST NOT execute package content.

SHA-256 verifies byte integrity relative to the digest in the manifest; it does not prove authorship, ownership, authenticity, or permission. Digital signatures are outside the mandatory Core v0.1 profile.

## 11. Versioning and extensibility

The format version uses semantic versioning. Component schemas are independently versioned. Core component identifiers and semantics are reserved. Extensions SHOULD use collision-resistant namespaced identifiers. Unknown optional extensions may be ignored; unknown required extensions prevent full compatibility.

## 12. Out of scope

PoLiS does not define world simulation, physics, navigation, scheduling, agent execution, LLM inference, database persistence, authentication, runtime authorization, cross-platform synchronization, or deterministic visual generation.

## 13. Conformance status

This document and the accompanying schemas are an initial public proposal, not a ratified standard. Conformance claims SHOULD identify the exact PoLiS version and component schemas supported. A future conformance suite is expected to define package-level checks beyond JSON Schema validation.
```
PoLiS specification, documentation, and JSON Schema files are licensed under the
Creative Commons Attribution 4.0 International License (CC BY 4.0).

You are free to share and adapt these materials for any purpose, including
commercial purposes, provided that appropriate credit is given, a link to the
license is provided, and changes are indicated.

Full license text:
https://creativecommons.org/licenses/by/4.0/legalcode

SPDX-License-Identifier: CC-BY-4.0

This license does not grant rights to example Liveable data, characters,
trademarks, images, audio, or other assets unless a separate license or
permission explicitly says so. Future reference implementation source code
may be distributed under a separate software license, proposed as Apache-2.0.
