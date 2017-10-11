# TermGui
Terminal choice selector menu and sub menus

<hr>
 
## Requirements
 - FancyOut.py | http://github.com/vindennl48/fancyout

## How To Use
```python
from TermGui import *
```

The easiest and least painful way to use this
module is by the following method:
```python
gui = TermGui({
    '<name of menu>':MenuFrame('<name of menu>', [
        ['<name of first choice>',  <result of first choice>],
        ['<name of second choice>',  <result of second choice>]
    ]),
    '<name of menu>':MenuFrame('<name of menu>', [
        ['<name of first choice>',  <result of first choice>],
        ['<name of second choice>',  <result of second choice>]
    ])
})
```
 
Results of menu choices can take two different forms:
 - Integer
   - The integer will be returned by gui.run(xx) so you can identify what choice was selected.
 - String
   - The string needs to be the name of a menu to switch to. This is used to go into sub menus or go back to a previous menu.
 
To use this inside of your own code, the easiest way is to create a 'while' loop:
 ```python
 result = 'Main Menu'
 while (result != -1):
     prev_result = result
     result = gui.run(result)
 
     if result == 10:
         # perform an action associated with this
         #  menu choice
         print("You Chose Option 10!")

         # Ending Options, Choose one or write your own
         result = prev_result    # Return to last menu
         result = '<menu name>'  # Switch to a different menu
         exit()                  # Exit Program
 
     if result == 20:
         # perform an action associated with this
         #  menu choice
         print("You Chose Option 10!")

         # Ending Options, Choose one or write your own
         result = prev_result    # Return to last menu
         result = '<menu name>'  # Switch to a different menu
         exit()                  # Exit Program

     elif type(result) == int:
         # Failsafe incase an option does not have an if statement
         result = prev_result

     else:
         # This will catch any other exceptions that are not
         #  acceptable
         raise Exception("No Menu Or Option Is Available!")
```

## Example Code
```python
from TermGui import *

gui = TermGui({
    'Main Menu':MenuFrame('Main Menu', [
        ['First Choice',  'First Choice'],
        ['Second Choice', 20],
        ['Exit',  -1]
    ]),
    'First Choice':MenuFrame('First Choice', [
        ['Another First Choice', 11],
        ['Another First Choice', 21],
        ['Another First Choice', 31]
    ])
})

result = 'Main Menu'
while (result != -1):
    prev_result = result
    result = gui.run(result)

    if result == 20:
        print("My Result is 20!")
        result = prev_result

    if result == 11:
        print("My Result is 11!")
        result = prev_result

    if result == 21:
        print("My Result is 21!")
        result = prev_result

    if result == 31:
        print("My Result is 31!")
        result = prev_result

     elif type(result) == int:
         result = prev_result

     else:
         raise Exception("No Menu Or Option Is Available!")
```


