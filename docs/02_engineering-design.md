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
def main():
    """
    function calls go below here
    """
    pass

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
