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
**`hunger`:** A number provider. Specifies the health to set.
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

Sets the hunger of a player. (Figure out a way to set saturation, maybe something like a `minecraft:set_saturation` or `minecraft:set_hunger_saturation` function?)
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

### `minecraft:set_name`

Sets the name of an entity. (Figure out a way to reset the name, maybe a `minecraft:reset_name` function?)
**`name`:** A text component. Advanced components are resolved using the entity that is being modified.
**`visible`:** An optional boolean. If `true`, the entity's name will be visible, otherwise this is unchanged.

Example:
```json
{
    "function": "minecraft:set_name",
    "name": {
        "text": "Hello World",
        "color": "red",
        "bold": true
    }
    "visible": true
}
```
