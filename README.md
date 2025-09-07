# A-Pathfinher
A cool pathfinding module i did


---

## 📢 Reddit Post Example

```markdown
**Title:** 🔥 [Release] AdvancedPathfinder – A\* Pathfinding Module for Roblox (Terrain, Slopes, Trusses, Dynamic Obstacles!)

---

Hey everyone 👋  

I’ve built a custom **A\*** pathfinding module for Roblox that’s way more flexible than the built-in `PathfindingService`.  

✅ Handles **Terrain + Parts**  
✅ Works on **slopes & steps**  
✅ Can **climb Trusses** (adds vertical links)  
✅ Respects **agent size, slope, step height**  
✅ Supports **dynamic blockers** with CollectionService tags  
✅ Allows **material/tag-based costs** (mud is slower, roads are faster, etc.)  
✅ Has a **debug draw** mode so you can see the grid and paths  

---

### Example Usage:

```lua
local Pathfinder = require(game.ReplicatedStorage.Pathfinding.AdvancedPathfinder)

local pf = Pathfinder.new(Vector3.new(0,20,0), Vector3.new(200,80,200), {
    cellSize = 3,
    agentRadius = 2,
    agentHeight = 6,
    maxSlopeDeg = 50,
    stepHeight = 3,
    debugDraw = true,
})

local start = Vector3.new(-50,20,-50)
local goal  = Vector3.new(50,20,50)

local path = pf:FindPath(start, goal)
if path then
    pf:VisualizePath(path, 8)
end

