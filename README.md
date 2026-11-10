What Makes a Hero?
What Makes a Hero? is a short 2D narrative RPG created in Microsoft MakeCode Arcade using JavaScript/TypeScript.

The game follows Prince Lancer, who is sent on a traditional heroic mission after hearing that Princess Noelle has been taken by monsters. As the journey continues, the player discovers that the situation is more complicated than it first appeared.

The project explores the question:
Does achieving a heroic goal automatically make your actions heroic?

The player can choose to fight enemies or attempt to understand them. These decisions are stored throughout the game and influence the final ending.

Game Overview
- Genre: Narrative RPG / Adventure
- Platform: Microsoft MakeCode Arcade
- Language: JavaScript / TypeScript
- Playtime: Approximately 5–10 minutes
- Areas: 6
- Main encounters: 3
- Endings: 2
The game was influenced by choice-based RPGs such as Undertale and Deltarune, particularly their use of combat mechanics to encourage players to consider alternatives to violence.

Story
Prince Lancer leaves the kingdom believing that monsters have kidnapped Princess Noelle.

During the journey, he encounters three creatures:
Tarn — The Frightened Guard
Tarn believes Lancer is dangerous.

To resolve the encounter peacefully, the player must:

Lower Sword → Explain → MERCY
Moss — The Hungry Creature
Moss attacks because it is hungry.

The player can:

Ask What's Wrong → Offer Food → MERCY

The player must have collected bread before food can be offered.
Wren — The Lonely Ghost
Wren wants someone to acknowledge and listen to them.

The peaceful route requires:

Ask Name → Listen → MERCY

Battle System
Each encounter provides three main choices:
FIGHT
The player attacks using a timing-bar mechanic.

The closer the marker is to the centre of the bar, the stronger the attack:
- Critical Hit — marker is very close to the centre
- Normal Hit — marker is within the normal hit area
- Miss — marker is too far from the centre
UNDERSTAND
UNDERSTAND provides character-specific actions that allow the player to learn why an enemy is attacking.

Each encounter requires the player to complete the correct sequence before MERCY becomes available.
MERCY
MERCY becomes available after the required UNDERSTAND conditions have been completed.

The battle menu visually changes to indicate when MERCY can be selected.

Dodge System
After an unsuccessful or non-lethal FIGHT action, the player enters a short dodge phase.

The player controls a heart inside a restricted arena while avoiding projectiles.

Each enemy has a different projectile pattern:
- Tarn: projectiles travel vertically downward.
- Moss: projectiles enter horizontally from either side.
- Wren: projectiles move toward the player's current position.
A temporary 900 ms invincibility period prevents multiple overlapping projectiles from removing several lives immediately.

Choices and Endings
The game remembers the player's decisions throughout the journey.

A kills variable records whether any creatures have been killed.
if (kills == 0) {
    // Peaceful ending
} else {
    // Violent ending
}
Peaceful Ending
Achieved when:
kills == 0
The player reaches Princess Noelle without killing Tarn, Moss or Wren.
Violent Ending
Triggered when the player kills one or more creatures.

The ending changes according to the consequences of the player's previous actions.

Main Programming Concepts
This project uses several programming concepts developed throughout the course:
- Variables
- Boolean values
- Conditionals
- Functions
- Arrays
- Classes and objects
- Game states
- Sprite collision
- Controller events
- Runtime calculations
- Projectile movement
- Persistent state
- Custom movement and collision detection

Game States
The game uses a GameMode system to control which actions are available at different points.
Cutscene
Explore
Menu
Understand
Timing
Dodge
Ending
This prevents input intended for one part of the game from affecting another part.

For example, movement controls behave differently during exploration and the dodge phase.

Persistent State
The game stores information about previous player actions.

Examples include:
- kills — number of enemies killed
- hasBread — whether the player currently has bread
- breadTaken — whether bread has already been collected
- flagA and flagB — progress through an enemy's peaceful interaction
- canMercy — whether MERCY is currently available
- Creature state — unresolved, spared or killed
These variables allow decisions made earlier in the game to affect later dialogue, encounters and endings.

Movement and Collision
The project uses a custom movement system.

Instead of checking only the player's final position, movement is checked in smaller steps. This reduces the possibility of the player moving through walls when travelling at higher speeds.

The system uses functions such as:
blocked()
sweepMove()
exploreFrame()

Controls
Directional buttons / Arrow keys
Move Prince Lancer during exploration and navigate menus.

A button
Interact, confirm menu selections and stop the timing-bar marker during attacks.

During dodge sequences, use the directional controls to move the heart and avoid projectiles.

Development Process
The project was originally planned using MakeCode Arcade Blocks.

As the battle system became more complex, managing nested conditions, variables and multiple states visually became difficult. Development therefore moved to MakeCode's JavaScript/TypeScript editor.

The project was developed iteratively through:
1. Early Blocks experiments
2. Transition to JavaScript
3. Map and movement development
4. Enemy interaction and state systems
5. Timing-bar combat
6. Dodge mechanics
7. Debugging and collision testing
8. Persistent route tracking
9. Ending implementation
10. Full-game testing and refinement

Running the Project
The game was developed using Microsoft MakeCode Arcade.

To work with the project:
1. Open Microsoft MakeCode Arcade.
2. Open or import the project.
3. Switch to the JavaScript editor to view the source code.
4. Run the game using the MakeCode Arcade simulator.
Microsoft MakeCode Arcade:
https://arcade.makecode.com/

Development Resources
Resources consulted during development included Microsoft MakeCode Arcade documentation and tutorials covering areas such as sprites, maps, JavaScript, collision detection and game development.

Relevant MakeCode resources include:
•	Fox, T. (2018–2025). Deltarune [Video game]. Toby Fox.
•	Microsoft MakeCode. (n.d.). Activity: Boolean statements and expressions. https://arcade.makecode.com/courses/csintro2/logic/booleans
•	Microsoft MakeCode. (n.d.). Activity: If and else comparisons. https://arcade.makecode.com/courses/csintro2/logic/if-else
•	Microsoft MakeCode. (n.d.). Maze. https://arcade.makecode.com/tutorials/maze
•	Chris Courses. (2022, March 12). Pokémon JavaScript game tutorial with HTML Canvas [Video]. YouTube.
https://www.youtube.com/watch?v=yP5DKzriqXA
•	freeCodeCamp.org. (2022, September 28). Code a 2D game using JavaScript, HTML, and CSS (w/ free game assets) – Tutorial [Video]. YouTube.
https://www.youtube.com/watch?v=7BHs1BzA4fs
•	Chris Courses. (2020, September 21). HTML5 Canvas and JavaScript game tutorial [Video]. YouTube.
https://www.youtube.com/watch?v=eI9idPTT0c4
•	Tan, C. (n.d.). Introduction to object-oriented programming with MakeCode Arcade. Little Bird Electronics.
https://littlebirdelectronics.com.au/projects/introduction-to-object-oriented-programming-with-makecode-arcade
•	Tan, C. (n.d.). Player selection screen with MakeCode Arcade. Little Bird Electronics.
https://littlebirdelectronics.com.au/projects/player-selection-screen-with-makecode-arcade
•	freeCodeCamp.org. (2020, April 8). Learn JavaScript by building 7 games [Video]. YouTube.
https://www.freecodecamp.org/news/learn-javascript-by-building-7-games-video-course/


Project Purpose
The technical goal of the project was to develop my understanding of code literacy through the creation of a larger interactive system.

During development, my understanding of coding shifted from seeing variables, functions and conditionals as separate concepts toward understanding how they interact as part of a complete system.

The final game can be understood as a sequence of connected processes:
Player Input
      ↓
Function
      ↓
Variable / State Change
      ↓
Conditional Check
      ↓
Game Response
      ↓
Future Consequence
The narrative also demonstrates that computational rules contain design decisions. In What Makes a Hero?, the program does not independently determine what counts as heroic. The game's rules and ending conditions represent choices made during the design process.

Credits
Game design, programming and development: Michael Wang

Platform: Microsoft MakeCode Arcade

Narrative/gameplay inspiration: Undertale and Deltarune by Toby Fox

Development references: Microsoft MakeCode Arcade documentation and tutorials.

Academic Project
This project was created for 52685 Creative Coding at the University of Technology Sydney (UTS) as part of the Code Prototype Project assessment.
