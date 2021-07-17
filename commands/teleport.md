```
teleport
    entity
        <targets: entity>
            to
                <destination: entity>
            <location: vec3>
                facing
                    entity
                        <facingEntity: entity>
                            [facingAnchor: entity_anchor]
                    <facingLocation: vec3>
                [rotation: rotation]
    to
        <destination: entity>
    <location: vec3>
```
|New|Original|
|---|---|
|`teleport entity @e to @s`|`teleport @e @s`|
|`teleport entity @e ~ ~ ~`|`teleport @e ~ ~ ~`|
|`teleport entity @e ~ ~ ~ facing entity @s`|`teleport @e ~ ~ ~ facing entity @s`|
|`teleport entity @e ~ ~ ~ facing entity @s eyes`|`teleport @e ~ ~ ~ facing entity @s eyes`|
|`teleport entity @e ~ ~ ~ facing ~ ~ ~`|`teleport @e ~ ~ ~ facing ~ ~ ~`|
|`teleport entity @e ~ ~ ~ ~ ~`|`teleport @e ~ ~ ~ ~ ~`|
|`teleport to @s`|`teleport @s`|
|`teleport ~ ~ ~`|`teleport ~ ~ ~`|
