# ELEC2645 Unit 4 Group Project

This repository contains the final code for our ELEC2645 Unit 4 STM32 mini game console project.

The project runs on an STM32 Nucleo-L476RG board and integrates a shared menu system with multiple games. The system uses a 1.54-inch ST7789V2 LCD screen, joystick, joystick switch, separate button, buzzer and PWM output.

## Hardware

- STM32 Nucleo-L476RG
- 1.54-inch ST7789V2 LCD
- Joystick
- Joystick SW / PC3
- Button / PC2
- Buzzer
- PWM LED

## Project Overview

The project is structured as a small embedded game console. A shared menu system allows the player to select and enter different games. Each game is implemented as a separate module, while common hardware drivers and input handling are shared across the whole project.

The main software structure is based on a state-machine style menu system:

- `main.c` controls the overall menu state.
- `shared/Menu.c` handles menu navigation and game selection.
- `shared/InputHandler.c` handles button input.
- `game_1/`, `game_2/` and `game_3/` contain the individual game implementations.
- LCD, joystick, buzzer and PWM drivers are reused across the games.

## Games

### Game 1: Dodge Rush

Game 1 is a falling-object survival game.

The player controls a block near the bottom of the LCD screen and avoids falling obstacles. The game includes score, high score, HP, level progression, bonus HP items, collision detection and temporary invincibility after being hit.

Main features:

- Joystick-controlled player movement
- Falling obstacles
- HP and collision detection
- Score and high score
- Level-based difficulty progression
- Bonus HP items
- Temporary invincibility after collision
- Top HUD and bottom taskbar
- Buzzer feedback for game events

### Game 2: Fighting Game

Game 2 is a sprite-based 2D fighting game.

The game uses character images instead of simple rectangles. Player and enemy characters have different states such as idle, movement, crouch, jump, attack, hit and death. Character images are converted into C arrays and drawn on the LCD using image drawing functions.

Main features:

- Player and enemy character sprites
- Multiple character states and animations
- Weapon switching
- Four weapons: fists, dagger, whisk and spear
- Different attack ranges for different weapons
- Attack box and hurtbox collision judgement
- Crouch and jump hurtbox changes
- Enemy behaviour based on distance and random actions
- HP bars and result display
- RGB565 image data optimisation to reduce Flash memory usage

### Game 3: Maze Game

Game 3 is a coordinate-based maze game.

The player moves through 32×32 grid-based mazes using the joystick. The maze is represented by 2D arrays, where walls block movement and open cells allow movement. The player position is updated using XY coordinate movement while preventing movement through walls or outside the maze boundary.

Game 3 includes two modes:

#### Campaign Mode

In Campaign Mode, the player completes maze rounds while a timer records the elapsed time. The player moves through the maze and reaches the target area to complete the round.

#### Challenge Mode

In Challenge Mode, the player must clear circles placed inside the maze. The game tracks which circles are still active and displays them on the LCD. The player must move through the maze, collect the required circles, and complete the challenge within the game rules.

Main features:

- 32×32 grid-based maze maps
- XY coordinate movement
- Wall collision / boundary restriction
- Campaign mode
- Challenge mode
- Circle collection mechanic
- Timer display
- Best time record
- LCD maze rendering
- Buzzer feedback for win / lose events

## Controls

General controls:

- Joystick: menu navigation and movement
- Joystick SW / PC3: confirm selection, start, pause, resume, restart or game-specific action
- Button / PC2: return to menu or game-specific action

Game-specific behaviour may vary slightly depending on the selected game.

## Project Structure

```text
Core/                         STM32CubeMX generated source files
Drivers/                      STM32 HAL and CMSIS drivers
Buzzer/                       Buzzer driver
Joystick/                     Joystick driver
PWM/                          PWM driver
ST7789V2_Driver_STM32L4/      LCD driver
shared/                       Shared menu and input handler
game_1/                       Dodge Rush game
game_2/                       Fighting game
game_3/                       Maze game
cmake/                        CMake support files
CMakeLists.txt                Main CMake project file
Unit_4_1_Menu_Template.ioc    STM32CubeMX project file
