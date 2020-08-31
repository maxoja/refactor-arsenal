The use of enum in python is not primitive as it came later for us to use as sub classes of Enum class. The use cases of python's enum are mostly straight forward but there're some tricky tricks worth knowing

1. [What to import](#what-to-import)
2. [Simple enum](#simple-enum)
3. [Use enum as value](#use-enum-as-value)
4. [Iterating over enum](#iterating-over-enum)
5. [Get item by order](#get-item-by-order)

### What to import
Enum classes inherit from enum.Enum and if you want it to be operational as integer you can use enum.IntEnum.
Also, enum.auto() is for defining enum name without value. These 3 should be sufficient for most use cases.
```
from enum import Enum, IntEnum, auto
```

### Simple Enum
```
class Direction(Enum):
    LEFT = auto()
    RIGHT = auto()
    UP = auto()
    DOWN = auto()
```

### Use Enum as value
It is possible to allow primitive operations (string concat, numurical op) to be performed on an enum item. We can associate a type into an Enum subclass as below.
```
class Orientation(IntEnum):
    UP = 0
    RIGHT = 90
    DOWN = 180
    LEFT = 270
    
class Endpoint(str, Enum):
    DEV = 'x.x.x.x:xxxx'
    PROD = 'y.y.y.y:yyyy'
```

### Iterating over enum
