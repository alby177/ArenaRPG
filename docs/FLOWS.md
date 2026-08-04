This document contains the interaction among the systems when executing simple end to end actions.

# Flows
## Gameplay
### Start game
- Navigation (move among starting environments) -> Character Management (choose players, equipment and abilities) -> Match (place characters) -> Arena (register characters position)

### Player moves
Platform (receive physical input) -> Input (translate input to game coordinates) -> Movement (check obstacles) -> Character (new position) -> Arena (read character position)

### Player attacks enemy
Platform (receive physical input) -> Input (translate input to game coordinates) -> Combat (calculate damage) -> Character, Arena, Equipment (assing damage) -> Match (verify match end conditions)

### AI move
AI (take decision based on current state) -> Arena (check old position) -> Character (check state) -> Movement (check obstacles) -> Character (new position) -> Arena (register position) -> Match (verify end match conditions)

## Application
### Player equips weapon
Navigation (move among customization environments) -> Character Management (show available options) -> Character (register equipment chosen)

### Player chooses ability
Navigation (move among customization environments) -> Character Management (show available options) -> Character (register ability chosen) -> Ability (register ability)

### Save Character
Character Management (chosen options) -> Persistence (take options to store) -> Serialization (create storable objects) -> Filesystem (store object in the disk)

### Modify game setting
Navigation (move to settings environment) -> Settings (show available settings) -> Persistence (take options to store) -> Serialization (create storable objects) -> Filesystem (store object in the disk)

### Show images
Game Loop (keep game alive) -> Rendering (print elements on the screen) -> Arena (provide the elements to print) -> Character (provide the players to print)