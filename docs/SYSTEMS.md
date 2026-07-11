# Gameplay Systems
## Combat system
It regulates the interactions during the fights.
### Responsibility
- Attacks execution
- Calculate damage
- Apply defense bonuses
- Notify match system about defeated characters
### Works with
- Character
- Equipment
- Arena
### Does not
- Renders graphic
- Save data
- Read user input
### Owns
- Character status
- Attacks cost
- Life points calculations

## Movement System
It regulates the character moving inside the arena
### Responsibility
- Manage characters position inside the arena
### Works with
- Character
- Arena
- Obstacle
### Does not
### Owns
- Collision detection
- Interaction with obstacles
- Movement cost calculation

## Character Management System
Build and modify character appearance and equipment.
### Responsibility
- Choose players
- Add chosen equipment to players
- Add chosen ability to equipment
### Works with
- Character
- Equipment
- Ability
### Does not
- Compute damages with equipment and abilities
- Render equipment
- Render abilities
### Owns
- Equipment inventory
- Ability Inventory
- Match abilities with equipment

## Match System
Manage game progress
### Responsibility
- Put players into the arena
- Start the fight
- Decide when the fight finishes
- Establish the winner
### Works with
- Character
### Does not
- Manage attack/defense
- Render arena obstacles
### Owns
- Fight start time
- Chosen arena

## AI system
Takes AI opponents decision
### Resposability
- Analizes current situation
- Decide which is the best decision to keep up with the player according to the difficulty
- AI players surviving
### Works with
- Character
- Equipment
- Ability
- Arena
### Does not
### Owns
- AI characters
- Decisions tree
- Autonomous combat algorithm

# Application
## Navigation system
## Input system
## Settings system

# Support
## Persistence system
Manage permanent information store and retrieve
### Responsibility
- Save characters configuration
- Store equipments
- Store abilities
- Store maps
### Works with
- Character
- Equipment
- Ability
- Arena
### Does not
- Renders Players
- Renders Arena
- Match equipment with their abilities
### Owns
- Available characters
- Available equipments
- Available abilities
- Available maps
- Customized characters

## Logging system

## Configuration system

# Infrastructure
## Filesystem system

## Serialization system

## Platform system

## Audio system

## Networking system?
