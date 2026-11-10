What Makes a Hero?

What Makes a Hero? is a short 2D narrative RPG created in Microsoft MakeCode Arcade using JavaScript/TypeScript.

The game follows Prince Lancer, who begins his journey believing that Princess Noelle has been taken by monsters. As he travels through the kingdom, he gradually discovers that the situation is more complicated than he first assumed.

The project explores the question:

Does achieving a heroic goal automatically make your actions heroic?

The player's decisions during each encounter are remembered by the game and influence the final ending.

Table of Contents

Game Overview

Story

Characters and Encounters

Battle System

Dodge System

Choices and Endings

Main Programming Concepts

Game States

Persistent State

Movement and Collision

Controls

Development Process

Running the Project

Development Resources

Project Purpose

Credits

Academic Project

Game Overview

Genre: Narrative RPG / Adventure

Platform: Microsoft MakeCode Arcade

Programming language: JavaScript / TypeScript

Estimated playtime: 5 to 10 minutes

Areas: 6

Main enemy encounters: 3

Endings: 2

The game is influenced by choice-based RPGs such as Undertale and Deltarune, particularly their use of combat systems where violence is not always the only available solution.

Story

Prince Lancer begins the game in the throne room, where he is sent on a journey after hearing that Princess Noelle has been taken by monsters.

Lancer travels through several areas while encountering creatures that initially appear to be enemies.

As the player learns more about them, it becomes clear that the original story was incomplete.

The player must decide whether to immediately fight these characters or attempt to understand why they are behaving aggressively.

These choices determine how the story develops and what happens at the end of the game.

Characters and Encounters

Prince Lancer

Lancer is the main playable character.

He begins the game with a traditional understanding of heroism, where defeating monsters appears to be the correct response.

The player's choices gradually determine what kind of hero Lancer becomes.

Tarn

Tarn is a frightened guard who believes that Lancer is dangerous.

The peaceful solution involves lowering Lancer's weapon and explaining his intentions before MERCY becomes available.

Moss

Moss attacks because it is hungry.

The player can ask what is wrong and later offer food if bread has been collected earlier in the game.

The peaceful route therefore depends on both dialogue choices and an item collected during exploration.

Wren

Wren is a lonely ghost who wants to be recognised and listened to.

The player must first learn Wren's name and then choose to listen before the encounter can be resolved peacefully.

Princess Noelle

Noelle becomes important near the end of the game.

Her dialogue reveals more information about the monsters Lancer encountered and forces the player to reconsider the consequences of their earlier decisions.

Battle System

Each enemy encounter contains three main options:

FIGHT

FIGHT begins a timing-bar mechanic.

A marker moves across the bar and the player presses the action button to stop it.

Damage depends on the marker's distance from the centre.

A marker very close to the centre produces a critical hit

A marker within the normal hit range produces a normal hit

A marker outside the hit range produces a miss

The calculation is based on the distance between the marker and the centre of the timing bar.

let off = Math.abs(marker.x - BAR_CENTRE)

if (off <= CRIT_RANGE) {
    dmg = 3
} else if (off <= HIT_RANGE) {
    dmg = 2
}

UNDERSTAND

UNDERSTAND opens character-specific interaction choices.

Each creature requires the player to complete different actions before MERCY becomes available.

The system uses Boolean variables to remember which actions have already occurred.

For example:

canMercy = c.flagA && c.flagB

This means that both required interaction conditions must be completed before the game allows the peaceful option.

MERCY

MERCY allows the player to end an encounter peacefully.

It remains unavailable until the required UNDERSTAND conditions have been completed.

The menu uses visual feedback to show whether MERCY is currently available.

Dodge System

After certain FIGHT actions, the player enters a short dodge phase.

The player controls a heart inside a restricted arena and must avoid enemy projectiles.

Each enemy uses a different projectile pattern.

Tarn

Tarn's projectiles move vertically downward.

Moss

Moss's projectiles enter from either side of the arena and move horizontally.

Wren

Wren's projectiles move toward the heart's position.

The system also includes temporary invincibility after being hit.

if (game.runtime() - lastHit > 900) {
    lastHit = game.runtime()
    info.changeLifeBy(-1)
}

This prevents several overlapping projectiles from removing multiple lives almost immediately.

Choices and Endings

The game stores the consequences of the player's actions.

The variable kills records how many creatures have been killed.

At the end of the game, this value determines the route.

if (kills == 0) {
    // Peaceful ending
} else {
    // Violent ending
}

Peaceful Ending

The peaceful ending occurs when the player reaches the end of the game without killing Tarn, Moss or Wren.

The condition is:

kills == 0

Violent Ending

The violent ending occurs when one or more creatures have been killed.

The ending also identifies which characters are missing as a result of the player's previous actions.

Main Programming Concepts

The project uses several programming concepts developed throughout the course:

Variables

Boolean values

Conditionals

Functions

Arrays

Classes

Objects

Game states

Sprite collisions

Controller events

Runtime calculations

Projectile movement

Persistent state

Custom movement

Collision detection

User interface logic

Game States

The project uses a GameMode system to control which part of the game is currently active.

The available modes are:

Cutscene
Explore
Menu
Understand
Timing
Dodge
Ending

Different controller inputs behave differently depending on the current mode.

For example, directional input moves Lancer while exploring, but controls the heart during the dodge phase.

This prevents the same button press from triggering unrelated actions in different parts of the game.

Persistent State

A major part of the game is remembering previous player actions.

Important variables include:

kills

hasBread

breadTaken

canMercy

flagA

flagB

Creature state

kills

Records how many enemies the player has killed.

hasBread

Records whether the player currently has bread.

breadTaken

Records whether the bread has already been collected from the map.

flagA and flagB

Store progress through each creature's UNDERSTAND interaction.

canMercy

Controls whether MERCY is currently available.

Creature state

Each creature stores whether it is:

0 = unresolved
1 = spared
2 = killed

These stored values allow decisions made earlier in the game to affect later scenes and the ending.

Movement and Collision

The game uses a custom movement and collision system.

At higher movement speeds, checking only Lancer's final position could allow him to move through thin walls.

To reduce this problem, movement is checked in smaller steps.

Important functions include:

blocked()
sweepMove()
exploreFrame()

The game also remembers the player's previous safe position so movement can be corrected if the next position is blocked.

This helped prevent Lancer from moving through walls or becoming stuck around map boundaries.

Controls

Exploration

Arrow keys / directional controls

Move Prince Lancer around the map.

A button

Interact with characters and objects.

Battle Menu

Directional controls

Navigate between FIGHT, UNDERSTAND and MERCY.

A button

Confirm a selection.

Timing Attack

A button

Stop the timing marker.

Dodge Phase

Directional controls

Move the heart inside the dodge arena.

Development Process

The project was originally planned using MakeCode Arcade Blocks.

I first used Blocks for movement, sprites, dialogue and early battle logic.

As the project became more complex, the visual workspace became increasingly difficult to manage. The battle system required several connected variables, conditions, enemy states and controller events.

I eventually moved the project into MakeCode's JavaScript editor.

The main development stages were:

Early Blocks experimentation

Basic movement and throne room development

Transition from Blocks to JavaScript

Map development

Collision testing

UNDERSTAND interaction system

Enemy state management

Timing-bar combat

Projectile dodge system

Debugging repeated damage

Persistent state and route tracking

Ending implementation

Full playtesting and refinement

One of the main changes in my development process was moving from random trial and error toward tracing specific variables, states and execution order when debugging.

Running the Project

The project was created using Microsoft MakeCode Arcade.

To run or edit the game:

Open Microsoft MakeCode Arcade.

Import or open the project.

Run the game in the MakeCode Arcade simulator.

Open the JavaScript editor to view the source code.

Use the simulator controls to play through the game.

Microsoft MakeCode Arcade:

https://arcade.makecode.com/

Development Resources

The following MakeCode resources were relevant during development:

Microsoft MakeCode Arcade

https://arcade.makecode.com/

Setting the Scene

https://arcade.makecode.com/concepts/setting-the-scene

Maze Tutorial

https://arcade.makecode.com/tutorials/maze

I also consulted JavaScript and game-development tutorials while learning concepts such as functions, classes, collision detection, projectile movement and game-state management.

Any external tutorials or resources used during development are acknowledged in the accompanying project documentation and reference list.

Project Purpose

The technical purpose of this project was to develop my code literacy through the creation of a larger interactive system.

At the beginning of development, I mainly understood programming concepts individually.

For example, I knew what a variable, function or conditional was, but I did not fully understand how these concepts interacted inside a larger program.

During the project, I began to understand coding more as a connected process:

Player Input
      ↓
Function
      ↓
Variable or State Change
      ↓
Conditional Check
      ↓
Game Response
      ↓
Future Consequence

The game also made me think about how programming rules can represent design decisions.

For example, the condition:

kills == 0

is technically a simple Boolean comparison.

However, inside the game it represents a much larger design decision about how the project defines a peaceful or heroic outcome.

The program follows the rule that I created, meaning the moral interpretation comes from the designer rather than from the computer itself.

Credits

Game design and development: Michael Wang

Programming environment: Microsoft MakeCode Arcade

Programming language: JavaScript / TypeScript

Game inspiration: Undertale and Deltarune by Toby Fox

Development resources: Microsoft MakeCode Arcade documentation, tutorials and JavaScript learning resources.

Academic Project

What Makes a Hero? was developed for 52685 Creative Coding at the University of Technology Sydney as part of the Code Prototype Project assessment.
