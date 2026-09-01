The Engine provides the runtime infrastructure required to execute the game independently from the Presentation layer.  

The engine follows the Entity Component System reprensentation model.

# Design
## ECS Model
The Engine represents runtime game objects as Entities identified by an ID.

Entities do not contain game logic.

Components contain the data required by the Engine.

Systems operate on entities by accessing the components they require.

In general, the players of this kind of model are:
- Entity → identity
- Component → data/state
- System → behavior/processing

## Entities
| Domain Concept | Is Engine Entity | Reason                                                                             |
| -------------- | ---------------- | ---------------------------------------------------------------------------------- |
| Character      | Yes              | It is characterized by some phyical entities that needs to be used to run the game |
| Equipment      | No               | Attached to the entity for it to use                                               |
| Ability        | No               | Attached to the entity for it to use                                               |
| Arena          | No               | It just hosts entities                                                             |
| Obstacle       | Yes              | It is characterized by some phyical entities that needs to be used to run the game |
| Match rules    | No               | Just a set of rules which are used by the Match Engine                             |

## Components
- Position_Component (Holds X and Y coordinates)
- Health_Component (Holds life points)
- Stamina_Component (Holds stamina quantity and regain ratio)
- Movement_Component (Holds movement speed)
- Image_Component (Holds the data/sprite to be shown on the screen)
- Equipment_Component (Holds base damage, base range and base area of damage)
- Ability_Component (Holds damage bonus, range bonus, area of damage bonus and resistance bonus)
- AI_Driven_Component (Holds wether or not an entity as driven BY AI)

## Systems
| Domain/System        | Is ECS System | Reason                                                  |
| -------------------- | -----------   | ------------------------------------------------------- |
| Movement             | Yes           | Computes the movement of the entities                   |
| Combat               | Yes           | Computes damages during the match                       |
| AI                   | Yes           | Take decisions and apply them on the AI driven entities |
| Match                | Yes           | Apply match rules to update match state                 |
| Rendering            | Yes           | Show entities on the screen                             |

Systems not mentioned here are not ECS system.

## System / Component Matrix
| System    | Reads                                          | Writes      |
| --------- | ---------------------------------------------- | ----------- |
| Movement  | Position, Movement, Stamina                    | Position    |
| Combat    | Equipment, Ability, Health, Stamina            | Health      |
| AI        | Match_State, Position, Stamina                 | Command     |
| Match     | Health, Match_Rules                            | Match_State |
| Rendering | Position, Image                                | —           |

## Domain Model / ECS Boundary
Domain is separated from ECS entities and components. 

The domain supplies the data to the ECS engine for its computations.  
In this way it is possible to keep the engine as generic as possible for reusability.

## Open Questions

# Implementation project
## Entity
It is an unsigned integer for storing the ID.  

## Component
It is a struct holding data (e.g. Position -> X : Unsigned int, Y: Unsigned int). Each component knows the values of its data for each entity that needs the component. 

## System
A System operates on the entities that provide the components required by the system. 

It holds the logic to apply on the components data.

The update function run from the engine allows to iterate through the registered entites updating all the components related to them.

## World
Manages the systems creation/registration, the assignement of the components to the systems and provides the entities knowing the free IDs. 

Allow also to register entities to components and systems. 