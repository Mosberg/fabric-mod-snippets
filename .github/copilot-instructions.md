# AI Project Instructions

These notes help AI coding agents work effectively in this repository.

## Big Picture

- **Project Type:** VS Code snippet extension (not a mod) providing ready-made code templates for Minecraft Fabric mod development.
- **Distribution:** Published to VS Code Marketplace (`vsce package`); snippets contribute via [package.json](../package.json) `contributes.snippets`.
- **Target Developer:** Minecraft modders using Fabric 1.21.11, Yarn mappings, Loom, Java 21.
- **Scope:** Registries (items, blocks, entities), data generation, mixins, screens/GUIs, networking, commands, events, item groups, worldgen, Gradle config, and fabric.mod.json templates.
- **Key Constraint:** All snippets use modern Fabric patterns (`Identifier.of()`, `Registry.register()`, `FabricDataGenerator.Pack`).

## Snippet Architecture

### Structure

- **Core snippets:** [snippets/java/fabric.json](../snippets/java/fabric.json) (Java) and [snippets/json/fabric.json](../snippets/json/fabric.json) (JSON) – registry helpers (`reg.*`), basic items/blocks/entities, datagen setup (mirrors in [fabric.code-snippets](../snippets/java/fabric.code-snippets) for consistency).
- **Domain-specific files (Java):** Each `.code-snippets` file targets a single concern:
  - **Items & Blocks:** `fabric.item.registry.code-snippets`, `fabric.block.registry.code-snippets`, `fabric.block.with.item.code-snippets`, `fabric.items.advanced.code-snippets` (armor, tools, food, tooltips, fuel).
  - **Entities:** `fabric.entity.type.code-snippets`, `fabric.entity.attributes.code-snippets`.
  - **Data Generation:** `fabric.datagen.entrypoint.code-snippets` + helper providers for models, loot, recipes, tags.
  - **Runtime:** `fabric.events.code-snippets`, `fabric.commands.code-snippets`, `fabric.networking.code-snippets`, `fabric.screen.code-snippets`, `fabric.itemgroup.code-snippets`.
  - **Mixins & Worldgen:** `fabric.mixins.code-snippets`, `fabric.world.generation.code-snippets`.
- **Properties/Gradle (JSON language):** `gradle.code-snippets`, `gradle.properties.code-snippets` (versions, JVM tuning, build flags) now live under `snippets/json`.
- **Contribution Wiring:** Every `.code-snippets` file is registered in [package.json](../package.json) `contributes.snippets` with `language` and `path` pointing to `snippets/java` or `snippets/json`.

### Discovery Rule

When adding a snippet, place it in the appropriate domain file:

- Registry/core patterns → [snippets/java/fabric.json](../snippets/java/fabric.json) or [snippets/java/fabric.code-snippets](../snippets/java/fabric.code-snippets).
- Single-topic additions → their domain file (e.g., new tool item variant → `fabric.items.advanced.code-snippets`).
- **File organization drives IDE discoverability** – users type a prefix like `item.` to see all item variants in one namespace.

## Conventions

- **Prefixes:** Short, discoverable patterns using `domain.variant` format (e.g., `reg.item`, `block.ore`, `packet.send.server`, `mixin.inject`, `worldgen.ore`). Enables prefix-based IDE browsing (type `item.` to see all item snippets).
- **Placeholders:** Numbered and descriptive (`${1:TYPE}`, `${2:NAME}`, `${3:item_name}`). Ordered for left-to-right tab navigation.
- **Optional content:** Provided as commented lines (e.g., `.luminance()`, `.statusEffect()`, `.canAlwaysEat()`) – users uncomment when needed.
- **Registration Style:** Always use `Identifier.of(MOD_ID, "name")` + `Registry.register(Registries.X, ...)` – no string concatenation; modern, type-safe, and explicit.
- **Default Settings:** Block snippets include `.requiresTool()` unless contextually wrong; entity snippets include attribute registration to prevent crashes.
- **DataGen Pattern:** Entrypoint creates `FabricDataGenerator.Pack`; providers are per-domain (models, loot, recipes, tags); users add their domain classes via `pack.addProvider(...)`.
- **Attribute Registration:** Entities must call `FabricDefaultAttributeRegistry.register()` with default attributes in a separate snippet or setup method.
- **Helper Methods:** `fabric-mod-snippets.code-snippets` shows registry helpers (`registerItem()`, `registerBlock()`) to encourage centralized registration logic.

## Adding or Updating Snippets

- **Edit Live Snippets:** Core patterns live in [snippets/java/fabric.json](../snippets/java/fabric.json); domain-specific snippets live in their file under [snippets/java](../snippets/java). Keep names/descriptions concise (e.g., "Registry: Item", "Item: Basic").
- **Wire Additional Files:** Add entries under `contributes.snippets` in [package.json](../package.json) pointing into `snippets/java` (language `java`) or `snippets/json` (language `properties`/`json`).
- **Prefix Design:** Prefer `domain.variant` (e.g., `block.ore`, `packet.send.server`, `event.player.join`) so users can type the domain to browse all variants.
- **Body Style:** Keep imports implicit; surface common tweaks via placeholders; include commented optional lines (luminance, sounds, effects, conditions); keep `${2:MOD_ID}` for consistency.
- **Filename Convention:** Use `fabric.<domain>.<variant>.code-snippets` (e.g., `fabric.items.advanced.code-snippets`, `fabric.commands.code-snippets`).

## Validation & Testing

- **JSON Validity:** Ensure all `.json` and `.code-snippets` files remain valid JSON. Use an IDE or `jq` to validate: `jq . snippets/java/fabric.json > /dev/null` and `jq . snippets/json/gradle.code-snippets > /dev/null`.
- **Snippet Schema:** Each snippet must have `prefix` (string), `body` (array of strings or single string), and `description` (string).
- **Manual IDE Test:** Open a Java or JSON file in VS Code and type a known prefix (e.g., `reg.item`) to confirm contributions are discoverable and content is correct.
- **Marketplace Packaging:** Use `vsce package` to build the extension locally before publishing. No build scripts in this repo; external tooling handles packaging.

## Key Files & Examples

- **Core Registry:** [snippets/java/fabric.json](../snippets/java/fabric.json) → `reg.item`, `reg.block`, `reg.entity` (modern `Identifier.of` + `Registry.register` pattern).
- **Items & Blocks:** [snippets/java/fabric.items.advanced.code-snippets](../snippets/java/fabric.items.advanced.code-snippets) → armor, tools, food, tooltips, fuel variants.
- **DataGen:** [snippets/java/fabric.datagen.entrypoint.code-snippets](../snippets/java/fabric.datagen.entrypoint.code-snippets) → entrypoint setup; model/loot/recipe providers defined in domain files.
- **Networking:** [snippets/java/fabric.networking.code-snippets](../snippets/java/fabric.networking.code-snippets) → custom payloads, S2C/C2S handlers, packet IDs.
- **Mixins:** [snippets/java/fabric.mixins.code-snippets](../snippets/java/fabric.mixins.code-snippets) → inject, redirect, accessor patterns with proper `@At` targets.
- **Worldgen:** [snippets/java/fabric.world.generation.code-snippets](../snippets/java/fabric.world.generation.code-snippets) → ore placement, configured/placed features, biome modifications.

## When Editing package.json

- **Keep Aligned:** Every snippet file in `snippets/java` or `snippets/json` should have a corresponding entry in `contributes.snippets` with correct `language` and relative `path`.
- **Language Mapping:** Java snippets use `language: "java"`; properties/Gradle snippets use `language: "properties"`; JSON snippets (if any) use `language: "json"`.
- **Avoid Duplication:** Don't register the same file twice unless intentionally targeting different languages.

## Key Files

- [snippets/java](../snippets/java): all Java-facing snippets (core registry, domain files, mixins, worldgen, networking, commands, events, screens, item groups).
- [snippets/json](../snippets/json): Gradle/properties and JSON-facing snippets (gradle.\* files, fabric.json for JSON language contribution).
- [package.json](../package.json): snippet contributions — ensure new files are added under `contributes.snippets` with correct language and path into `snippets/java` or `snippets/json`.
- [README.md](../README.md): prefix catalog, conventions, and version targets.
