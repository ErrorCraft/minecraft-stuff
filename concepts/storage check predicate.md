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
    "function": "minecraft:storage_check",
    "check": {
		"type": "...",
		...
	}
}
```
