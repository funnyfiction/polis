# PoLiS — Portable Liveables Interchange Standard

**An open proposal for portable digital identities.**

Imagine spending years building an AI character: giving them a name, personality, memories, relationships, appearance, and a history.

Then imagine wanting to move that character to another game, virtual world, AI service, or creative tool.

Usually, you can't take all of that with you. The character's identity and history are tied to the platform where they were created. Move to another platform, and you may have to rebuild them from scratch.

**PoLiS is an attempt to solve this problem.**

It defines an open package format for describing a digital entity and the information that may need to travel with it. Another platform can read the package, understand what it contains, and decide what it can use.

> **Identity travels. Platforms remain independent.**

## What can travel with a digital entity?

PoLiS calls a digital entity with an identity a **Liveable**.

A Liveable can be almost anything that has a persistent identity:

- an AI character or virtual companion;
- an NPC in a game or virtual world;
- a virtual pet or animal;
- a digital plant;
- an object with a history;
- another persistent digital entity.

It does not have to think, speak, or act. A goldfish in a virtual aquarium can be a Liveable just as much as an AI bartender.

A PoLiS package can carry information such as:

- **Identity** — who or what the entity is.
- **Properties and state** — its characteristics and a snapshot of its condition.
- **Personality** — traits and preferences.
- **Behavior** — descriptions of how it may behave.
- **Cognition** — information related to its thinking capabilities, without tying it to one AI provider.
- **Memories and relationships** — experiences and connections.
- **Goals and continuity** — information that helps preserve its ongoing identity.
- **Visual Identity** — defining visual traits and reference material for image, video, audio, or 3D workflows.
- **Provenance and rights** — origin, authorship, licensing, consent, and transfer restrictions.
- **Assets** — images, audio, video, and 3D resources.

These parts are optional. A flower does not need memories or a personality. A character may need several components to preserve what makes them recognizable.

## What PoLiS does — and does not do

PoLiS provides a shared way to package and exchange identity data. It does not force platforms to work the same way.

When a Liveable is imported, the receiving platform remains in control. It decides whether to accept the package, which parts it supports, and how the imported entity can exist in its world.

A PoLiS package does **not** automatically:

- create or place an entity in another world;
- execute scripts or behavior;
- grant permissions or privileges;
- overwrite the destination platform's state;
- create events or perform actions in the destination world.

In short: **PoLiS can carry a description of an entity, but it cannot carry authority over another platform.**

Nor does PoLiS guarantee that a character will look or behave exactly the same everywhere. Platforms have different capabilities, rules, and AI models. Some data may not be supported or may need to be adapted.

## How is a `.polis` package built?

The proposed format uses familiar, inspectable technologies:

- **JSON** for structured, human-readable data;
- **JSON Schema Draft 2020-12** for describing and validating the data structure;
- **TAR** as the package container;
- **Zstandard** for compression;
- **SHA-256** checksums to verify component and asset integrity.

A `.polis` file is a Zstandard-compressed TAR archive.

Its required `manifest.json` and `identity.json` files live at the archive root. Optional component JSON files are grouped under `components/`, and binary resources under `assets/`.

No proprietary runtime is needed just to inspect a package.

## Repository contents

This repository contains the public proposal, draft validation schemas, and example Liveables:

- [Specification](SPECIFICATION.md)
- [JSON Schemas](schemas/v0.1/)
- [Examples](examples/)
- [License](LICENSE)
- [What the heck is PoLiS? — a plain-language introduction](%21what-the-heck-is-this.md)

## Project status

**Initial Public Standard Proposal v0.1.0**

PoLiS is an early proposal, not a finalized or ratified standard. The specification and draft schemas are published for review. Package rules and schemas may change before a stable release.

We want developers, world builders, AI researchers, digital artists, and anyone working with persistent digital entities to challenge the assumptions, find gaps, and help shape the proposal.

## Contributing

Issues and pull requests are welcome.

When proposing a change, please indicate whether it affects:

- the data model — what information a package can describe;
- the package structure — how files are organized;
- validation — what a valid package must contain;
- implementation guidance — recommendations for software that reads or writes PoLiS packages.

The goal is to make the proposal clearer and more useful through open discussion and review.

## Licensing

The specification (`SPECIFICATION.md`), repository documentation, and JSON Schemas in `schemas/` are licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Copyright © 2026 Gene Semerenko. Published by FunnyFiction.

Example Liveable data and media assets must carry their own explicit license or usage permissions. The specification license does not grant rights to those assets, trademarks, or future software implementations. Any future reference implementation source code will be licensed separately under **Apache License 2.0**.

## Governance

FunnyFiction is the publishing home for PoLiS. It is currently an independent project organization; this does not imply that a separately registered legal entity exists.

The project aims to develop in the open:

- Changes are proposed and discussed publicly through GitHub issues and pull requests.
- Changes to the standard are reviewed and documented before release.
- Published versions use explicit version numbers and should remain available as historical releases. Their meaning should not be silently changed; updates belong in subsequent versions.
- Independent developers and organizations are welcome to contribute or maintain their own forks, subject to the license and applicable trademark rights.

The project founder and original author is Gene Semerenko. The governance process may evolve as the project and community grow, with changes documented publicly.

---

**PoLiS is an open standard proposal published by FunnyFiction.**

**Identity travels. Platforms remain independent.**
