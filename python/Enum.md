The use of enum in python came later as a class we can inherit from. The uses are mostly straight forward but there're some tricky tricks worth knowing as well.

1. [What to import](#import)
2. [Simple enum](#simple-use)
3. [Use enum as value](#enum-as-value)
4. [Iterating over enum](#iteration)
5. [Converting between enum value and index](#conversion)

### What to import <span id="import"><span>
Enum classes inherit from enum.Enum and if you want it to be operational as integer you can use enum.IntEnum.
Also, enum.auto() is for defining enum name without value. These 3 should be sufficient for most use cases.
```
from enum import Enum, IntEnum, auto
```

### Simple Enum <span id="simple-use"><span>
```
class Direction(Enum):
    LEFT = auto()
    RIGHT = auto()
    UP = auto()
    DOWN = auto()
```

### Use Enum as value <span id="enum-as-value"><span>
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

### Iterating over enum <span id="iteration"><span>
```
class MockEnum(Enum):
    A = auto()
    B = auto()
    C = auto()
    
for e in MockEnum:
    print(e)
```

### Converting between enum value and index <span id="conversion"><span>
Some modification can be made for when an enum needs to be presented in multiple forms often. The content in this snippet is functional but not optimized.
```
class MockEnum(str, Enum):
    A = 'Apple'
    B = 'Boy'
    C = 'Cat'
    
    @staticmethod
    def from_index(i):
        all_type = [t for t in Type]
        return all_type[i]

    @staticmethod
    def index_of(t):
        all_types = [t for t in Type]
        return all_types.index(t)

    def i(self):
        all_types = [t for t in Type]
        return all_types.index(self.value)
```
