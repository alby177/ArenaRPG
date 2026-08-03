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
- Combat resolution
- Combat rules
- Damage calculations

## Movement System
It regulates the character moving inside the arena
### Responsibility
- Manage characters position inside the arena
- Update characters position
### Works with
- Character
- Arena
- Obstacle
### Does not
### Owns
- Collision rules
- Can a Character move from A to B?
- Movement cost

## Character Management System
Build and modify character appearance and equipment.
### Responsibility
- Create Character
- Customize Character
### Works with
- Character
- Equipment
- Ability
### Does not
- Compute damages with equipment and abilities
- Render equipment
- Render abilities
### Owns
- Character customization rules
- Equipment assignment rules
- Match abilities with equipment

## Match System
Manage game progress
### Responsibility
- Create march context
- Start the fight
- Decide when the fight finishes
- Establish the winner
- Spawn Characters
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
### Responsibility
- Analizes current situation
- Decide which is the best decision to keep up with the player according to the difficulty
- Evaluate survival strategies
### Works with
- Character
- Equipment
- Ability
- Arena
### Does not
### Owns
- Decision making process
- Difficulty rules
- Autonomous combat algorithm

# Application
## Navigation system
Manage application state transitions
### Responsibility
- Provide the available options to move through the menus
- Provide the available options for each menu
- Provide the available statuses that can follow each state
### Works with
### Does not
- Manage characters equipment
### Owns
- Menus content
- Sequence to access the various menus

## Input system
Catch input from the user and provide it to the other systems
### Responsibility
- Catch user input from keyboard or joypad
- Provide the translated input to the other systems
- Unification of the inputs coming from different devices
### Works with
- Navigation system
- Movement system
### Does not
- Move the character
- Decide if the character can move
### Owns
- Input detection loop
- Translation from hardware data to software data

## Settings system
Show the available settings and the current settings status
### Responsibility
- List all the available settings
- Show all the current selected settings
- Provide mechanism to change the selected settings
### Works with
- Persistence system
### Does not
### Owns
- Available settings list

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
- Filesystem system
### Does not
- Renders Players
- Renders Arena
- Match equipment with their abilities
### Owns
- Serialization format
- Storage mechanism

## Logging system
Print out what is happening during the application execution
### Responsibility
- Read logging configuration
- Write diagnostic information
### Works with
- Filesystem system
### Does not
### Owns
- Log configuration data
- Output file/terminal/connection

# Infrastructure
## Game loop system
Starts the game and Keep it running
### Responsibility
- Keep on running until the game execution is interrupted
- Update systems
### Works with
- Rendering system
- Input system
- Navigation system
### Does not
- Render UI element
- Transition among menus
- Catch inputs
### Owns
- Game loop

## Rendering system
Create each UI element is shown to the user
### Responsibility
- Create UI element which needs to be shown
- Output the UI element
### Works with
- Presentation Model
### Does not
### Owns
- Rendering engine
- UI output

## Filesystem system
Allow to access the files stored inside the PC
### Responsibility
- Provide abstractions to access the stored data
- Retrieve and store phisically the data on the hard drive
### Works with
- Persistence system
- Logging system
### Does not
- Know what is stored on the hard drive
### Owns
- File system connection

## Serialization system
Knows how to compress and decompress data
### Responsibility
- Translate data into specific format to store it on disk
### Works with
- Persistence system
### Does not
- Store data on disk
### Owns
- Serialization algorithm

## Platform system
Abstract the platform on which the application is running
### Responsibility
- Use the API specific to the platform
- Provide an abstraction from the platform
### Works with
- Filesystem system
- Input system
### Does not
- Store the data into the disk
- Catch and translate inputs
### Owns
- Platform type
- Platform API



# Future
## Audio system
## Networking system
