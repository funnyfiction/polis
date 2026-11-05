# What the heck is PoLiS?

**PoLiS** stands for **Portable Liveables Interchange Standard**.

In plain English: PoLiS is a proposed open format for packing up the identity and portable data of a digital entity, so another platform can understand it and potentially host it.

Think of a character you have spent years building: their identity, personality, memories, relationships, visual traits, and history. Today, that information is often trapped inside the app, game, or AI service where the character was created.

PoLiS is an attempt to make that data more portable.

> **Identity travels. Platforms remain independent.**

## First: what is a Liveable?

A **Liveable** is a digital entity with an identity and potentially portable characteristics or state.

It could be:

- an AI character;
- an NPC in a virtual world;
- a virtual pet;
- a digital plant;
- an object with a history;
- or another persistent digital entity.

It does not have to be intelligent, autonomous, or even capable of doing anything. A goldfish in a virtual aquarium can be a Liveable. So can the plant next to the tavern window.

## What can a PoLiS package carry?

A PoLiS package can describe a Liveable through optional components, including:

- **Identity** — the entity's stable identity and semantic type;
- **Properties and state** — characteristics and a snapshot of its condition;
- **Personality** — traits and preferences;
- **Behavior** — declarative behavior descriptions;
- **Cognition** — cognition-related data, without requiring a particular AI provider;
- **Memories and relationships** — accumulated experience and connections;
- **Goals and continuity** — objectives and information that helps preserve a continuing identity;
- **Visual Identity** — defining visual characteristics and references for image, video, audio, or 3D workflows;
- **Provenance and rights** — information about origin, authorship, licensing, consent, and transfer restrictions;
- **Assets** — images, audio, video, and 3D resources.

Not every Liveable needs every component. A flower does not need a personality file. A character may need quite a few.

## What does a `.polis` file look like?

The proposed package format uses familiar, inspectable building blocks:

- **JSON** for structured, human-readable data;
- **JSON Schema Draft 2020-12** for the public validation contract;
- **TAR** as the package container;
- **Zstandard** for compression;
- **SHA-256** checksums for integrity verification.

A package contains a `manifest.json`, an `identity.json`, and any optional components and assets.

No proprietary runtime is required just to inspect the package.

## Does PoLiS move a character into another world automatically?

No. And that distinction matters.

PoLiS carries portable identity and data. It does **not** carry authority over the destination platform.

A receiving world or application remains in control of its own rules. Importing a package does not automatically:

- create or place an entity in a world;
- execute behavior or scripts;
- grant permissions or privileges;
- overwrite the destination's canonical state;
- create events in the destination world.

The receiving platform decides what it can accept and how an imported Liveable can be represented.

> **We can move the description of an entity. We do not move the world's authority with it.**

## Is this only for AI characters?

No.

AI characters are an obvious use case, but PoLiS is intended to cover digital entities more broadly: NPCs, animals, plants, objects, and other persistent entities.

It is also designed to be useful beyond virtual worlds. Generative tools may use Visual Identity and associated assets as reference material. Creative applications may exchange entity descriptions. Different platforms may map portable data into their own runtime models.

PoLiS does not prescribe a database, programming language, simulation engine, AI model, or platform architecture.

## Does PoLiS guarantee that a character will look or behave exactly the same everywhere?

No. Portability is not magic.

Different platforms have different capabilities, rules, models, and representations. A destination may support only some components, or may interpret them differently. A PoLiS importer should report unsupported or omitted data rather than pretending that everything transferred perfectly.

PoLiS aims to make identity and data exchange more explicit and interoperable. It does not promise perfect runtime equivalence.

## Is PoLiS finished?

Not even close. This is an **Initial Public Standard Proposal, v0.1.0**.

The proposal and draft JSON Schemas are published for review and discussion. The format, schemas, and governance process may evolve before a stable release.

We want developers, world builders, AI researchers, digital artists, and anyone working with persistent digital entities to challenge the assumptions, find gaps, and help shape the standard.

## How is it licensed?

The specification, documentation, and JSON Schemas are published under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

That allows people to share and adapt those materials, including commercially, provided they follow the attribution terms.

Example Liveable identities, character data, images, audio, other assets, trademarks, and future software implementations are not automatically covered by that license. Check the relevant file or project notice.

## Where can I find it?

- **GitHub repository:** https://github.com/funnyfiction/polis
- **Public Standard Proposal:** [SPECIFICATION.md](./SPECIFICATION.md)
- **JSON Schemas:** [schemas/v0.1](./schemas/v0.1/)
- **License:** [LICENSE](./LICENSE)

## Why are we doing this?

Because digital entities should not be permanently locked into the platforms where they were created.

A character should be more than a database row owned by one app. A digital companion, NPC, pet, or other Liveable should have a way to carry its identity and relevant history between systems—while each destination remains free to make its own decisions.

That's the idea behind PoLiS.

**Identity travels. Platforms remain independent.**

---

*PoLiS is an open standard proposal published by FunnyFiction. Project founder and original author: Gene Semerenko.*
