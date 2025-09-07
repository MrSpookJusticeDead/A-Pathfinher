# AdvancedPathfinder Module

An **advanced A\* pathfinding solution for Roblox** that:
- Scans both **Terrain** and **Parts** (supports slopes, steps, and trusses).
- Supports **agent settings** (radius, height, slope limit, step height).
- Handles **dynamic blockers** with tags (e.g. moving doors, obstacles).
- Adds **cost multipliers** for terrain materials or tagged objects.
- Has **debug visualization** for nodes and paths.

Perfect for NPCs, mobs, and AI that need reliable navigation in custom maps.

---

## Installation

1. Place `AdvancedPathfinder` as a **ModuleScript** in `ReplicatedStorage/Pathfinding/`.
2. `require()` it in your scripts.

---

##  Usage Example

```lua
local AdvancedPathfinder = require(game.ReplicatedStorage.Pathfinding.AdvancedPathfinder)

-- Create a pathfinder grid covering a region
local pf = AdvancedPathfinder.new(Vector3.new(0, 25, 0), Vector3.new(300, 100, 300), {
    cellSize = 3,
    agentRadius = 2,
    agentHeight = 6,
    maxSlopeDeg = 55,
    stepHeight = 3,
    enableTruss = true,
    debugDraw = true,
})

-- Find a path
local start = Vector3.new(-100, 25, -100)
local goal = Vector3.new(100, 25, 100)
local path = pf:FindPath(start, goal)

-- Draw it
if path then
    pf:VisualizePath(path, 8)
end
```

⚙️ API Reference
AdvancedPathfinder.new(origin: Vector3, size: Vector3, settings: Settings?) -> Pathfinder

Creates a new pathfinder grid in the defined region.

origin: Center of the nav area.

size: Dimensions (X, Y, Z) of the nav area.

settings: Optional settings table (see below).

Pathfinder Methods
FindPath(from: Vector3, to: Vector3) -> {Vector3}?

Finds a path between two world positions.
Returns an array of waypoints (Vector3) or nil if no path found.

VisualizePath(path: {Vector3}, lifetime: number?)

Draws the path with neon parts for debugging.

Rebuild(newOrigin?: Vector3, newSize?: Vector3)

Rebuilds the navigation grid (use if world changes significantly).

GetNearestNodePosition(worldPos: Vector3) -> Vector3?

Returns the closest walkable node position to the given point.

SetSetting(key: string, value: any)

Change a setting dynamically after creation.

Destroy()

Cleans up the pathfinder instance and debug parts.
