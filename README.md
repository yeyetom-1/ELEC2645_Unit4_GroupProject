# ELEC2645 Unit 4 Group Project

This repository contains the final code for our STM32 mini game console project.

## Hardware

- STM32 Nucleo-L476RG
- 1.54-inch ST7789V2 LCD
- Joystick
- Joystick SW / PC3
- Button / PC2
- Buzzer
- PWM LED

## Games

### Game 1: Dodge Rush
A falling-object survival game with score, HP, high score, levels, bonus items and invincibility after collision.

### Game 2: Fighting Game
A sprite-based fighting game with character images, weapon switching, attack boxes, hurtboxes and LCD image rendering.

### Game 3
Additional group game integrated into the shared menu system.

## Controls

- Joystick: move / menu navigation
- Joystick SW / PC3: select, start, pause, restart, or weapon switch depending on the game
- Button / PC2: return to menu or game-specific action

## Project Structure

- `game_1/`: Dodge Rush source code
- `game_2/`: Fighting game source code
- `game_3/`: Third game source code
- `shared/`: menu and input handling
- `ST7789V2_Driver_STM32L4/`: LCD driver
- `Joystick/`: joystick driver
- `Buzzer/`: buzzer driver
- `PWM/`: PWM driver
