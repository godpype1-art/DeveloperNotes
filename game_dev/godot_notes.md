# Godot Notes

## File structuring

There is a conventional GDScript ordering that most teams settle on:

- Enums first — types/shapes of data, needed before anything else references them
- Signals — the building's "public API" for communication, worth seeing early
- Constants — fixed values, don't change, good to see before variables
- Exports — inspector-visible values, essentially the building's "configuration"
- Onready — node references, depend on the scene being ready
- Variables — runtime state, changes during gameplay

---

### Visual Example

```gdscript
class_name Building
extends Node2D

# ============ ENUMS ============ #
enum BuildingState { GHOST, ACTIVE, DELETED }

# ============ SIGNALS ============ #
signal state_changed(new_state: BuildingState)

# ============ CONSTANTS ============ #
const SOME_CONSTANT: int = 0

# ============ EXPORTS ============ #
@export var hp: int = 100
@export var max_hp: int = 100
@export var cost: int = 50

# ============ ONREADY ============ #
@onready var sprite: Sprite2D = $Sprite2D

# ============ VARIABLES ============ #
var current_state: BuildingState = BuildingState.GHOST
```