```
item
    block
        <pos: block_pos>
            clear
                [item: item_predicate]
                    [maxCount: integer]
            copy
                <slot: item_slot>
                    block
                        <source: block_pos>
                            <sourceSlot: item_slot>
                                [modifier: resource_location]
                    entity
                        <source: entity>
                            <sourceSlot: item_slot>
                                [modifier: resource_location]
            give
                <item: item_stack>
                    [count: integer]
            modify
                <slot: item_slot>
                    <modifier: resource_location>
            replace
                <slot: item_slot>
                    <item: item_stack>
                        [count: integer]
    entity
        <targets: entity>
            clear
                [item: item_predicate]
                    [maxCount: integer]
            copy
                <slot: item_slot>
                    block
                        <source: block_pos>
                            <sourceSlot: item_slot>
                                [modifier: resource_location]
                    entity
                        <source: entity>
                            <sourceSlot: item_slot>
                                [modifier: resource_location]
            give
                <item: item_stack>
                    [count: integer]
            modify
                <slot: item_slot>
                    <modifier: resource_location>
            replace
                <slot: item_slot>
                    <item: item_stack>
                        [count: integer]
```
```
item block ~ ~ ~ clear
item block ~ ~ ~ clear #minecraft:stairs
item block ~ ~ ~ clear #minecraft:stairs 15
item block ~ ~ ~ copy container.0 block
item block ~ ~ ~ copy container.0 block ~ ~ ~ container.0
item block ~ ~ ~ copy container.0 block ~ ~ ~ container.0 example:modifier
item block ~ ~ ~ copy container.0 entity @s inventory.0
item block ~ ~ ~ copy container.0 entity @s inventory.0 example:modifier
item block ~ ~ ~ give minecraft:cobblestone
item block ~ ~ ~ give minecraft:cobblestone 15
item block ~ ~ ~ modify container.0 example:modifier
item block ~ ~ ~ replace container.0 minecraft:cobblestone
item block ~ ~ ~ replace container.0 minecraft:cobblestone 15
item entity @s clear
item entity @s clear #minecraft:stairs
item entity @s clear #minecraft:stairs 15
item entity @s copy inventory.0 block
item entity @s copy inventory.0 block ~ ~ ~ container.0
item entity @s copy inventory.0 block ~ ~ ~ container.0 example:modifier
item entity @s copy inventory.0 entity @s inventory.0
item entity @s copy inventory.0 entity @s inventory.0 example:modifier
item entity @s give minecraft:cobblestone
item entity @s give minecraft:cobblestone 15
item entity @s modify inventory.0 example:modifier
item entity @s replace inventory.0 minecraft:cobblestone
item entity @s replace inventory.0 minecraft:cobblestone 15
```
