# Storage Check Predicate Concept

The `minecraft:storage_check` predicate can be used to compare two different storage NBT values.
Currently we would use something like the following to check for equality of two NBT values:
```mcfunction
data modify storage example:storage temporary set from storage example:storage valueA
execute store success score copyResult Temporary run data modify storage example:storage temporary set from storage example:storage valueB
execute if score copyResult Temporary matches 0 run say They were the same...
```
To check if an item is in a collection, we currently have two options:
- Loop over the collection and check for equality using the above method. This involves a lot of copying or hardcoded indices.
- Try to append a string to the `Tags` tag on an entity and compare the length. This only works for strings and involves entity NBT.

Both are very tedious to do and limited in their use. The `minecraft:storage_check` predicate is supposed to get rid of all that.

## Format

The format is not too complex, it only takes a `check` value, which is a storage comparer.

```json
{
    "condition": "minecraft:storage_check",
    "check": {
        "type": "...",
        "other_properties": "..."
    }
}
```

## Storage Comparers

### `minecraft:equals`

Checks if two NBT values are equal.

**`left`:** A storage provider. The left side to check for.\
**`right`:** A storage provider. The right side to check for.

Example:
```json
{
    "function": "minecraft:equals",
    "left": {
        "storage": "example:storage",
        "path": "path.to.item"
    },
    "right": {
        "storage": "example:storage",
        "path": "path.to.other.item"
    }
}
```

### `minecraft:greater_than`

Checks if a numerical NBT value is greater than the other.
If either `left` or `right` is not numerical, it returns `false`.

**`left`:** A storage provider. The left side to check for.\
**`right`:** A storage provider. The right side to check for.

Example:
```json
{
    "function": "minecraft:greater_than",
    "left": {
        "storage": "example:storage",
        "path": "path.to.item"
    },
    "right": {
        "storage": "example:storage",
        "path": "path.to.other.item"
    }
}
```

### `minecraft:smaller_than`

Checks if a numerical NBT value is smaller than the other.
If either `left` or `right` is not numerical, it returns `false`.

**`left`:** A storage provider. The left side to check for.\
**`right`:** A storage provider. The right side to check for.

Example:
```json
{
    "function": "minecraft:smaller_than",
    "left": {
        "storage": "example:storage",
        "path": "path.to.item"
    },
    "right": {
        "storage": "example:storage",
        "path": "path.to.other.item"
    }
}
```

## Storage Providers

A storage provider is used to target storage NBT with a specific path.

**`storage`:** A resource location specifying the storage ID to get the NBT from.\
**`path`:** An NBT path pointing to the value.

Example:
```json
{
    "storage": "example:storage",
    "path": "path.to.item"
}
```
