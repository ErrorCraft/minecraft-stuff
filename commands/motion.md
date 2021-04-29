```
motion
    <target: entity>
        get
            x
                [scale: double]
            y
                [scale: double]
            z
                [scale: double]
        set
            motion
                <xMotion: double>
                    <yMotion: double>
                        <zMotion: double>
            x
                value
                    <motion: double>
            y
                value
                    <motion: double>
            z
                value
                    <motion: double>
```
```
motion @s get x
motion @s get x 1000
motion @s get y
motion @s get y 1000
motion @s get z
motion @s get z 1000
motion @s set motion 1.5 1.5 1.5
motion @s set x value 1.5
motion @s set y value 1.5
motion @s set z value 1.5
```
