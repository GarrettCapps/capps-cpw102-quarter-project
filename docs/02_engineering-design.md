# Engineering Design Document


## Overview

The Character Creator will handle the necessary choices to make a V&V Character. In order, the user will:
    Choose a species and (if applicable) Subspecies
    Distribute points into their S.P.E.C.I.A.L. Stats
    Select a background
    Select their Tagged Skill(s)
The application will track these decisions and display them to the user as the character creation process goes along.
Once the character creation process has been finished, the application will output the created character to the user.
    
## System Diagrams

[This document must include one or more of the following:

- block diagram of your proposed functions and modules, including external libraries
- flowchart of logic for critical flows
- mockups of any program-driven user interfaces, if applicable]

## Technical Details


### Inputs

For baseline functionality, the Character Creator will take input from the user through the console. Time permitting, a GUI will be developed afterwards. Most data, whether entered as a string or integer (or mouse click), will be stored internally as integers, enabling the use of lists for handling species, subspecies, and background selection and display, as well as simplifying the modification of S.P.E.C.I.A.L. Stats.

#### Handling bad inputs

Input that is technically valid but formatted poorly can be handled with tools such as .strip() and .lower(). Invalid input can be handled with loops, rejecting invalid input and prompting the user again until valid input is given. Should a GUI be properly implemented, preventing invalid input becomes more about ensuring the user goes through the character creation process in the right order, which can be done with booleans and if statements checking for prerequisite steps being completed.

### Logic

[At a high level, describe the logic you will need to apply. What Python tools will you use to capture that logic? For loops, while loops, exceptions?] 

### Functions

[How will you break your flow of logic up into functions? Write some pseudo code for your `main()` function to show how your app will coordinate its duties.]

``` python
import random
# Initialize global variables for tracking character information like stats,
# skills, species/subspecies and background
# these are made global so that multiple functions can reference and modify them

# Stats start at and have an absolute minimum of 1
# And max out at 10
strength = 1
perception = 1
endurance = 1
charisma = 1
intelligence = 1
agility = 1
luck = 1
SPECIAL_MAXIMUM = 10

# Stat modifiers are derived from the formula of the Stat - 5
strength_modifier = -4
perception_modifier = -4
#etc.

# Tagged stats receive a bonus to saving throws, and need to be communicated to the user
strength_tagged = False
perception_tagged = False
#etc.

# Species give Stat bonuses which can not be removed
# effectively raising the stat floor above 1. These variables track that
strength_minimum = 1
perception_minimum = 1
#etc.

# Skills range from 0 to 100 and, at character creation,
# are derives from their related S.P.E.C.I.A.L. stats

#Strength skills
melee = 0
#perception skills
energy = 0
explosives = 0
lockpick = 0
#endurance skills
big_guns = 0
survival = 0
unarmed = 0
#charisma skills
barter = 0
speech = 0
#intelligence skills
medicine = 100
repair = 100
science = 100
#agility skills
small_guns = 0
sneak = 0

# Tagged skills receive a starting bonus of +15
# and have other minor gameplay implications
# and must be communicated to the user
melee_tagged = False
energy_tagged = False
explosives_tagged = False
#etc.

# (Most) Species give tagged skills. Tagged skills given by species can not be untagged
# and so their status being locked needs to be tracked
melee_locked = False
energy_locked = False
explosives_locked = False
# etc.

# SPECIAL points are spent by the user to increase their S.P.E.C.I.A.L. stats.
# Most species get 33 points. Humans get 35.
# Track remaining points to distribute
special_points = 33

# All characters get to choose one free tag skill
# except humans, which get three.
tags_left = 1

def main():
    # input lists of species/subspecies and backgrounds
    # The user will select species and subspecies simultaneously
    # As I am unsure how I would associate them with each other with the modular approach I've taken
    with open("species.txt", "r") as file:
        species_list = [line.strip() for line in file.readlines()]
    with open("backgrounds.txt", "r") as file:
        backgrounds_list = [line.strip() for line in file.readlines()]
    # print some sort of header to the console
    # likely modeled after Fallout terminals
    # for the sake of aesthetics
    print_header()
    # Prompt user to select species
    species = input_species_choice()
    # Humans get more tagged skills and S.P.E.C.I.A.L. points
    # Using the text value rather than the integer to prevent
    # bugs if more species are added, shifting where Human is
    # on the list
    if species_list[species] = "Human":
        special_points += 2
        tags_left += 2
    # The Worker subspecies of Synths (synthetic humans) get a choice on
    # whether to tag Science or Barter.
    if species_list[species] = "Gen. 2 Worker Synth":
        worker_synth_tag_select()
    if species_list[species] = "Gen. 3 Worker Synth":
        worker_synth_tag_select()
    # assign S.P.E.C.I.A.L. points to stats
    distribute_special()
    #Update special modifiers now that special has been distributed
    calculate_special_modifiers()
    # Prompt user to select a background
    background = input_background_choice()
    # Selecting a tagged skill/ tagged skills
    distribute_skill_tags()
    #
    calculate_skills()

def input_species_choice(species_list):
    print([-1]: Random)
    for i in range(len(species_list)):
            # Number each choice
            print(f"[{i}]: {species_list[i]}")
    while True: #loop to ensure a valid input
        try:
            species_choice = int(input("Select a species: "))
        except ValueError: # prevent non-integer input
            print("Please enter an integer value!")
        else:
            #only return a valid value
            if species_choice <= len(species_list):
                # -1 indicates a random choice
                if species_choice = -1:
                    return random.randint(0, len(species_list))
                else :
                    return species_choice
            else:
                print("Please enter a valid choice!")
#Background choice will operate functionally the same as species
def input_background_choice():
    #et cetera

def distribute_special():
    while special_points > 0:
        print(f"Strength: {strength}")
        print(f"Perception: {perception}")
        print(f"Endurance: {endurance}")
        print(f"Charisma: {charisma}")
        print(f"Intelligence: {intelligence}")
        print(f"Agility: {agility}")
        print(f"Luck: {luck}")
        print(f"S.P.E.C.I.A.L. Points remaining: {special_points}")
        stat = input("Select a S.P.E.C.I.A.L. stat to modify: ")
        stat = stat.strip().lower()
        #verify input
        match stat:
            case strength:
                # Ensure that the stat remains within its bounds
                if strength + stat_modification >= strength_minimum
                    if stat_modification < 0:
                        strength += stat_modification
                        special_points -= stat_modification
                    if strength + stat_modification <= SPECIAL_MAXIMUM:
                        strength += stat_modification
                        strength -= stat_modification
                    else:
                        #adding too much
                        
                else:
                    #subtracting too much
                    strength = strength_minimum
                    
            
            

def print_character_sheet()
            

main()

```

### Libraries

[How can you leverage external libraries to:

- take advantage of functionality already written and tested by others?
- improve the performance, user experience, or features in your application?

All apps should leverage libraries. ]

### Output

[What exactly will you output to the user? Options could be:

- printing a report to the terminal at the end of a program
- repeatedly giving users updates on an iterative process
- creating a file based on user-entered data

If applicable, show an example output below:]

```

```
