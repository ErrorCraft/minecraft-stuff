# Reworked text components
This is a text component rework proof-of-concept thing.
<br></br>


## Structure
The reworked structure would make use of CODEC and a registry for the content types.
This makes it representable in NBT directly rather than requiring a stringified form.
Primitive JSON types (strings, numbers and booleans) could also still be interpreted as literals, just like the current implementation.

### Arguments
**`content`:** The text component content. Based on the recent rework of the text component system.\
**`style`:** The style for the text component. This is already used for chat types.\
**`siblings`:** An array for extra text components. It's currently named `extra`, but I like this name more as it's more descriptive.\
**`events`:** Events related to the text component.

### Example
```json
{
    "content": {
        "type": "minecraft:literal",
        "literal": "Some text"
    },
    "style": {
        "color": "red",
        "bold": true
    },
    "siblings": [
        {
            "content": {
                "type": "minecraft:literal",
                "literal": "Other text components"
            }
        }
    ],
    "events": {
        "clickEvent": {
            "action": "open_url",
            "value": "https://minecraft.net"
        }
    }
}
```
<br></br>


## Text content
The actual text of the text component. This replaces the check for a key with a resource location.


### `minecraft:literal`
A literal piece of text.

#### Arguments
**`literal`:** A string representing the literal.

#### Example
```json
{
    "component": "minecraft:literal",
    "literal": "Some text"
}
```


### `minecraft:translation`
A translated piece of text using a key.

#### Arguments
**`key`:** A string representing the key of the translation.

#### Example
```json
{
    "component": "minecraft:translation",
    "key": "my.translation.key"
}
```


### `minecraft:selector`
A selector for displaying entity names.

#### Arguments
**`selector`:** A selector to get the entity names. (This could be reworked as well to remove it being a string, but that's something for another time)\
**`separator`:** An optional text component for the separator between names.

#### Example
```json
{
    "component": "minecraft:selector",
    "selector": "@a",
    "separator": {
        "content": {
            "type": "minecraft:literal",
            "literal": " and "
        }
    }
}
```


### `minecraft:score`
A score to display.

#### Arguments
**`objective`:** The name of the scoreboard.\
**`name`:** A selector to get the name of the score holder whose score should be displayed or `*` for the reader's own score.\
Alternatively this could use a score number provider, though this does not include an option for `*`.

#### Example
```json
{
    "component": "minecraft:score",
    "objective": "MyScoreboard",
    "name": "@s",
}
```


### `minecraft:keybind`
A keybind to display.

#### Arguments
**`keybind`:** A keybind identifier.

#### Example
```json
{
    "component": "minecraft:keybind",
    "keybind": "key.inventory"
}
```


### `minecraft:nbt` (hiss)
NBT to display.

#### Arguments
**`nbt`:** An nbt provider. See below for more information.\
**`interpreted`:** An optiona boolean to indicate if the NBT should be interpreted as a text component.\
**`separator`:** An optional text component for the separator between NBT values.

#### Example
```json
{
    "component": "minecraft:nbt",
    "nbt": {
        "type": "minecraft:storage",
        "storage": "namespace:path/to/storage",
        "path": "path.to.nbt"
    },
    "interpret": true
}
```
<br></br>


## NBT providers
These exist to replace yet another key check.
To be honest, I would prefer to just outright remove this (except for storage) and use another system instead of changing it, but this is a rewrite of the existing thing, so there's nothing new in here.

### `minecraft:block`
NBT of an block.

#### Arguments
**`position`:** A string for the position of the block.\
**`path`:** The NBT path.

#### Example
```json
{
    "type": "minecraft:block",
    "position": "~ ~ ~",
    "path": "path.to.nbt"
}
```


### `minecraft:entity`
NBT of an entity.

#### Arguments
**`position`:** A selector for the entity to use.\
**`path`:** The NBT path.

#### Example
```json
{
    "type": "minecraft:entity",
    "entity": "@s",
    "path": "path.to.nbt"
}
```


### `minecraft:storage`
NBT of a storage.

#### Arguments
**`storage`:** A resource location for the storage.\
**`path`:** The NBT path.

#### Example
```json
{
    "type": "minecraft:storage",
    "storage": "namespace:path/to/storage",
    "path": "path.to.nbt"
}
```
<br></br>


## Events
It's basically the same as the current implementation.
However, it *could* use a registry too for the types of click events and hover events, so `minecraft:open_url` would be used instead of `open_url`. (To be honest, this system could also be fully reworked to make multiple events possible at once.)

### Arguments
**`insertion`:** Insertion of text when shift clicked. (This probably doesn't belong here but it's related to a click event.)\
**`clickEvent`:** A click event.\
**`hoverEvent`:** A hover event.\
All of these are optional.

### Example
```json
{
    "insertion": "Inserted text",
    "clickEvent": {
        "action": "open_url",
        "value": "https://minecraft.net"
    },
    "hoverEvent": {
        "action": "show_text",
        "contents": {
            "content": {
                "type": "minecraft:literal",
                "literal": "Hover event!"
            },
            "style": {
                "color": "green",
                "italic": true
            }
        }
    }
}
```
