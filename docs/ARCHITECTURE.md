# ARCHITECTURE
This document is going to contain how the code will be structured.

## Project structure
The project is divided in 2 entities, Native (C++) and Presentation (CLI/Avalonia).

The Native part is written in C++, is cross platform and uses the C++23 standard to learn about all the new available features and try them on the field.

The frontend can be chosen between CLI (super light) and Avalonia (greater visual experience).

Automated tests are implemented using Catch2 for the C++ part and XUnit for the C#.

The project can be build with the CMake build system.

## Project map
The source code is stored inside the src folder following this structure:

| Folder Name         | Module                | Description                                                     |
|----------------     | --------------------- | ----------------------------------------------------------------|
| src/core            | Core Domain           | Contains all the domain code                                    |
| src/gameplay        | Gameplay              | Contains the game logic                                         |
| src/app             | Application           | Contains the application logic (available menus, settings, ...) |
| src/infrastructure  | Infrastructure        | Contains all the code which supports the development abstracting the access to the underlying platform |
| src/engine          | Engine                | Contains the code updating allowing the update of each module   |
| src/presentation    | Presentation          | Contains the presentation code (not included in CMake)          |

## Modules dependencies
| Module         | Relies on                                |
| -------------- | ---------------------------------------- |
| Core Domain    | Nothing                                  |
| Gameplay       | Core Domain, Application                 |    
| Application    | Core Domain, Infrastructure              |
| Infrastructure | Nothing                                  |
| Engine         | Core Domain, Infrastructure              |      
| Presentation   | Engine, Application                      |

## Design
The engine chosen architecture is classic OOP, for now ECS is out of scope. Each entity contains every information needed to work. 

ECS is going to be implemented for didactical purposes in the future. The ENGINE_DESIGN.md file documents how it will be created. 