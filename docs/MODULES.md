# MODULES
This document groups together the systems to understand how to organize the code.

## List
### Core Domain
Contains:
- Character
- Equipment
- Ability
- Arena
- Obstacle
- Match rules

### Gameplay
Contains:
- Combat
- Movement
- Character Management

### Application
Contains:
- Navigation
- Settings
- Persistence
- Command

### Infrastructure
Contains:
- File System
- Serialization
- Logger
- Platform

### Engine
Contains: 
- Input
- AI Engine
- Match Engine
- Game loop
- Rendering API

### Presentation
Contains:
- CLI
- Avalonia

## Dependecies
| System      | Dependencies                    | Runtime interactions|
| ----------- | ----------------------------- |-----------|
| Core domain | Nothing | Nothing |
| Gameplay    | Core Domain <br> Application (i.e. Persistence) | Engine (i.e. Input) |
| Application | Core Domain <br> Infrastructure (i.e. Serialization, File System) | Engine (i.e. Input) |
| Infrastructure | Nothing | Application (i.e. Settings) |
| Engine | Core Domain (i.e. Match Rules), Infrastructure (i.e. Platform) | Application (i.e. Settings) |
| Presentation | Engine (i.e. Rendering API) | Application (i.e. Settings) |

## Interactions
In this section are presented the interfaces/contracts that allow the systems to communicate

### Gameplay
| System | Interacts With | Through |
| ------ | -------------- | ------- |
| Combat | Character | CharacterStats |
| Combat | Equipment | EquipmentStats |
| Combat | Ability | AbilityStats |
| Combat | Command | ActionCommand |
| Combat | Settings | CombatSettings |
| Movement | Character | CharacterStats |
| Movement | Character | EquipmentStats |
| Movement | Character | AbilityStats |
| Movement | Arena | ArenaSpecs |
| Movement | Obstacle | ObstacleSpecs |
| Movement | Command | MoveCommand |
| Character Management | Character | CharacterStats |
| Character Management | Equipment | EquipmentStats |
| Character Management | Ability | AbilityStats |
| Character Management | Input | NavigationCommand |
| Character Management | Persistence | PlayerSpecs |

### Application
| System | Interacts With | Through |
| ------ | -------------- | ------- |
| Navigation | Command | NavigationCommand |
| Settings | Command | NavigationCommand |
| Settings | Persistence | ImageSettings |
| Settings | Persistence | MatchSetttings |
| Settings | Persistence | CombatSettings |
| Settings | Persistence | DiagnosticSettings |
| Persistence | Serialization | CharacterStats |
| Persistence | Serialization | EquipmentStats |
| Persistence | Serialization | AbilityStats |
| Persistence | Serialization | ArenaSpecs |
| Persistence | Serialization | ObstacleSpecs |
| Command | Input | RawInput |
| Command | Navigation | ContextDetails |

### Infrastructure
| System | Interacts With | Through |
| ------ | -------------- | ------- |
| Logger | Settings | DiagnosticSettings |

### Engine
| System | Interacts With | Through |
| ------ | -------------- | ------- |
| Input | Platform | KeyPressed |
| AI Engine | Settings | AISettings |
| AI Engine | Combat | GameState |
| AI Engine | Combat | AvailableActions |
| Match Engine | Combat | MatchState |
| Match Engine | Match Rules | MatchRule |
| Match engine | Settings | MatchSetttings |
| Rendering | Settings | ImageSettings |

#### Game Loop
Game loop must be represented differently because it's aim is to coordinate game execution, so no contracts among it and the other systems but it allows to run the engine and the sub systems through the update.
```
Game Loop -> Input
          |
          -> Render       --> AI
          |               |
          -> Update ------|-> Combat
                          |
                          --> Movement
```

### Presentation
| System | Interacts With | Through |
| ------ | -------------- | ------- |
| Avalonia <br> CLI | Rendering API | RenderFrame |
| Avalonia <br> CLI | Settings | UISettings |