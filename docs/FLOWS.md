This document contains the interaction among the systems when executing simple end to end actions.

# Flows
## Gameplay
### Start game
- Navigation (move among starting environments) -> Character Management (choose players, equipment and abilities) -> Match (place characters) -> Arena (register characters position)

### Player moves
Platform (receive physical input) -> Input (translate input to game coordinates) -> Command (translate the input into the appropriate command according to the context) -> Movement (check obstacles) -> Character (new position) -> Arena (read character position)

#### Flow chart
- Keyboard stroke taken by Platform, uniformed abstracting the platform and sent to Input.
- Input translate the received data. It modifies the physical abstracted input into game known input (e.g. physical left arrow on the keyboard or on the joypad are translated into Left arrow input)
- Command creates the MoveCommand starting from the Input because it knows that the game is in fight mode.
- Command is received by Movement which checks if the MoveCommand can be executed. If so, it propagates it otherwise it doesn't move.
- If the movement can be done, the Character position is updated.
- Rendering reads the position, either new or old, and show the Character on the screen. 

### Player attacks enemy
Platform (receive physical input) -> Input (translate input to game coordinates) -> Command (translate the input into the appropriate command according to the context) -> Combat (calculate damage) -> Character, Arena, Equipment (assing damage) -> Match (verify match end conditions)

#### Flow chart
- Keyboard stroke taken by Platform, uniformed abstracting the platform and sent to Input.
- Input translate the received data. It modifies the physical abstracted input into game known input of attack
- Command creates the AttackCommand starting from the Input because it knows that the game is in fight mode
- Command is received by Combat which calculates how much damage is dealt
- Arena, knowing the position of obstacles and Characters, assess where the damage is directed and what it reaches
- Combat get back a HitResult from Arena with the target so combat can calculate damage, taking possibly into consideration Character defence and Equipment.
- Combat updates Characters status 
- MatchEngine observes the Characters' current status
- MatchRules evaluates end game conditions
- MatchEngine updates MatchState

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