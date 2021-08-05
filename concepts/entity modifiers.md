# Entity Modifiers Concept

## Format

Entity modifiers can be found under `data/namespace/modifiers/entity`. The entity used for context (for example when resolving text components) will always be the entity that is being modified.

```json
{
    "function": "resource_location",
    "other_properties": "..."
}
```

## Modifiers

### `minecraft:set_health`

Sets the health of an entity.

**`health`:** A number provider. Specifies the health to set.

**`add`:** An optional boolean. If `true`, change will be relative to the current health.

Example:

```json
{
    "function": "minecraft:set_health",
    "health": 5.0,
    "add": true
}
```

### `minecraft:set_hunger`

Sets the hunger of a player.

**`hunger`:** A number provider. Specifies the hunger to set.

**`add`:** An optional boolean. If `true`, change will be relative to the current hunger.

Example:

```json
{
    "function": "minecraft:set_hunger",
    "hunger": -2,
    "add": true
}
```

### `minecraft:set_display_name`

Sets the display name of an entity. (Figure out a way to reset the name, maybe a `minecraft:reset_display_name` function?)

**`name`:** A text component. Advanced components are resolved using the entity that is being modified.

**`visible`:** An optional boolean. If `true`, the entity's name will be visible, otherwise this is unchanged.

Example:

```json
{
    "function": "minecraft:set_display_name",
    "name": {
        "text": "Hello World",
        "color": "red",
        "bold": true
    },
    "visible": true
}
```

### `minecraft:set_air_time`

Sets the air time of an entity.

**`time`:** A number provider. Specifies the air time to set.

**`add`:** An optional boolean. If `true`, change will be relative to the current air time.

Example:

```json
{
    "function": "minecraft:set_air_time`",
    "time": 100,
    "add": true
}
```

### `minecraft:set_fire_time`

Sets the fire time of an entity.

**`time`:** A number provider. Specifies the fire time to set.

**`add`:** An optional boolean. If `true`, change will be relative to the current fire time.

Example:

```json
{
    "function": "minecraft:set_fire_time",
    "time": 40,
    "add": false
}
```

### `minecraft:set_invulnerable`

Sets the invulnerability of an entity.

**`invulnerable`:** A boolean. If `true`, the entity will be invulnerable and won't take any damage.

Example:

```json
{
    "function": "minecraft:set_invulnerable",
    "invulnerable": true
}
```

### `minecraft:set_absorption`

Sets the absorption of an entity.

**`absorption`:** A number provider. Specifies the absorption to set.

**`add`:** An optional boolean. If `true`, change will be relative to the current absorption.

Example:

```json
{
    "function": "minecraft:set_absorption",
    "absorption": 2.0,
	"add": true
}
```

### `minecraft:set_saturation`

Sets the saturation of a player.

**`saturation`:** A number provider. Specifies the saturation to set.

**`add`:** An optional boolean. If `true`, change will be relative to the current saturation.

Example:

```json
{
    "function": "minecraft:set_hunger",
    "saturation": 1.5,
    "add": true
}
```

### `minecraft:set_silent`

Sets whether the entity is silent or not.

**`silent`:** A boolean. If `true`, the entity won't make any sounds.

Example:

```json
{
    "function": "minecraft:set_silent",
    "silent": true
}
```
