
# PoLiS
## Portable Liveables Interchange Standard

**Standard Proposal — Version 0.1.0**

**Status:** Initial Public Proposal  
**Category:** Open Interchange Standard  
**Package Extension:** `.polis`  
**Serialization:** JSON  
**Schema Validation:** JSON Schema  
**Container:** TAR  
**Compression:** Zstandard  
**Integrity:** SHA-256

---

# 1. Abstract

Digital entities are increasingly becoming persistent participants in virtual worlds, interactive environments, AI applications, and generative media workflows.

These entities may be intelligent characters, autonomous agents, non-player characters, animals, plants, objects, or other persistent elements of digital environments.

However, their identity and state are typically tied to the specific platform, application, database, or AI provider in which they were created.

Moving an entity between systems often means losing important parts of what makes it recognizable and meaningful: its identity, personality, appearance, memories, behavioral characteristics, relationships, and history.

**PoLiS (Portable Liveables Interchange Standard)** proposes an open, platform-independent format for describing, packaging, and transferring digital entities while preserving their portable identity and continuity.

PoLiS is designed to work across:

- Virtual worlds and persistent simulations.
- AI character platforms and agent systems.
- Image, video, audio, and 3D generation tools.
- Digital asset ecosystems.
- Other applications that create or consume persistent digital entities.

PoLiS separates an entity's identity and portable data from the infrastructure that executes or hosts it.

The goal is to make digital entities portable, reusable, and interoperable across independent systems.

# 2. The Problem

Digital entities are becoming increasingly sophisticated.

An AI character may have a distinct personality, persistent memories, relationships, goals, and a recognizable visual identity.

A virtual animal may have a species, physical characteristics, health state, behavioral patterns, and a history.

A plant may have a species, growth stage, environmental preferences, and a visual appearance that changes over time.

A digital object may have a stable identity, origin, properties, and historical significance.

Despite these similarities, most platforms represent these entities using proprietary data structures and platform-specific storage.

This creates several problems:

**Platform Lock-in**

An entity created in one platform cannot easily be transferred to another without rebuilding its data.

**Identity Fragmentation**

Visual appearance, personality, behavior, and other defining characteristics are often stored separately or tied to platform-specific implementations.

**Loss of Continuity**

Memories, history, relationships, and other accumulated information may not survive migration.

**AI Provider Dependency**

AI characters may be coupled to particular models, prompts, APIs, or runtime implementations.

**Limited Reusability**

A character created for a virtual world may be difficult to reuse as a reference in an image generator, video generator, or 3D creation system.

PoLiS addresses these problems by defining a common interchange format for digital entities.

# 3. Design Philosophy

PoLiS is built around five principles.

## 3.1 Identity Independence

A Liveable's identity must not depend on the platform, database, runtime, or AI provider hosting it.

The same Liveable should be recognizable as the same underlying entity when transferred between compatible systems.

## 3.2 Universal Applicability

PoLiS must support different kinds of digital entities without requiring them to share the same characteristics.

An AI character, a goldfish, a flower, and a historical object should all be representable using the same foundational model.

Not every Liveable needs personality, cognition, memory, or behavior.

Components are optional according to the nature of the entity.

## 3.3 Platform Independence

PoLiS must not require a particular programming language, database, operating system, virtual world engine, AI provider, or application runtime.

Any implementation capable of processing the standard should be able to inspect and validate a compatible package.

## 3.4 Continuity Preservation

Where applicable, a Liveable should be able to carry its accumulated experience, memories, relationships, and historical context between systems.

The standard must preserve the distinction between identity, historical information, and current runtime state.

## 3.5 Creative Interoperability

A Liveable should not be limited to the environment in which it was created.

Its identity and reference materials should be reusable by creative and generative systems, including image, video, audio, and 3D generation tools.

# 4. What Is a Liveable?

A **Liveable** is a transferable digital entity with an identity and potentially portable characteristics, state, behavior, cognition, or continuity.

A Liveable does not have to be intelligent, autonomous, interactive, or capable of performing actions.

Examples include:

| Category | Examples |
|---|---|
| Intelligent Characters | AI characters, digital humans, replicants |
| Simulated Characters | NPCs, virtual inhabitants |
| Animals | Fish, pets, wildlife |
| Plants | Flowers, trees, virtual vegetation |
| Objects | Furniture, artifacts, persistent items |
| Environments | Other persistent digital entities, where supported by an implementation |

The category system is extensible.

Implementations may define more specific types without requiring changes to the core standard.

Examples:

- `character.intelligent_replicant`
- `character.npc`
- `animal.fish.goldfish`
- `plant.flower`
- `object.furniture`

A Liveable's type describes what it represents. It does not determine which capabilities a receiving platform must support.

# 5. Universal Liveable Model

PoLiS defines a universal model consisting of an identity and a collection of optional components.

## 5.1 Identity

Identity is the mandatory foundation of every Liveable.

It describes the stable identity of the entity independently of its runtime implementation.

Typical information includes:

- Stable identifier.
- Semantic type.
- Name and display name.
- Description.
- Origin and provenance references.
- Tags and classification.

The identity identifier must remain stable across exports and compatible migrations.

It must not be confused with a database ID, runtime instance ID, or package ID.

## 5.2 Properties and State

Describes the characteristics and current state of a Liveable.

Examples include:

- Physical characteristics.
- Health and condition.
- Growth stage.
- Environmental requirements.
- Current activity.
- Custom domain-specific properties.

Properties describe what an entity is or what characteristics it has.

State describes its current condition.

The receiving platform remains responsible for deciding whether imported state can be restored.

## 5.3 Personality

Describes individual psychological and communication characteristics where applicable.

Examples include:

- Temperament.
- Personality traits.
- Values.
- Communication style.
- Preferences.
- Boundaries.

Personality is optional and does not imply the presence of an AI runtime.

## 5.4 Behavior

Describes behavioral characteristics and declarative behavioral rules.

Examples include:

- Habits.
- Preferences.
- Needs.
- Reactions.
- Behavioral patterns.
- Conditional behavior declarations.

PoLiS Core does not define executable behavior code.

Behavior descriptions represent portable behavioral information, not authority to execute actions in a receiving environment.

## 5.5 Cognition

Describes cognitive characteristics and requirements where applicable.

Examples include:

- Cognitive capabilities.
- Memory organization.
- Reasoning requirements.
- Goal formation.
- Context requirements.
- Decision-making characteristics.

PoLiS does not prescribe a specific AI architecture or language model.

## 5.6 Memories and Relationships

Describes accumulated experience and relational information.

Memories may include episodic, semantic, relational, procedural, or reflective information.

Relationships describe connections between Liveables or other referenced entities.

References to entities not present in the receiving system should remain identifiable as unresolved references rather than being silently discarded.

Memory and relationship data must preserve relevant provenance and transfer restrictions.

## 5.7 Continuity

Describes information needed to preserve an entity's historical continuity.

Examples include:

- Experience summaries.
- Development history.
- Significant events.
- Historical milestones.
- Migration lineage.

PoLiS does not require the complete event history of the original world to be included in a package.

## 5.8 Visual Identity

Visual Identity is a core PoLiS component.

It describes the defining visual characteristics that should remain recognizable across different rendering and generation systems.

It may include:

- Facial characteristics.
- Body proportions.
- Distinctive physical features.
- Colors and patterns.
- Species-specific characteristics.
- Visual invariants.
- Preferred representation styles.
- Reference asset declarations.

Visual Identity is particularly important for generative AI applications.

A Liveable package may contain multiple reference images for different purposes, such as facial identity, full-body appearance, clothing, distinctive features, or multiple views.

A receiving image or video generator can use these references to construct its own generation context.

PoLiS describes visual identity and provides reference material. It does not guarantee identical generated results across different models or tools.

## 5.9 Presentation and Assets

Presentation describes how a Liveable is represented in an application.

Assets may include:

- Images.
- Audio.
- Voice samples.
- Video.
- 3D models.
- Textures.
- Other binary resources.

Binary assets are stored separately from structured JSON data.

## 5.10 Provenance and Rights

Provenance describes where information originated and how it relates to the entity.

Rights and permissions describe applicable ownership, consent, licensing, and transfer restrictions.

A package must not imply that all included information is automatically transferable or freely reusable.

Personal information and third-party data require appropriate handling and permission.

# 6. Package Format

PoLiS packages use a combination of established technologies.

| Layer | Technology | Purpose |
|---|---|---|
| Serialization | JSON | Structured, human-readable data |
| Schema | JSON Schema | Public structural contract |
| Container | TAR | Package composition |
| Compression | Zstandard | Efficient compression |
| Integrity | SHA-256 | Component integrity verification |

The standard package extension is:

`.polis`

A PoLiS package is a TAR archive compressed using Zstandard.

The archive must follow the package structure and validation rules defined by the standard.

## 6.1 Package Structure

A typical package may look like this:

```text
rachel.polis
│
├── manifest.json
├── identity.json
├── visual-identity.json
├── provenance.json
├── signature.json
│
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
│
└── assets/
    ├── portrait.webp
    ├── full-body.webp
    └── voice.ogg
```

This is an illustrative structure.

Only `manifest.json` and `identity.json` are mandatory in the initial proposal.

Other components and assets are optional.

Directories are used for logical grouping, not merely to place a single file inside an unnecessary subdirectory.

## 6.2 Manifest

`manifest.json` is the package entry point.

It describes:

- Format identification.
- Format version.
- Package identity.
- Liveable identity reference.
- Component registry.
- Component schema references.
- Required capabilities.
- Integrity metadata.

The manifest allows an importer to inspect and validate a package before processing its full contents.

## 6.3 Package Identity and Liveable Identity

PoLiS distinguishes between two identifiers.

**Package ID**

Identifies a specific exported package.

Every export produces a new package ID.

**Liveable ID**

Identifies the underlying digital entity.

It remains stable across exports and compatible migrations.

A third identifier may exist inside a receiving platform:

**Runtime ID**

Identifies a particular instance of the Liveable inside that platform.

Runtime IDs are implementation-specific and are not portable identity identifiers.

# 7. Import and Interoperability

PoLiS defines a package format, not a universal execution environment.

A receiving platform is responsible for interpreting imported components and mapping them to its own internal representation.

An import process should:

1. Inspect the package.
2. Validate the archive structure.
3. Parse the manifest.
4. Verify component integrity.
5. Validate supported JSON Schemas.
6. Inspect component compatibility.
7. Evaluate required capabilities.
8. Check provenance and transfer restrictions.
9. Map supported information into the receiving platform.
10. Report the import result.

Import outcomes may include:

- Full import.
- Partial import.
- Restricted import.
- Rejected import.

A successful JSON parse does not imply a successful Liveable import.

## 7.1 Capability Compatibility

A receiving platform may not support every capability described by a Liveable.

For example, a platform may support visual identity and personality but not persistent memory.

The importer should report unsupported capabilities and describe any resulting degradation.

Unknown optional components may be skipped with a warning.

Unknown required components must prevent a fully compatible import.

## 7.2 Clone and Migration

PoLiS distinguishes between two transfer operations.

**Clone**

Creates an independent copy of a Liveable.

The source remains unchanged. The resulting copies may evolve independently.

**Migration**

Transfers a Liveable's continuity to another platform.

Migration is intended to preserve the same underlying identity and its historical lineage.

Migration metadata should describe the source, destination, export revision, and relevant continuity information.

PoLiS does not guarantee that two independent platforms can maintain perfectly synchronized copies of one Liveable.

# 8. Generative AI Interoperability

PoLiS is designed to be useful beyond virtual worlds.

A PoLiS package can serve as a structured reference for generative systems.

## 8.1 Image Generation

An image generator can consume:

- Visual Identity.
- Reference images.
- Appearance characteristics.
- Relevant personality or presentation context.
- Scene-specific instructions supplied separately.

This allows a Liveable to be represented in different scenes while retaining its defining visual characteristics.

## 8.2 Video Generation

A video generator may use the same identity and visual references to create moving representations of a Liveable.

## 8.3 Voice Generation

Voice-related assets and presentation metadata may be used by compatible audio systems, subject to applicable rights and permissions.

## 8.4 3D Generation

A 3D generation system may use appearance references, proportions, species information, and available assets to produce a compatible representation.

PoLiS does not require generative tools to implement the entire standard.

Tools may consume only the components relevant to their tasks.

A specialized adapter can translate PoLiS components into the input format expected by a particular generation system.

# 9. Platform and AI Independence

PoLiS does not prescribe:

- A particular LLM provider.
- A particular language model.
- A particular prompt format.
- A particular agent framework.
- A particular database.
- A particular simulation engine.
- A particular application runtime.

A Liveable's identity and portable data should remain independent of these implementation choices.

An AI character may change its underlying model without changing its PoLiS identity.

However, different models and platforms may produce different behavior. PoLiS preserves portable descriptions and continuity data, not deterministic behavioral equivalence.

# 10. Security and Trust

PoLiS packages may contain personal information, private memories, copyrighted assets, or other restricted material.

Implementations should treat imported packages as untrusted input.

Importers must validate:

- Archive paths.
- File counts.
- File sizes.
- Decompressed size limits.
- JSON structure.
- Component schemas.
- Component checksums.
- Supported media types.

Core packages must not contain executable code.

Imported behavior declarations must not be executed automatically.

Importing a Liveable must not grant it privileges in the receiving platform.

Digital signatures may be used to establish package authenticity and publisher identity.

A valid integrity checksum proves that data has not changed relative to the expected checksum. It does not independently prove authorship, ownership, or permission to use the data.

# 11. Extensibility

PoLiS is intended to be extensible.

Implementations may define additional components and more specific Liveable types.

Extensions should use globally unique namespaces or otherwise collision-resistant identifiers.

Extensions must not redefine the meaning of existing core components.

The initial standard defines the foundational model and package structure.

Additional component specifications may be developed independently.

# 12. What PoLiS Does Not Define

PoLiS is an interchange standard, not a complete virtual world or AI runtime specification.

It does not define:

- World simulation.
- Physics.
- Navigation.
- Scheduling.
- Agent execution.
- LLM inference.
- Database persistence.
- User authentication.
- Runtime authorization.
- Cross-platform synchronization.
- Identical visual generation results.

These responsibilities belong to the systems that create, host, or consume Liveables.

A PoLiS package transfers identity and portable data. It does not transfer authority over the receiving environment.

# 13. Reference Implementation

A reference implementation is expected to demonstrate:

- Package creation.
- Package inspection.
- JSON Schema validation.
- Component integrity verification.
- Liveable export and import.
- Optional component handling.
- Capability compatibility reporting.
- Asset extraction.
- Clone and Migration metadata.

The first reference implementation is intended to use Consent Bar as an initial test environment.

However, the standard itself must remain independent of Consent Bar.

Independent implementations are encouraged.

# 14. Standard Development

This document represents the initial public proposal for PoLiS Core.

The next development stages are expected to include:

1. Formal Universal Liveable Model.
2. Formal Manifest JSON Schema.
3. Core component JSON Schemas.
4. Visual Identity specification.
5. Package integrity and signature specification.
6. Reference exporter and importer.
7. Interoperability tests between independent implementations.

The standard should evolve through public technical discussion and implementation feedback.

# 15. Conclusion

Digital entities should not be permanently locked into the platforms where they were created.

Their identity, appearance, characteristics, and accumulated continuity should be capable of moving between compatible systems.

An AI character should be able to move between virtual worlds.

A digital animal should be reusable in different simulations.

A flower should retain its identity and visual characteristics across creative applications.

A character should be usable as a reference in an image generator, video generator, or 3D creation system.

PoLiS proposes a common foundation for these possibilities.

**Identity travels. Platforms remain independent.**

---

## PoLiS

**Portable Liveables Interchange Standard**

An open standard for portable identity across digital worlds and generative systems.

**Initial Public Proposal — v0.1.0**
