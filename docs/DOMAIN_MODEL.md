# Character
It is the main actor of the game. It's the one which is fighting in the ARENA. 
- IT HAS -> Equipment.
- IT HAS -> Life points. 
- IT HAS -> Resistance.
- IT HAS -> Speed movement.
- IT HAS -> Stamina. It determines if it is still able to move or attack or it must rest for a little bit of time to regain some of it to continue the fight. Ending the stamina doesn't mean losing.
- IT HAS -> Stamina regain. In case of 0 stamina, the player can't move until enough stamina to move is regained.

# Equipment
Represents every object which can be employed by the character. The available ones are Weapons and Armors. Characters can wear only one armor and use one or more weapons according to their characteristics.
- IT HAS -> Durability.
- IT HAS -> Attack points (Weapons).
- IT HAS -> Resistance (Armors). In case the equipment provides resistance, this value is sum to the character resistance.
- IT HAS -> Abilities.
- IT HAS -> Range (Weapons).

# Ability
It provides the equipment with special powers. 
- IT HAS -> Type. It provides magic or physical skills.
- IT HAS -> Bonus. It can boost either attack points or resistance or stamina regain.
- IT HAS -> Cost. It reduces the player stamina when used.

### Out of scope
Right now regeneration items for the life ponts like potions are out of scope.

# Arena
It's the theatre of the fight. 
- IT HAS -> Characters.
- IT HAS -> Obstacles. 
- IT HAS -> Fixed dimension and the characters cannot exit it until the match is over. The arena models are fixed and can be chosen before the match.

# Match
It is the main event of the game. It is the moment when the fight happens. It ends when one of its victory condition is met. 
- IT HAS -> Arena.

# Obstacle
It is an entity present in the arena that spice up the match. It can act as a barrier to stop opponent's attack or slow down the characters while they are inside it. 
- IT HAS -> Durability. Characters attacks damage it. Once its 0, it disappears.
- IT HAS -> Malus (if it is spread on the ground)