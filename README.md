# Fabric Mod Snippets

A comprehensive snippet pack for Minecraft **Fabric mod development** in VS Code.

This extension provides ready‑to‑use snippets for:

- Registries
- Items
- Blocks
- Block Items
- Entities
- Entity Renderers
- Data Generation (models, loot tables, recipes, tags)
- Fabric entrypoints
- Gradle properties
- Loom build scripts
- Fabric mod JSON

Designed for **Fabric 1.21.11**, **Yarn mappings**, and modern Loom.

## Usage

Type any snippet prefix (e.g., `reg.item`, `block.basic`, `datagen.model`) and VS Code will suggest completions.

## Snippet Categories (prefix-first)

| Category         | Prefix Examples                                                                     |
| ---------------- | ----------------------------------------------------------------------------------- |
| Registries       | `reg.item`, `reg.block`, `reg.blockitem`, `reg.entity`                              |
| Items & Blocks   | `item.basic`, `item.food`, `block.basic`, `block.ore`, `itemgroup.*`                |
| Entities         | `entity.class`, `entity.renderer`, `fabric-entity`, `fabric-entity-attrs`           |
| Data Generation  | `datagen.setup`, `datagen.entry`, `fabric-model-provider`, `fabric-recipe-provider` |
| Networking       | `packet.id`, `packet.server.handler`, `packet.send.*`                               |
| Commands         | `command.register`, `command.arg.*`, `command.feedback`                             |
| Events           | `event.player.block.break`, `event.server.tick`, `event.loot.modify`                |
| Screens/GUI      | `screen.handler`, `screen.handled`, `screen.register.client`                        |
| Mixins           | `mixin`, `mixin.inject`, `mixin.modifyconstant`, `mixin.overwrite`                  |
| Worldgen         | `worldgen.ore`, `worldgen.feature.configured`, `worldgen.structure`                 |
| Gradle/Props     | `gradle.jvm`, `gradle.flags`, `fabric-gradle-full`, `mod.props`                     |
| Mod JSON helpers | `fid` and other Identifier helpers for modern registration                          |

## Contributing

Pull requests welcome.
Issues and feature requests can be submitted on GitHub.

## License

MIT

## Catalog by File (source of truth)

### Java snippets (snippets/java)

- [snippets/java/fabric-mod-snippets.code-snippets](snippets/java/fabric-mod-snippets.code-snippets) — `fabric-item-reg`, `fabric-block-reg`, `fabric-entity-reg`, `fabric-registry-setup`, datagen bundle and providers.
- [snippets/java/fabric.code-snippets](snippets/java/fabric.code-snippets) — `reg.item`, `reg.block`, `reg.blockitem`, `reg.entity`, `item.basic`, `item.food`, `block.basic`, `block.ore`, `entity.class`, `entity.renderer`, `datagen.setup`, `datagen.model`, `datagen.loot`, `datagen.recipe`.
- [snippets/java/fabric.identifier.code-snippets](snippets/java/fabric.identifier.code-snippets) — `fid` Identifier helper.
- [snippets/java/fabric.item.registry.code-snippets](snippets/java/fabric.item.registry.code-snippets) — `fabric-item`.
- [snippets/java/fabric.block.registry.code-snippets](snippets/java/fabric.block.registry.code-snippets) — `fabric-block`.
- [snippets/java/fabric.block.with.item.code-snippets](snippets/java/fabric.block.with.item.code-snippets) — `fabric-block-item` (block + BlockItem).
- [snippets/java/fabric.block.tags.code-snippets](snippets/java/fabric.block.tags.code-snippets) — `fabric-tags-block`.
- [snippets/java/fabric.block.loot.tables.code-snippets](snippets/java/fabric.block.loot.tables.code-snippets) — `fabric-loot-block`.
- [snippets/java/fabric.item.model.provider.code-snippets](snippets/java/fabric.item.model.provider.code-snippets) — `fabric-item-model`.
- [snippets/java/fabric.tool.item.code-snippets](snippets/java/fabric.tool.item.code-snippets) — `fabric-tool`.
- [snippets/java/fabric.items.advanced.code-snippets](snippets/java/fabric.items.advanced.code-snippets) — `item.armor`, `item.armor.material`, `item.tool`, `item.tool.material`, `item.food.advanced`, `item.tooltip`, `item.blockitem.tooltip`, `item.fuel`.
- [snippets/java/fabric.entity.type.code-snippets](snippets/java/fabric.entity.type.code-snippets) — `fabric-entity`.
- [snippets/java/fabric.entity.attributes.code-snippets](snippets/java/fabric.entity.attributes.code-snippets) — `fabric-entity-attrs`.
- [snippets/java/fabric.datagen.entrypoint.code-snippets](snippets/java/fabric.datagen.entrypoint.code-snippets) — `fabric-datagen` entrypoint.
- [snippets/java/fabric.networking.code-snippets](snippets/java/fabric.networking.code-snippets) — `packet.id`, `packet.server.handler`, `packet.client.handler`, `packet.send.server`, `packet.send.client`, `packet.send.all`, `packet.send.tracking`.
- [snippets/java/fabric.commands.code-snippets](snippets/java/fabric.commands.code-snippets) — `command.register`, `command.permission`, `command.arg.*`, `command.feedback`, `command.error`, `command.subcommand`.
- [snippets/java/fabric.events.code-snippets](snippets/java/fabric.events.code-snippets) — `event.player.block.break`, `event.attack.entity`, `event.use.item`, `event.use.block`, `event.server.tick`, `event.world.tick`, `event.player.join`, `event.player.death`, `event.entity.load`, `event.loot.modify`, `event.server.starting`, `event.server.started`.
- [snippets/java/fabric.screen.code-snippets](snippets/java/fabric.screen.code-snippets) — `screen.handler`, `screen.handler.register`, `screen.handled`, `screen.register.client`.
- [snippets/java/fabric.mixins.code-snippets](snippets/java/fabric.mixins.code-snippets) — `mixin`, `mixin.inject`, `mixin.inject.return`, `mixin.modifyvariable`, `mixin.modifyarg`, `mixin.redirect`, `mixin.modifyconstant`, `mixin.overwrite`, `mixin.shadow.field`, `mixin.shadow.method`, `mixin.accessor`, `mixin.invoker`, `mixin.client`.
- [snippets/java/fabric.world.generation.code-snippets](snippets/java/fabric.world.generation.code-snippets) — `worldgen.ore`, `worldgen.feature.configured`, `worldgen.feature.placed`, `worldgen.ore.placement`, `worldgen.tree`, `worldgen.structure`.
- [snippets/java/fabric.block.entity.code-snippets](snippets/java/fabric.block.entity.code-snippets) — block entity boilerplate and registration.

### JSON / properties snippets (snippets/json)

- [snippets/json/gradle.code-snippets](snippets/json/gradle.code-snippets) — `gradle.jvm`, `gradle.flags`, `mod.props`, `fabric.props`, `deps.props`, `test.props`, `gradle.full`.
- [snippets/json/gradle.properties.code-snippets](snippets/json/gradle.properties.code-snippets) — `gradle-jvm`, `gradle-opt`, `fabric-maven`, `fabric-mod-meta`, `fabric-core`, `java-gradle`, `deps-common`, `deps-test`, `fabric-gradle-full`.

---

## Gradle Properties Example

Add this to your project's `gradle.properties` to match the versions used by these snippets:

```properties
# Done to increase the memory available to gradle.
org.gradle.jvmargs=-Xmx4G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200

org.gradle.parallel=true
org.gradle.caching=true
org.gradle.configuration-cache=true

# Mod Properties
maven_group=my.vscode
archives_base_name=snippets

mod_id=snippets
mod_version=1.0.0
mod_name=Snippets
mod_description=Minecraft 1.21.11 Fabric with Yarn-Mappings and Split Sources Mod VSCode Snippets.
mod_author=Mosberg
mod_homepage=https://mosberg.github.io/snippets
mod_sources=https://github.com/mosberg/snippets
mod_issues=https://github.com/mosberg/snippets/issues
mod_license=MIT

# Fabric Properties
minecraft_version=1.21.11
loader_version=0.18.4
yarn_mappings=1.21.11+build.4
loom_version=1.14-SNAPSHOT
fabric_api_version=0.141.1+1.21.11
java_version=21
gradle_version=9.2.1

# Dependencies
gson_version=2.13.2
slf4j_version=2.0.17
annotations_version=26.0.2

# Testing
junit_version=6.0.2
```

Tip: If you upgrade Minecraft/Fabric, update these versions consistently along with your `build.gradle` and Loom configuration.

## Patterns and Best Practices

- Centralize registrations (items, blocks, entities) in domain classes and call them from a single `ModRegistries.register()` entry.
- Keep datagen providers small and focused; prefer explicit models and loot tables to reduce runtime JSON mistakes.
- Always register default attributes for living entities to prevent crashes.
- Use tags (`BlockTags`, `ItemTags`) whenever possible; they simplify compatibility.
- Prefer `Identifier.of(MOD_ID, "name")` over string concatenation; it’s safer and clearer.
- Add optional comments to toggle common behaviors (e.g., `.requiresTool()`, `Models.HANDHELD`, luminance).

---

## Compatibility Notes

- Snippets target the modern Fabric API patterns used around MC 1.21.11.
- If you’re on a different version, adapt:
  - Fabric Loader/API, Yarn mappings, Loom, and Gradle versions in the gradle snippets.
  - Some class/method names can shift across mappings or versions.

---

## Troubleshooting

- Snippet not triggering: Ensure the file language mode matches (Java or properties/JSON) and that this extension is installed; for local development ensure files remain under [snippets/java](snippets/java) and [snippets/json](snippets/json).
- Red types/methods: Verify your Fabric/Yarn dependencies line up with the targeted versions in your project.
- Data gen providers: Run datagen with your Loom tasks and ensure the entrypoint is declared in `fabric.mod.json` when needed.

---

## Contributing

If you spot a missing pattern or want an additional variant (e.g., block states for stairs/slabs, recipe advancements, complex model builders), create a new snippet in this folder following the same placeholder and comment conventions.
