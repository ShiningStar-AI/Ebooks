# Coding Projects in Python

# Project reference

The "Project reference" section of the sources provides the complete Python code for each project in the book, excluding the hacks and tweaks. Below are the codes for each project as presented in that section:

### Animal Quiz

This code defines a function `check_guess` that evaluates a player's answer, considering up to three attempts, and the main script that uses this function to run the quiz.

```python
def check_guess(guess, answer):
    global score
    still_guessing = True
    attempt = 0
    while still_guessing and attempt < 3:
        if guess.lower() == answer.lower():
            print('Correct Answer')
            score = score + 1
            still_guessing = False
        else:
            if attempt < 2:
                guess = input('Sorry wrong answer. Try again ')
            attempt = attempt + 1
    if attempt == 3:
        print('The correct answer is ' + answer)

score = 0
print('Guess the Animal')
guess1 = input('Which bear lives at the North Pole? ')
check_guess(guess1, 'polar bear')
guess2 = input('Which is the fastest land animal? ')
check_guess(guess2, 'cheetah')
guess3 = input('Which is the largest animal? ')
check_guess(guess3, 'blue whale')
print('Your score is ' + str(score))

```

The Animal Quiz project is designed to create a simple quiz game about animals where players guess answers and score points for correct responses. The game gives players three chances to answer each question, and their final score is revealed at the end.

Here's a step-by-step explanation of the Animal Quiz code:

1. **Initial Setup**
    - The game begins by **initializing a `score` variable to 0** (`score = 0`). This variable will keep track of the player's correct answers throughout the game.
    - A welcome message, "Guess the Animal!", is displayed to the player using the `print()` function (`print('Guess the Animal!')`). This is the first thing the player sees.
2. **Defining the `check_guess` Function**
    - A core part of the quiz is the `check_guess()` function, which is defined at the top of the script. This function's purpose is to **compare the player's `guess` to the `answer`** for a question. Functions are reusable blocks of code that perform specific tasks.
    - It takes two **parameters**: `guess` (the player's input) and `answer` (the correct answer). Parameters are like variables that belong to the function and allow data to be passed to it.
    - The line `global score` declares that the `score` variable inside this function refers to the **global `score` variable** defined outside the function. This ensures that any changes made to `score` within `check_guess()` affect the overall game score.
    - Two additional variables are initialized within the function: `still_guessing = True` and `attempt = 0`.
        - `still_guessing` is a **Boolean variable** (can be True or False) that tracks whether the player has found the right answer for the current question. It's initially `True` because the answer hasn't been found yet.
        - `attempt` tracks the number of guesses the player has made for the current question.
    - A **`while` loop** is used to give the player multiple chances to answer (`while still_guessing and attempt < 3:`). The loop continues as long as `still_guessing` is `True` and the `attempt` count is less than 3.
    - Inside the loop, an `if` statement compares the player's guess to the correct answer (`if guess.lower() == answer.lower():`).
        - The `.lower()` function is applied to both the `guess` and `answer` to **convert them to lowercase** before comparison. This ensures the comparison is **case-insensitive**, meaning "polar bear" and "Polar Bear" are both recognized as correct.
        - If the guess is correct:
            - "Correct answer" is printed.
            - **`score` is increased by 1** (`score = score + 1`).
            - `still_guessing` is set to `False` (`still_guessing = False`), which stops the `while` loop for this question.
        - If the guess is incorrect (the `else` block):
            - Another `if` statement checks if `attempt` is less than 2 (`if attempt < 2:`), meaning the player still has guesses left.
            - If so, it prompts the player to "Sorry wrong answer. Try again. " and takes new input for `guess`.
            - The `attempt` variable is increased by 1 (`attempt = attempt + 1`).
            - If `attempt` reaches 3 (all chances used), "The correct answer is " followed by the `answer` is printed.
3. **Asking Questions and Calling the Function**
    - After defining `check_guess`, the main quiz flow starts by asking the first question: `guess1 = input('Which bear lives at the North Pole? ')`. The player's typed answer is stored in the `guess1` variable.
    - The `check_guess()` function is then **called** to evaluate this answer: `check_guess(guess1, 'polar bear')`. This runs the logic defined in the `check_guess` function with `guess1` as the player's input and 'polar bear' as the correct answer.
    - This process is **repeated for subsequent questions**, such as the fastest land animal and the largest animal, storing answers in `guess2` and `guess3` respectively, and calling `check_guess` for each.
4. **Displaying the Final Score**
    - At the end of the quiz, the player's total score is displayed.
    - The `print()` statement `print('Your score is ' + str(score))` combines a string with the numerical `score`.
    - The `str()` function is crucial here because it **converts the `score` (an integer) into a string**, allowing it to be concatenated (joined) with other strings. Python would otherwise show an error if you try to add a string and an integer directly.

The complete code for the Animal Quiz, excluding hacks and tweaks, can be found in the Project Reference section.

---

### Password Picker

This code imports necessary modules, defines lists of adjectives and nouns, and then enters an infinite loop to generate random passwords based on these lists, numbers, and punctuation.

```python
import random
import string

adjectives = ['sleepy', 'slow', 'smelly',
              'wet', 'fat', 'red',
              'orange', 'yellow', 'green',
              'blue', 'purple', 'fluffy',
              'white', 'proud', 'brave']
nouns = ['apple', 'dinosaur', 'ball',
         'toaster', 'goat', 'dragon',
         'hammer', 'duck', 'panda']

print('Welcome to Password Picker!')

while True:
    adjective = random.choice(adjectives)
    noun = random.choice(nouns)
    number = random.randrange(0, 100)
    special_char = random.choice(string.punctuation)

    password = adjective + noun + str(number) + special_char
    print('Your new password is: %s' % password)

    response = input('Would you like another password? Type y or n: ')
    if response == 'n':
        break

```

The Password Picker project is designed to create a tool that generates **secure, memorable passwords**. When the program runs, it produces a new password and displays it on the screen, allowing the user to request new passwords until they find one they like.

Here's a step-by-step explanation of the Password Picker code:

1. **Project Goal**
    - The aim is to create **strong passwords by combining words, numbers, and characters**. The program can generate "crazy, hard-to-forget passwords, such as 'fluffyapple14(' or 'smellygoat&' ".
2. **How it Works (Overview)**
    - The project utilizes **Python's `random` module**.
    - The program "uses **random choices from groups of adjectives, nouns, numbers, and punctuation characters** to assemble each password".
    - The process is summarized by a flowchart: Choose a random adjective, noun, number (between 0 and 99), and punctuation character, then create and display the secure password. The user is then asked if they want another password, and the steps repeat if 'Y' is chosen, ending if 'N' is chosen.
3. **Step-by-Step Code Explanation**
    - **1. Create a New File**: Begin by opening IDLE and creating a new file, saving it as `"password_picker.py"`.
    - **2. Add the Modules**:
        - `import random`: This line imports the `random` module, which is essential for making random selections.
        - `import string`: This line imports the `string` module, which provides useful tools for working with strings, including a constant that holds punctuation characters. These lines are typed at the very top of the file.
    - **3. Welcome the User**:
        - `print('Welcome to Password Picker!')`: This displays a welcome message to the user, which is the first thing they see.
    - **4. Make an Adjective List**:
        - `adjectives = ['sleepy', 'slow', 'smelly', 'wet', 'fat', 'red', 'orange', 'yellow', 'green', 'blue', 'purple', 'fluffy', 'white', 'proud', 'brave']`: This code creates a **list** named `adjectives` that stores a collection of describing words. Each item in the list is a string and is separated by commas, all enclosed within square brackets `[]`. This list is placed between the `print()` command and the `import` statements.
    - **5. Make a Noun List**:
        - `nouns = ['apple', 'dinosaur', 'ball', 'toaster', 'goat', 'dragon', 'hammer', 'duck', 'panda']`: Similar to the adjective list, this creates a list named `nouns` to store names of things. It follows the adjective list.
    - **6. Start the Password Generation Loop**:
        - `while True:`: This creates an **infinite loop**. The code inside this loop will repeatedly generate new passwords until the user explicitly tells it to stop.
    - **7. Pick the Words (inside the loop)**:
        - `adjective = random.choice(adjectives)`: The `random.choice()` function selects a **random item** from the `adjectives` list and stores it in the `adjective` variable.
        - `noun = random.choice(nouns)`: Similarly, a random noun is selected from the `nouns` list.
    - **8. Select a Number (inside the loop)**:
        - `number = random.randrange(0, 100)`: The `random.randrange(0, 100)` function selects a **random whole number between 0 and 99** (inclusive of 0, exclusive of 100).
    - **9. Select a Special Character (inside the loop)**:
        - `special_char = random.choice(string.punctuation)`: This line uses `random.choice()` again, but this time it selects a random character from the `string.punctuation` **constant**. This constant "holds a string of characters used for punctuation".
    - **10. Create the New Secure Password (inside the loop)**:
        - `password = adjective + noun + str(number) + special_char`: This line **assembles all the randomly chosen parts** into a single `password` string.
        - The `str(number)` function is crucial here, as it **converts the `number` (an integer) into a string**. This is necessary because Python will raise an error if you try to directly combine (concatenate) a string with an integer.
    - **11. Display the Password (inside the loop)**:
        - `print('Your new password is: %s' % password)`: This line displays the newly generated password to the user. The `%s` is a placeholder that will be replaced by the value of the `password` variable.
    - **12. Ask for Another Password (inside the loop)**:
        - `response = input('Would you like another password? Type y or n: ')`: This line prompts the user to decide if they want another password and stores their input (`'y'` or `'n'`) in the `response` variable.
    - **13. Exit the Loop (inside the loop)**:
        - `if response == 'n': break`: If the user types `'n'` (for no), the `break` statement is executed. This causes the `while True` loop to terminate, ending the program. If the response is anything other than 'n', the loop continues, generating a new password.

The code leverages concepts such as **variables** for storing data, **lists** for organized collections of items, **functions** for reusable blocks of code, and **`while` loops** for repetition, making it a concise yet powerful application. Indentation is critical in Python to define code blocks, especially within loops and functions.

---

### Nine Lives

This code sets up a word-guessing game where the player has nine lives. It uses a `update_clue` function to reveal correctly guessed letters and a main loop that continues until the word is guessed or lives run out.

```python
import random

lives = 9
words = ['pizza', 'fairy', 'teeth', 'shirt', 'otter', 'plane']
secret_word = random.choice(words)
clue = list('?????')
heart_symbol = u'\u2764'

guessed_word_correctly = False

def update_clue(guessed_letter, secret_word, clue):
    index = 0
    while index < len(secret_word):
        if guessed_letter == secret_word[index]:
            clue[index] = guessed_letter
        index = index + 1

while lives > 0:
    print(clue)
    print('Lives left: ' + heart_symbol * lives)
    guess = input('Guess a letter or the whole word: ')

    if guess == secret_word:
        guessed_word_correctly = True
        break

    if guess in secret_word:
        update_clue(guess, secret_word, clue)
    else:
        print('Incorrect. You lose a life')
        lives = lives - 1

if guessed_word_correctly:
    print('You won! The secret word was ' \
+ secret_word)
else:
    print('You lost! The secret word was ' \
+ secret_word)

```

The "Nine Lives" project is a **nerve-shredding game** where you guess a secret word one letter at a time. If your guess is wrong, you lose a life, and you only have nine lives in total. The game ends when you either correctly guess the word or run out of lives.

Here's a step-by-step explanation of the Python code for the "Nine Lives" game:

**I. Setting Up the Game**

1. **Create a new file**: You start by opening IDLE and creating a new file, saving it as "nine_lives.py".
2. **Import the `random` module**: This module is essential for the game, as it allows the program to randomly pick the secret word.
3. **Initialize `lives` variable**: A variable named `lives` is created and set to **9**, representing the player's starting number of guesses.
4. **Create the `words` list**: The program needs a list of words from which to choose the secret word. This list, named `words`, contains strings like 'pizza', 'fairy', 'teeth', 'shirt', 'otter', and 'plane'.
    - **Caution**: The source advises using words that are **five letters long**, as the `clue` list (explained next) is initially set up for five characters. Using longer words will cause an error when the program tries to insert letters beyond the fifth position, while shorter words will leave extra question marks.
5. **Choose a `secret_word`**: The `random.choice()` function is used to randomly select one word from the `words` list, and this chosen word is stored in the `secret_word` variable.
6. **Store the `clue` list**: An empty list to hold the clue is created, initially filled with question marks (`'?????'`). These question marks will be replaced by correct letters as the player guesses them.
7. **Store the `heart_symbol`**: To display the remaining lives, the Unicode heart character (`u'\u2764'`) is stored in the `heart_symbol` variable, making the display easier to read and write.
8. **Set `guessed_word_correctly` flag**: A **Boolean variable** `guessed_word_correctly` is created and initialized to `False`. This variable tracks whether the player has guessed the word correctly, and it will be set to `True` if they win.

**II. The Main Code Logic**

The main part of the game involves a loop that continually gets guesses from the player and checks them against the `secret_word`.

1. **Define `update_clue()` function**:
    - This function is defined with three parameters: `guessed_letter`, `secret_word`, and `clue`.
    - It contains a `while` loop that iterates through each letter of the `secret_word` using an `index` variable.
    - If the `guessed_letter` matches a letter at a specific `index` in the `secret_word`, that position in the `clue` list is updated with the `guessed_letter`.
    - This ensures that if a letter appears multiple times in the `secret_word`, all instances are revealed.
2. **Main Game Loop (`while lives > 0`)**:
    - This `while` loop continues as long as the player has lives remaining.
    - Inside the loop:
        - The current `clue` (e.g., `['?', '?', '?', '?', '?']`) and the number of `Lives left:` (displayed using the `heart_symbol` repeated by the `lives` count, e.g., "Lives left: ❤️❤️❤️❤️❤️❤️❤️❤️❤️") are printed to the shell.
        - The program prompts the user to `Guess a letter or the whole word:` and stores their input in the `guess` variable.
        - **Check if the whole word is guessed**: An `if` statement checks if the player's `guess` exactly matches the `secret_word`.
            - If it matches, `guessed_word_correctly` is set to `True`, and a `break` statement immediately exits the `while` loop, ending the game.
        - **Check if the guessed letter is in the secret word**: If the whole word wasn't guessed, an `if` statement checks if the `guess` (which is assumed to be a single letter at this point) is present within the `secret_word`.
            - If it is, the `update_clue()` function is called, passing the `guess`, `secret_word`, and `clue` to reveal the correct letter(s) in the clue.
        - **Handle incorrect guesses**: If the `guess` is not in the `secret_word` (handled by the `else` block):
            - A message "Incorrect. You lose a life" is printed.
            - The `lives` variable is **decremented by 1** (`lives = lives - 1`).
3. **Determine Win/Loss**:
    - After the main `while` loop ends (either by guessing correctly or running out of lives), an `if` statement checks the value of `guessed_word_correctly`.
    - If `guessed_word_correctly` is `True`, the program prints a "You won!" message along with the `secret_word`.
    - Otherwise (`else`), it means the player ran out of lives, and the program prints a "You lost!" message, also revealing the `secret_word`.

The source also suggests **hacks and tweaks** to customize the game, such as adding more words, changing word length, or altering the number of lives to adjust difficulty.

---

### Robot Builder

This code uses the Turtle module to draw a robot piece by piece. It defines a `rectangle` function to draw different parts of the robot using specific dimensions and colors.

```python
import turtle as t

def rectangle(horizontal, vertical, color):
    t.pendown()
    t.pensize(1)
    t.color(color)
    t.begin_fill()
    for counter in range(1, 3):
        t.forward(horizontal)
        t.right(90)
        t.forward(vertical)
        t.right(90)
    t.end_fill()
    t.penup()

t.penup()
t.speed('slow')
t.bgcolor('Dodger blue')

# feet
t.goto(-100, -150)
rectangle(50, 20, 'blue')
t.goto(-30, -150)
rectangle(50, 20, 'blue')

# legs
t.goto(-25, -50)
rectangle(15, 100, 'grey')
t.goto(-55, -50)
rectangle(-15, 100, 'grey')

# body
t.goto(-90, 100)
rectangle(100, 150, 'red')

# arms
t.goto(-150, 70)
rectangle(60, 15, 'grey')
t.goto(-150, 110)
rectangle(15, 40, 'grey')
t.goto(10, 70)
rectangle(60, 15, 'grey')
t.goto(55, 110)
rectangle(15, 40, 'grey')

# neck
t.goto(-50, 120)
rectangle(15, 20, 'grey')

# head
t.goto(-85, 170)
rectangle(80, 50, 'red')

# eyes
t.goto(-60, 160)
rectangle(30, 10, 'white')
t.goto(-55, 155)
rectangle(5, 5, 'black')
t.goto(-40, 155)
rectangle(5, 5, 'black')

# mouth
t.goto(-65, 135)
rectangle(40, 5, 'black')

t.hideturtle()

```

The "Robot Builder" project in Python allows you to program a robot "turtle" to draw pictures on the screen, specifically a friendly robot, using the `turtle` module.

Here's a step-by-step explanation of the Python code for the "Robot Builder" project:

**I. What Happens and How it Works**

When you run the "Robot Builder" program, Python's turtle scurries around the screen, drawing a friendly robot piece by piece using different colors. You can customize the robot's appearance by altering the size of its body parts and its color scheme.

The core mechanism involves **writing a function that draws rectangles**. These rectangles are then assembled to build the robot. The `turtle` module allows you to control a pen-carrying robot turtle, providing instructions for its movement to draw various pictures and designs. You can also tell the turtle when to put its pen down to draw and when to pull it up to move without leaving a trail. The program starts by setting the background color and the turtle's speed, then draws the robot part by part, from its feet to its head.

**II. Drawing Rectangles (Initial Setup)**

1. **Create a New File**: Begin by opening IDLE and creating a new file, saving it as "robot_builder.py".
2. **Import the Turtle Module**: At the top of your program, you need to import the `turtle` module. The command `import turtle as t` is used, which allows you to use functions from the `turtle` module by typing `t.` instead of `turtle.` each time.
3. **Create a Rectangle Function**: Define a function named `rectangle` that will draw the basic building blocks of your robot.
    - This function takes three **parameters**: `horizontal` (length of the horizontal side), `vertical` (length of the vertical side), and `color`.
    - **`t.pendown()`**: This command puts the turtle's pen down, so it starts drawing.
    - **`t.pensize(1)`**: Sets the thickness of the pen to 1 pixel.
    - **`t.color(color)`**: Sets the color of the pen (and subsequently the fill color) to the `color` parameter passed to the function. Python uses the US spelling "color".
    - **`t.begin_fill()`**: Tells the turtle to start filling the shape it draws with the chosen color.
    - **`for counter in range(1, 3):`**: This is a `for` loop that runs twice. Inside this loop, the turtle draws one horizontal and one vertical side.
        - **`t.forward(horizontal)`**: Moves the turtle forward by the `horizontal` length.
        - **`t.right(90)`**: Turns the turtle 90 degrees to the right.
        - **`t.forward(vertical)`**: Moves the turtle forward by the `vertical` length.
        - **`t.right(90)`**: Turns the turtle 90 degrees to the right again.
    - **`t.end_fill()`**: Stops filling the shape with color.
    - **`t.penup()`**: Lifts the turtle's pen, so it can move to a new position without drawing.
    - **`t.shape('turtle')`**: Changes the turtle's default arrowhead shape to a turtle shape.
    - **`t.setheading(0)`**: Sets the turtle's initial direction (heading) to 0, which means it will face right. Other headings include 90 (up), 180 (left), and 270 (down).
    - **`t.forward(80)`**: Moves the turtle forward 80 units.

**III. Building the Robot (Main Drawing Logic)**

The robot is built piece by piece, starting from the feet and moving upwards. All parts are drawn using rectangles of different sizes and colors, from specific starting points in the Turtle window. Python uses coordinates (x, y) to identify positions in the window, with (0,0) as the center.

1. **Set the Background**:
    - **`t.penup()`**: Ensures the turtle doesn't draw lines before the robot's feet are drawn.
    - **`t.speed('slow')`**: Controls how fast the turtle draws. Other options include 'slowest', 'normal', 'fast', and 'fastest'.
    - **`t.bgcolor('Dodger blue')`**: Sets the background color of the drawing window to "Dodger blue".
2. **Draw the Feet**:
    - **`t.goto(-100, -150)`**: Moves the turtle to the starting x and y coordinates for the first foot.
    - **`rectangle(50, 20, 'blue')`**: Calls the `rectangle` function to draw a blue rectangle 50 units wide and 20 units high for the first foot.
    - **`t.goto(-30, -150)`** and **`rectangle(50, 20, 'blue')`**: Repeats the process for the second foot.
    - **Comments (`# feet`)**: Lines starting with `#` are comments that make the code easier to read and are ignored by Python.
3. **Draw the Legs**:
    - **`t.goto(-25, -50)`** and **`rectangle(15, 100, 'grey')`**: Draws the right leg.
    - **`t.goto(-55, -50)`** and **`rectangle(-15, 100, 'grey')`**: Draws the left leg. The negative width causes it to be drawn in the opposite direction.
4. **Draw the Arms**: Each arm is drawn in two parts: upper and lower.
    - **`t.goto(-150, 70)`** and **`rectangle(60, 15, 'grey')`**: Draws the upper left arm.
    - **`t.goto(-150, 110)`** and **`rectangle(15, 40, 'grey')`**: Draws the lower left arm.
    - Similar `t.goto` and `rectangle` calls are used for the upper and lower right arms.
5. **Draw the Body**:
    - **`t.goto(-90, 100)`** and **`rectangle(100, 150, 'red')`**: Draws the main body of the robot.
6. **Draw the Neck**:
    - **`t.goto(-50, 120)`** and **`rectangle(15, 20, 'grey')`**: Draws the neck.
7. **Draw the Head**:
    - **`t.goto(-85, 170)`** and **`rectangle(80, 50, 'red')`**: Draws the head.
8. **Draw the Eyes**: Draws a large white rectangle for the eyes and two smaller black squares for the pupils.
    - **`t.goto(-60, 160)`** and **`rectangle(30, 10, 'white')`**: Draws the white part of the eyes.
    - **`t.goto(-55, 155)`** and **`rectangle(5, 5, 'black')`**: Draws the left pupil (a square is a rectangle with equal sides).
    - **`t.goto(-40, 155)`** and **`rectangle(5, 5, 'black')`**: Draws the right pupil.
9. **Draw the Mouth**:
    - **`t.goto(-65, 135)`** and **`rectangle(40, 5, 'black')`**: Draws the mouth.
10. **Hide the Turtle**:
    - **`t.hideturtle()`**: Makes the turtle invisible so it doesn't obstruct the view of the completed robot.

**IV. Hacks and Tweaks**

The sources suggest several ways to customize the robot after building it:

- **Change Colors**: Modify the `color` parameters in the `rectangle` function calls to change the robot's color scheme.
- **Change the Face**: Rearrange the eyes and mouth coordinates to give the robot different expressions, such as "wonky eyes and mouth".
- **Add Hands**: Add U-shaped gripping hands, hooks, or pincers using the `rectangle` function.
- **All-in-one Arms Function**: Create a new function that draws an entire arm at once to make it easier to change arm positions or add more arms.
- **Trial and Error / Coordinates**: Use `print(t.window_width())` and `print(t.window_height())` to get window dimensions and graph paper to plan coordinates for new body parts.

This step-by-step breakdown covers the creation and customization of the "Robot Builder" project based on the provided source material.

---

### Kaleido-spiral

This code uses the Turtle module and recursion to draw a colorful, shifting spiral pattern. It cycles through a list of colors and incrementally changes the size, angle, and shift of each drawn circle.

```python
import turtle
from itertools import cycle

colors = cycle(['red', 'orange', 'yellow', \
                'green', 'blue', 'purple'])

def draw_circle(size, angle, shift):
    turtle.pencolor(next(colors))
    turtle.circle(size)
    turtle.right(angle)
    turtle.forward(shift)
    draw_circle(size + 5, angle + 1, shift + 1)

turtle.bgcolor('black')
turtle.speed('fast')
turtle.pensize(4)
draw_circle(30, 0, 1)

```

The "Kaleido-spiral" project in Python uses the `turtle` module to draw intricate, colorful spiral patterns on the screen. When you run the program, the Python turtle draws circles one after another, continually shifting their position, angle, color, and size to form a snaking spiral from the center. The longer the program runs, the more complex and mind-boggling the pattern becomes.

Here's a step-by-step explanation of the Kaleido-spiral Python code:

**I. What Happens and How it Works**

The program utilizes the `turtle` module and a **recursive looping technique** to layer circles on top of each other in a spiral pattern. Each new circle drawn is slightly different from the last because the program incrementally increases the parameters of the circle-drawing code. The turtle module allows you to control a pen-carrying robot turtle, giving it instructions to move and draw. The program sets fixed values for the turtle's speed, background color, and pen size, then enters a loop that continually selects a new pen color, draws a circle, rotates and moves the turtle, and repeats until the program is quit.

**II. Getting Started and Initial Setup**

1. **Create a New File**: You begin by opening IDLE (Integrated Development Environment) and creating a new file, saving it as "kaleido-spiral.py". IDLE is a free application included when you install Python, designed for beginners to write and edit Python code.
2. **Import the Turtle Module**: At the top of your program, you need to `import turtle`. This loads the entire `turtle` module, which is the main module used for this project. Additionally, `from itertools import cycle` is imported, which allows the program to cycle through a list of different colors endlessly for vibrant patterns.
3. **Set Up the Turtle**: The program then calls functions from the `turtle` module to configure the drawing environment:
    - `turtle.bgcolor('black')`: Sets the **background color** of the drawing window to black.
    - `turtle.speed('fast')`: Controls the **drawing speed** of the turtle. Other options include 'slowest', 'slow', 'normal', and 'fastest'.
    - `turtle.pensize(4)`: Sets the **thickness of the turtle's pen** (trail) to 4 pixels.

**III. Drawing the Circles and Recursion**

1. **Define Colors Cycle**: A `colors` variable is created using `cycle(['red', 'orange', 'yellow', 'green', 'blue', 'purple'])`. This line sets up a sequence of colors that the turtle will cycle through repeatedly when drawing.
2. **Create `draw_circle` Function**: A function named `draw_circle` is defined. This function is crucial as it contains the logic for drawing each individual circle and for the recursive process.
    - It takes three **parameters**: `size`, `angle`, and `shift`.
    - `turtle.pencolor(next(colors))`: Sets the **pen color** to the next color in the `colors` cycle.
    - `turtle.circle(size)`: Instructs the turtle to draw a circle with the specified `size` (radius or diameter depending on the turtle implementation, but typically radius).
    - `turtle.right(angle)`: Turns the turtle `angle` degrees to the right (clockwise).
    - `turtle.forward(shift)`: Moves the turtle forward by the `shift` amount.
    - `draw_circle(size + 5, angle + 1, shift + 1)`: This is where **recursion** happens. The function calls itself, but with updated parameters:
        - The `size` for the next circle is increased by 5.
        - The `angle` for the next turn is increased by 1 degree.
        - The `shift` for the next forward movement is increased by 1 unit.
        This continuous change in parameters with each recursive call creates the evolving spiral pattern.

**IV. Starting the Drawing Process**

1. **Initial Function Call**: After defining the `draw_circle` function and setting up the turtle, the program makes its initial call to `draw_circle(30, 0, 1)`.
    - This starts the drawing with an initial circle size of 30 units.
    - The initial turning angle is 0 degrees.
    - The initial forward movement (shift) is 1 unit.
2. **Continuous Drawing**: Because the `draw_circle` function calls itself with modified parameters, the turtle will continue to draw circles, turn, and move, creating the "shifting spiral" effect indefinitely until the program is manually stopped.

**V. Hacks and Tweaks (Customization)**

The sources suggest several ways to modify and enhance the Kaleido-spiral:

- **Change Pen Size**: You can modify `turtle.pensize(4)` to a different value, such as `turtle.pensize(40)`, to make the circles chunkier.
- **Find New Patterns**: The appearance of the pattern is determined by how much you add to the function's parameters (`size`, `angle`, `shift`) each time `draw_circle` is called. Experiment with different increments (e.g., `size + 10`, `angle + 10`, `shift + 1`) to create varied designs.
- **Crazy Colors (Changing Background Color)**: You can make the background color change with each loop, in addition to the pen color, by moving `turtle.bgcolor(next(colors))` inside the `draw_circle` function.
- **Shapeshifting (Adding Other Shapes)**: The program can be modified to draw shapes other than circles, such as squares, by adding a new parameter `shape` to the `draw_circle` function (renamed `draw_shape`) and using `if`/`elif` statements to alternate between drawing circles and squares. This involves using a `for` loop to draw the sides of a square.

---

### Starry Night

This program uses the Turtle module to draw stars of varying sizes, shapes, colors, and positions across the screen using random values.

```python
import turtle as t
from random import randint, random

def draw_star(points, size, col, x, y):
    t.penup()
    t.goto(x, y)
    t.pendown()
    angle = 180 - (180 / points)
    t.color(col)
    t.begin_fill()
    for i in range(points):
        t.forward(size)
        t.right(angle)
    t.end_fill()

# Main code
t.Screen().bgcolor('dark blue')

while True:
    ranPts = randint(2, 5) * 2 + 1
    ranSize = randint(10, 50)
    ranCol = (random(), random(), random())
    ranX = randint(-350, 300)
    ranY = randint(-250, 250)
    draw_star(ranPts, ranSize, ranCol, ranX, ranY)

```

The "Starry Night" project in Python utilizes the `turtle` module to draw vibrant star shapes across the screen, simulating a starry sky. The program generates these stars at random locations with varying colors, sizes, and shapes. The longer the program runs, the more intricate and colorful the sky becomes.

Here's a step-by-step explanation of the "Starry Night" Python code:

**I. What Happens and How it Works**

When you run the "Starry Night" program, a nighttime sky is first drawn, followed by a single star appearing. The sky then progressively fills with more stars of various styles. The program uses the `turtle` module to draw star shapes at random locations within a Turtle Graphics window. It defines a function to draw a single star and then employs an **infinite loop** to repeatedly draw many different stars across the screen.

**II. Drawing a Single Star (Initial Setup)**

1. **Create a New File and Import Turtle**:
    - You begin by opening IDLE and creating a new file, saving it as "starry_night.py".
    - The first line of code is `import turtle as t`. This **imports the `turtle` module** and assigns it the shorter alias `t`, making it easier to call turtle functions later.
2. **Define Star Properties**:
    - Initially, the code sets variables for the **size** and **number of points** of the star, for example, `size = 300` and `points = 5`.
    - An `angle` variable is defined to calculate the turn the turtle needs to make for each point of the star: `angle = 180 - (180 / points)`. This allows the program to **draw stars with different numbers of points**. The source notes that this calculation works best for stars with **odd numbers of points**.
3. **Draw the Star's Lines**:
    - A `for` loop is used to instruct the turtle to draw the star. For each point of the star, the turtle moves forward by the `size` amount and then turns right by the calculated `angle`: `for i in range(points): t.forward(size); t.right(angle)`.
4. **Color the Star**:
    - To make the star more appealing, the code sets its color and then fills it.
    - `t.color('yellow')` sets the **pen color**.
    - `t.begin_fill()` tells the turtle to start filling the shape with color.
    - `t.end_fill()` is called after the `for` loop to **complete the color fill**.

**III. Creating the Starry Sky (Functions and Loops)**

1. **Define `draw_star` Function**:
    - To draw multiple stars, all the star-drawing instructions are wrapped into a function called `draw_star`.
    - This function takes **five parameters**: `points`, `size`, `col` (color), `x`, and `y` (coordinates for position).
    - Inside the function, `t.penup()` is called before moving to the star's `x` and `y` position (`t.goto(x, y)`) and `t.pendown()` is called to start drawing at that location. This ensures the turtle doesn't draw lines while moving to the starting point of a new star.
2. **Set Background and Initial Star Call**:
    - The main part of the code sets the background color of the screen to 'dark blue' using `t.Screen().bgcolor('dark blue')`.
    - An **initial call** is made to `draw_star(5, 50, 'yellow', 0, 0)` to draw a single yellow, five-pointed star of size 50 in the center of the window.
3. **Add Randomness**:
    - To make the stars varied, Python's `random` module is imported: `from random import randint, random`.
        - `randint()` is used to get a random integer within a range.
        - `random()` is used to get a random float between 0 and 1 (useful for RGB colors).
4. **Create an Infinite Loop for Continuous Drawing**:
    - A `while True:` loop is implemented to draw stars continuously until the program is manually stopped.
    - Inside this loop, parameters for each new star are **randomized**:
        - `ranPts = randint(2, 5) * 2 + 1`: This generates a random **odd number of points** for the star, between 5 and 11.
        - `ranSize = randint(10, 50)`: This sets a random **size** for the star between 10 and 50 units.
        - `ranCol = (random(), random(), random())`: This creates a **random color** using RGB values.
        - `ranX = randint(-350, 300)` and `ranY = randint(-250, 250)`: These choose random **x and y coordinates** for the star's position on the screen.
    - Finally, `draw_star(ranPts, ranSize, ranCol, ranX, ranY)` is called within the loop, using these newly randomized values to draw a unique star each time.
5. **Hide the Turtle**:
    - To prevent the turtle (which normally looks like a yellow arrowhead) from being visible on the screen, `t.hideturtle()` is called in the main code. This makes the stars appear as if drawn magically.

**IV. Customization (Hacks and Tweaks)**

The source provides several suggestions for modifying the "Starry Night" program:

- **Change Star Variation**: You can alter the numbers in the brackets of the `ranPts` and `ranSize` variables within the `while` loop to **control the range of points and sizes** of the stars.
- **Click for Stars**: Instead of random drawing, you can use the `turtle.onScreenClick()` function to draw a star **wherever the mouse is clicked**.
- **Speed Up/Down**: The turtle's drawing speed can be adjusted using `t.speed(0)` at the start of the main code, with `0` being the fastest.
- **Draw Planets**: By investigating the `turtle.circle()` function, you can add code to **draw planets** to your starry sky. You can even add rings around them.
- **Design Constellations**: You can create a list of (x, y) coordinates to design your own star patterns (constellations) and then use a `for` loop to draw stars at those specific locations.

---

### Mutant Rainbow

This code programs the Turtle to draw unpredictable, colorful lines by choosing random directions and colors. It includes functions for setting line length and width based on user input, and a mechanism to keep the turtle within the window.

```python
import random
import turtle as t

def get_line_length():
    choice = input('Enter line length (long, medium, short): ')
    if choice == 'long':
        line_length = 250
    elif choice == 'medium':
        line_length = 200
    else:
        line_length = 100
    return line_length

def get_line_width():
    choice = input('Enter line width (superthick, thick, thin): ')
    if choice == 'superthick':
        line_width = 40
    elif choice == 'thick':
        line_width = 25
    else:
        line_width = 10
    return line_width

def inside_window():
    left_limit = (-t.window_width() / 2) + 100
    right_limit = (t.window_width() / 2) - 100
    top_limit = (t.window_height() / 2) - 100
    bottom_limit = (-t.window_height() / 2) + 100
    (x, y) = t.pos()
    inside = left_limit < x < right_limit and bottom_limit < y < top_limit
    return inside

def move_turtle(line_length):
    pen_colors = ['red', 'orange', 'yellow', 'green', 'blue', 'purple']
    t.pencolor(random.choice(pen_colors))
    if inside_window():
        angle = random.randint(0, 180)
        t.right(angle)
        t.forward(line_length)
    else:
        t.backward(line_length)

line_length = get_line_length()
line_width = get_line_width()

t.shape('turtle')
t.fillcolor('green')
t.bgcolor('black')
t.speed('fastest')
t.pensize(line_width)

while True:
    move_turtle(line_length)

```

The Mutant Rainbow Python code programs Python's turtle to draw various patterns and designs by moving around the screen and painting colored lines. The program creates a display of colors where the type of pattern changes based on the length and thickness of the lines chosen.

Here is a step-by-step explanation of the Mutant Rainbow Python code:

- **Getting Started (Setting up the Environment and Core Functions)**
    - **Create a new file**: The first step is to open IDLE and save a new file as "rainbow.py".
    - **Import Modules**: You need to import the `random` module for random choices and the `turtle` module (aliased as `t` for brevity) to control the robot turtle.
    - **`get_line_length()` function**: This function prompts the user to "Enter line length (long, medium, short)".
        - If the user chooses 'long', `line_length` is set to 250.
        - If 'medium', `line_length` is 200.
        - Otherwise (for 'short'), it's 100.
        - The function then **returns** this `line_length` value.
    - **`get_line_width()` function**: Similar to the length function, this one asks the user to "Enter line width (superthick, thick, thin)".
        - 'superthick' sets `line_width` to 40.
        - 'thick' sets it to 25.
        - Otherwise (for 'thin'), it's 10.
        - This function also **returns** the `line_width` value.
    - **`inside_window()` function**: This function prevents the turtle from wandering off-screen.
        - It calculates the `left_limit`, `right_limit`, `top_limit`, and `bottom_limit` by taking the window's dimensions and subtracting/adding 100 pixels from the edges.
        - It gets the turtle's current `(x, y)` coordinates using `t.pos()`.
        - It then checks if the turtle's `x` coordinate is between the `left_limit` and `right_limit`, AND if its `y` coordinate is between the `bottom_limit` and `top_limit`.
        - It **returns** `True` if the turtle is inside the limits, `False` otherwise.
- **Summon the Turtle! (Initializing the Turtle and Getting User Input in the Main Program)**
    - **Get User Choices**: The main part of the program first calls `get_line_length()` and `get_line_width()` to get the user's preferences for the drawing.
    - **Configure Turtle**: It sets up the turtle's appearance and the drawing environment:
        - `t.shape('turtle')`: Changes the turtle's shape from an arrowhead to a turtle.
        - `t.fillcolor('green')`: Sets the turtle's fill color to green.
        - `t.bgcolor('black')`: Sets the background color of the window to black.
        - `t.speed('fastest')`: Sets the turtle's drawing speed to the fastest setting.
        - `t.pensize(line_width)`: Sets the thickness of the pen to the `line_width` chosen by the user.
- **Move that Turtle! (The Main Drawing Loop)**
    - **`move_turtle()` function**: This function contains the core logic for the turtle's movement and drawing.
        - **Random Pen Color**: It defines a list of `pen_colors` (red, orange, yellow, green, blue, purple) and randomly selects one for the pen using `random.choice(pen_colors)`.
        - **Boundary Check**: It calls `inside_window()` to determine if the turtle is within the defined boundaries.
        - **Movement Logic**:
            - **If `inside_window()` is `True`**: The turtle chooses a random `angle` between 0 and 180 degrees using `random.randint(0, 180)`, turns `t.right(angle)`, and moves `t.forward(line_length)`.
            - **If `inside_window()` is `False`**: The turtle `t.backward(line_length)` to move back into the window.
    - **Infinite Loop**: The program enters a `while True:` loop. Inside this loop, it continuously calls the `move_turtle(line_length)` function. This makes the turtle draw lines non-stop, creating the "mutant rainbow" effect.
    - **Start Main Loop**: The `root.mainloop()` command, located at the very end of the script (after obtaining user inputs and setting up the turtle), starts the Tkinter event loop, which manages all the drawing, user input, and timers, ensuring the program runs continuously.

---

### Countdown Calendar

This program creates a graphical user interface (GUI) to display a countdown to important events. It reads event information from an external text file (`events.txt`), calculates the days remaining using the `datetime` module, and displays them on a Tkinter canvas.

```python
from tkinter import Tk, Canvas
from datetime import date, datetime

def get_events():
    list_events = []
    with open('events.txt') as file:
        for line in file:
            line = line.rstrip('\n')
            current_event = line.split(',')
            event_date = datetime.strptime(current_event, '%d/%m/%y').date()
            current_event = event_date
            list_events.append(current_event)
    return list_events

def days_between_dates(date1, date2):
    time_between = str(date1 - date2)
    number_of_days = time_between.split(' ')
    return number_of_days

root = Tk()
c = Canvas(root, width=800, height=800, bg='black')
c.pack()
c.create_text(100, 50, anchor='w', fill='orange', font='Arial 28 bold underline', \
              text='My Countdown Calendar')

events = get_events()
today = date.today()

vertical_space = 100

for event in events:
    event_name = event
    days_until = days_between_dates(event, today)
    display = 'It is %s days until %s' % (days_until, event_name)
    c.create_text(100, vertical_space, anchor='w', fill='lightblue', \
                  font='Arial 28 bold', text=display)
    vertical_space = vertical_space + 30

```

The Python code for the Countdown Calendar project is designed to help you keep track of important future events by displaying a list of these events and showing how many days are left until each one. It leverages **Python's Tkinter module** for creating the graphical user interface (GUI) and the **datetime module** for date calculations. The event information itself is read from a separate text file.

Here's a step-by-step explanation of the Python code:

1. **Setting up the Event Data File (`events.txt`)**:
    - Before writing the Python code, you create a simple text file named `events.txt`.
    - In this file, you **list your upcoming events**, each on a separate line.
    - Each line should contain the **event name, followed by a comma, and then the date in `day/month/year` format (e.g., `Halloween,31/10/17`)**, ensuring no space between the comma and the date.
    - This `events.txt` file must be saved in the **same folder as your Python code** for the program to find it.
2. **Importing Necessary Modules**:
    - `from tkinter import Tk, Canvas`: This line imports specific components from the `tkinter` module. `Tk` is used to create the main window of the GUI, and `Canvas` provides a drawing area where text and graphics can be placed. Tkinter is a set of tools for displaying graphics and getting user input.
    - `from datetime import date, datetime`: This imports the `date` and `datetime` objects from the `datetime` module. This module is highly useful for calculations involving dates and time.
3. **`get_events()` Function Definition**:
    - `def get_events():`: This function is responsible for **reading the event details from `events.txt` and preparing them** for use in the program.
    - `list_events = []`: An **empty list** called `list_events` is initialized. This list will store all the processed event data.
    - `with open('events.txt') as file:`: This opens the `events.txt` file in **read mode**. The `with` statement ensures the file is automatically closed after its block of code is executed.
    - `for line in file:`: The code then **iterates through each line** in the opened `events.txt` file.
    - `line = line.rstrip('\n')`: Each line read from the file might have an invisible **newline character (`\n`)** at the end. `rstrip('\n')` removes this character to avoid issues with parsing.
    - `current_event = line.split(',')`: The `line` string (e.g., "Halloween,31/10/17") is **split into a list of strings** using the comma (`,`) as a separator. For example, "Halloween,31/10/17" becomes `['Halloween', '31/10/17']`. This result is stored in `current_event`.
    - `event_date = datetime.strptime(current_event, '%d/%m/%y').date()`: This is a crucial step for date handling.
        - `current_event` accesses the date string part (e.g., '31/10/17') from the `current_event` list (remember, list items are zero-indexed, so `` is the second item).
        - `datetime.strptime()` **converts this date string into a `datetime` object**, using the format `'%d/%m/%y'` (day/month/year) to correctly interpret the string.
        - `.date()` then converts the `datetime` object into a simpler `date` object, discarding any time information.
    - `current_event = event_date`: The original date string in the `current_event` list is **replaced with the newly created `date` object**.
    - `list_events.append(current_event)`: The `current_event` list (which now contains `[event_name, date_object]`) is **added to the `list_events`** list.
    - `return list_events`: After processing all lines, the function **returns the `list_events`** list, containing all event names and their corresponding `date` objects.
4. **`days_between_dates()` Function Definition**:
    - `def days_between_dates(date1, date2):`: This function calculates the **number of days between two `date` objects**.
    - `time_between = str(date1 – date2)`: When you subtract one `date` object from another, Python returns a `timedelta` object (e.g., "27 days, 0:00:00"). This line **converts the `timedelta` object into a string**.
    - `number_of_days = time_between.split(' ')`: This line **splits the `time_between` string** (e.g., "27 days, 0:00:00") into a list of strings using spaces as delimiters, resulting in `['27', 'days,', '0:00:00']`.
    - `return number_of_days`: The function then **returns the first element** of this list, which is the number of days (e.g., `'27'`), still as a string.
5. **GUI Setup (Main Program Execution)**:
    - `root = Tk()`: This creates the **main Tkinter window**, which serves as the top-level container for all other GUI elements.
    - `c = Canvas(root, width=800, height=800, bg='black')`: A **`Canvas` widget** named `c` is created inside the `root` window. It's set to be 800 pixels wide and 800 pixels high, with a black background. The `Canvas` is an area where shapes, graphics, text, or images can be placed.
    - `c.pack()`: This method is used to **organize and display the `canvas`** widget within the Tkinter window.
    - `c.create_text(100, 50, anchor='w', fill='orange', font='Arial 28 bold underline', text='My Countdown Calendar')`: This line adds the **main title text** "My Countdown Calendar" to the canvas.
        - `(100, 50)` are the x and y coordinates on the canvas where the text will start.
        - `anchor='w'` specifies that the text should be aligned to the **west (left)** of the given coordinates.
        - `fill='orange'` sets the color of the text.
        - `font='Arial 28 bold underline'` defines the **font family, size, weight (bold), and style (underline)**.
        - `text='My Countdown Calendar'` is the actual string content displayed.
6. **Event Processing and Display Loop**:
    - `events = get_events()`: This line **calls the `get_events()` function** (defined earlier) to retrieve the list of all events from `events.txt`. The returned list is stored in the `events` variable.
    - `today = date.today()`: This gets the **current date** from the `datetime` module and stores it in the `today` variable.
    - `vertical_space = 100`: A variable `vertical_space` is initialized to `100`. This will be used to **control the vertical positioning** of each event displayed on the canvas, ensuring they don't overlap.
    - `for event in events:`: This loop **iterates through each `event`** in the `events` list. Each `event` in this loop is itself a list like `[event_name_string, date_object]`.
    - `event_name = event`: The **name of the current event** is extracted (the first item in the `event` list).
    - `days_until = days_between_dates(event, today)`: The `days_between_dates()` function is called to **calculate the number of days between the event's date (`event`) and today's date (`today`)**. The result is stored in `days_until`.
    - `display = 'It is %s days until %s' % (days_until, event_name)`: This line creates a **formatted string** (e.g., "It is 20 days until Halloween") that will be displayed on the calendar. `%s` acts as a placeholder for strings.
    - `c.create_text(100, vertical_space, anchor='w', fill='lightblue', font='Arial 28 bold', text=display)`: This adds the formatted event string to the canvas.
        - `(100, vertical_space)` sets the position. The `vertical_space` variable ensures each event is drawn on a new line.
        - `fill='lightblue'` sets the text color for the event entries.
    - `vertical_space = vertical_space + 30`: After displaying each event, the `vertical_space` variable is **increased by 30 pixels**. This moves the starting position for the next event down, creating a neat vertical list.
7. **Running the Tkinter Main Loop**:
    - `root.mainloop()`: While not explicitly detailed in the step-by-step instructions for the code in the source, this line is **essential** for any Tkinter application. It starts the **Tkinter event loop**, which keeps the GUI window open and responsive to user interactions (like closing the window). Without `root.mainloop()`, the window would appear briefly and then close immediately.

In summary, the Countdown Calendar program combines **file input** to get event data, **date calculations** using the `datetime` module, and **graphical display** using Tkinter to present a user-friendly countdown to important dates.

---

### Ask the Expert

This program acts as an expert system for capital cities. It stores country-capital data in a text file and a Python dictionary, answers user queries, and can learn new facts from user input, saving them back to the text file.

```python
from tkinter import Tk, simpledialog, messagebox

def read_from_file():
    with open('capital_data.txt') as file:
        for line in file:
            line = line.rstrip('\n')
            country, city = line.split('/')
            the_world[country] = city

def write_to_file(country_name, city_name):
    with open('capital_data.txt', 'a') as file:
        file.write('\n' + country_name + '/' + city_name)

print('Ask the Expert – Capital Cities of the World')
root = Tk()
root.withdraw()
the_world = {}

read_from_file()

while True:
    query_country = simpledialog.askstring('Country', 'Type the name of a country:')

    if query_country in the_world:
        result = the_world[query_country]
        messagebox.showinfo('Answer',
                            'The capital city of ' + query_country + ' is ' + result + '!')
    else:
        new_city = simpledialog.askstring('Teach me',
                                          'I don\'t know! ' +
                                          'What is the capital city of ' + query_country + '?')
        the_world[query_country] = new_city
        write_to_file(query_country, new_city)

root.mainloop()

```

The "Ask the Expert" Python program is designed to act as a specialist on a particular topic, in this case, capital cities of the world. It can answer questions about capital cities and also learn new information from the user, becoming smarter over time.

Here's a step-by-step explanation of its Python code:

**1. Introduction and How it Works**

- The program uses **Tkinter** to create pop-up boxes for communication with the user.
- It stores information about countries and their capital cities in a **dictionary**.
- All its knowledge is initially loaded from a **text file**, and any new information learned is saved back into this file.
- The program uses an **infinite loop** to continually ask questions until the user quits.

**2. Initial Setup (First Steps)**

1. **Prepare the Text File (`capital_data.txt`)**:
    - You first create a text file (e.g., "capital_data.txt") where each line contains a country and its capital city, separated by a forward slash (/). For example, `India/New Delhi`.
    - This file serves as the program's initial knowledge base.
2. **Create the Python File (`ask_expert.py`)**:
    - A new Python file is created and saved in the same folder as `capital_data.txt`.
3. **Import Tkinter Tools**:
    - The program imports specific widgets from the Tkinter module: `Tk`, `simpledialog`, and `messagebox`.
    - **`Tk`** is used to create the main Tkinter window.
    - **`simpledialog.askstring()`** creates pop-up boxes that ask the user for text input.
    - **`messagebox.showinfo()`** displays information to the user in a pop-up box with an "OK" button.
4. **Start Tkinter and Hide Window**:
    - `root = Tk()` initializes Tkinter and creates a main window.
    - `root.withdraw()` is used to **hide this main Tkinter window**, as it's not needed for this program's interface, which relies solely on pop-up dialogs.
5. **Set Up a Dictionary (`the_world`)**:
    - `the_world = {}` creates an **empty dictionary**. This dictionary will store the country-capital city pairs, where the country name will be the "key" and the capital city will be its "value".

**3. Functions for File Handling**

1. **`read_from_file()` Function**:
    - This function is responsible for **reading all the information** from `capital_data.txt` and populating the `the_world` dictionary.
    - It opens `capital_data.txt` for reading (`with open('capital_data.txt') as file:`).
    - It then loops through each `line` in the file (`for line in file:`).
    - **`line = line.rstrip('\n')`**: This is crucial because when information is typed into a text file and the Enter/Return key is pressed, an **invisible "newline" character (`\n`)** is added at the end of each line. `rstrip('\n')` removes this character to prevent errors when processing the string.
    - **`country, city = line.split('/')`**: This line splits each `line` string at the forward slash (`/`) and assigns the two resulting parts to the `country` and `city` variables respectively.
    - **`the_world[country] = city`**: This adds the `country` as a key and `city` as its corresponding value to `the_world` dictionary.
2. **`write_to_file(country_name, city_name)` Function**:
    - This function **adds new country-capital city pairs** to the `capital_data.txt` file, effectively updating the program's knowledge.
    - It opens `capital_data.txt` in **append mode (`'a'`)** (`with open('capital_data.txt', 'a') as file:`). The `'a'` mode means new information will be added to the end of the file.
    - **`file.write('\n' + country_name + '/' + city_name)`**: This line writes a new entry to the file. It starts with a newline character (`\n`) to ensure the new entry begins on a fresh line, followed by the `country_name`, a slash, and the `city_name`. Python automatically closes the file after the `with` block.

**4. Main Program Logic**

1. **Load Initial Data**:
    - `read_from_file()` is called once at the beginning of the program to load all existing capital cities from the text file into the `the_world` dictionary.
2. **Infinite Loop for User Interaction**:
    - **`while True:`**: This creates an **infinite loop**, meaning the program will continuously run and interact with the user until explicitly stopped (e.g., by closing the program window or pressing Ctrl-C).
    - **`query_country = simpledialog.askstring('Country', 'Type the name of a country:')`**: Inside the loop, this line prompts the user to enter a country name using a pop-up dialog box titled 'Country'. The user's input is stored in `query_country`.
3. **Check for Known Answer**:
    - **`if query_country in the_world:`**: This `if` statement checks if the `query_country` entered by the user exists as a key in `the_world` dictionary.
        - **If True (Answer Known)**:
            - `result = the_world[query_country]` retrieves the capital city (value) associated with the `query_country` (key) from the dictionary.
            - `messagebox.showinfo('Answer', 'The capital city of ' + query_country + ' is ' + result + '!')` displays the answer in another pop-up info box.
        - **If False (Answer Unknown)**:
            - **`else:`**: If the country is not found in the dictionary, the program enters this block.
            - **`new_city = simpledialog.askstring('Teach me', 'I don\'t know! ' + 'What is the capital city of ' + query_country + '?')`**: A new pop-up asks the user to "teach" the program the capital city for the unknown country.
            - **`the_world[query_country] = new_city`**: The newly provided capital city (`new_city`) is added to the `the_world` dictionary, with `query_country` as its key.
            - **`write_to_file(query_country, new_city)`**: The `write_to_file` function is called to save this new information permanently to `capital_data.txt`, so the program remembers it for future runs.
4. **`root.mainloop()`**:
    - This line, typically placed at the very end of a Tkinter program, starts the **Tkinter event loop**. This loop continuously listens for events (like mouse clicks or key presses) and keeps the Tkinter windows active and responsive. For "Ask the Expert," it ensures the pop-up dialogs remain functional.

In essence, the "Ask the Expert" program demonstrates how to build a simple interactive application that can store and retrieve data using Python dictionaries and text files, all facilitated by Tkinter for user interaction.

---

### Secret Messages

This program encrypts and decrypts messages by rearranging letters based on their even or odd positions. It handles messages with odd lengths by adding an 'x' and uses Tkinter for user interaction.

```python
from tkinter import messagebox, simpledialog, Tk

def is_even(number):
    return number % 2 == 0

def get_even_letters(message):
    even_letters = []
    for counter in range(0, len(message)):
        if is_even(counter):
            even_letters.append(message[counter])
    return even_letters

def get_odd_letters(message):
    odd_letters = []
    for counter in range(0, len(message)):
        if not is_even(counter):
            odd_letters.append(message[counter])
    return odd_letters

def swap_letters(message):
    letter_list = []
    if not is_even(len(message)):
        message = message + 'x'
    even_letters = get_even_letters(message)
    odd_letters = get_odd_letters(message)
    for counter in range(0, int(len(message)/2)):
        letter_list.append(odd_letters[counter])
        letter_list.append(even_letters[counter])
    new_message = ''.join(letter_list)
    return new_message

def get_task():
    task = simpledialog.askstring('Task', 'Do you want to encrypt or decrypt?')
    return task

def get_message():
    message = simpledialog.askstring('Message', 'Enter the secret message: ')
    return message

root = Tk()

while True:
    task = get_task()
    if task == 'encrypt':
        message = get_message()
        encrypted = swap_letters(message)
        messagebox.showinfo('Ciphertext of the secret message is:', encrypted)
    elif task == 'decrypt':
        message = get_message()
        decrypted = swap_letters(message)
        messagebox.showinfo('Plaintext of the secret message is:', decrypted)
    else:
        break
root.mainloop()

```

The "Secret Messages" Python project allows users to **encrypt** and **decrypt** messages, essentially changing the text to hide its meaning. It works by rearranging the order of letters in a message, making it appear as "gibberish". The same process can then be reversed to make the encrypted message readable again.

Here's a step-by-step explanation of the Python code for the "Secret Messages" project:

**1. Project Overview**

- **What it does**: The program asks the user if they want to create a secret message or reveal an existing one. Based on the choice, it encrypts or decrypts the message typed by the user.
- **How it works**: The core mechanism involves **rearranging the order of letters** in the message. It identifies letters in even and odd positions and then swaps their positions. For example, in "secret", the program considers the first letter (s) to be in an even position (0 in Python's counting). The program also ensures the message has an **even number of characters**, adding an 'x' if necessary.
- **Tools used**: The project utilizes the **Tkinter module** to create interactive pop-up boxes for communication (dialogue boxes for input and info boxes for displaying results).

**2. Making the Graphical User Interface (GUI)**

This section sets up the visual part of the program that interacts with the user.

1. **Import Modules**:
    - `from tkinter import messagebox, simpledialog, Tk`.
    - This line imports the necessary tools from the Tkinter library:
        - `messagebox`: For displaying information or results in pop-up boxes.
        - `simpledialog`: For creating pop-up boxes that ask the user for text input.
        - `Tk`: The main Tkinter window (though often hidden for dialog-based apps).
2. **Define `get_task()` Function**:
    - `def get_task():`
    - `task = simpledialog.askstring('Task', 'Do you want to encrypt or decrypt?')`
    - `return task`
    - This function uses `simpledialog.askstring()` to display a pop-up box titled 'Task'. It asks the user whether they want to "encrypt" or "decrypt" a message. The user's input is stored in the `task` variable and then returned.
3. **Define `get_message()` Function**:
    - `def get_message():`
    - `message = simpledialog.askstring('Message', 'Enter the secret message: ')`
    - `return message`
    - Similar to `get_task()`, this function uses `simpledialog.askstring()` to prompt the user to "Enter the secret message". The entered message is stored in the `message` variable and returned.
4. **Initialize Tkinter Root Window**:
    - `root = Tk()`
    - `root.mainloop()`
    - `root = Tk()` initializes the Tkinter environment. The `root.mainloop()` line at the very end of the script starts the Tkinter event loop, which continuously listens for user interactions and keeps the GUI running.
    - *(Note: The source mentions `root.withdraw()` to hide the main Tkinter window as used in "Ask the Expert," but it's not present in the provided "Secret Messages" code snippet. Without it, a blank Tkinter window might appear in addition to the dialogs)*.

**3. Scrambling the Message (Core Logic)**

This section contains the functions responsible for the encryption and decryption process.

1. **Define `is_even(number)` Function**:
    - `def is_even(number):`
    - `return number % 2 == 0`
    - This function determines if a given `number` is even. It uses the **modulo operator (`%`)** which returns the remainder of a division. If `number % 2` is `0`, it means the number is perfectly divisible by 2, and thus, it's even. The function returns `True` or `False`.
2. **Define `get_even_letters(message)` Function**:
    - `def get_even_letters(message):`
    - `even_letters = []`
    - `for counter in range(0, len(message)):`
    - `if is_even(counter):`
    - `even_letters.append(message[counter])`
    - `return even_letters`
    - This function iterates through each character of the `message` using a `for` loop and a `counter`. It calls `is_even()` to check if the `counter` (which represents the letter's position, starting from 0) is an even number. If it is, the letter at that position (`message[counter]`) is added to the `even_letters` list. Finally, the list of even-positioned letters is returned.
3. **Define `get_odd_letters(message)` Function**:
    - `def get_odd_letters(message):`
    - `odd_letters = []`
    - `for counter in range(0, len(message)):`
    - `if not is_even(counter):`
    - `odd_letters.append(message[counter])`
    - `return odd_letters`
    - This function is similar to `get_even_letters()`, but it appends characters to the `odd_letters` list if their `counter` (position) is *not* even (i.e., it's odd).
4. **Define `swap_letters(message)` Function**:
    - `def swap_letters(message):`
    - `letter_list = []`
    - **Handle Odd Length**:
        - `if not is_even(len(message)):`
        - `message = message + 'x'`
        - This ensures the message always has an **even number of characters** before swapping. If the length of the `message` is odd, an 'x' is appended to it.
    - **Get Even/Odd Letter Lists**:
        - `even_letters = get_even_letters(message)`
        - `odd_letters = get_odd_letters(message)`
        - It calls the previously defined functions to get separate lists of letters from even and odd positions.
    - **Perform Swapping**:
        - `for counter in range(0, int(len(message)/2)):`
        - `letter_list.append(odd_letters[counter])`
        - `letter_list.append(even_letters[counter])`
        - A `for` loop iterates half the length of the message. In each iteration, it **alternately appends an odd-positioned letter then an even-positioned letter** to `letter_list`. This effectively swaps their original positions.
        - *(Expert Tip: The `int()` function is used with `len(message)/2` because division often results in a float, and list ranges require integers.)*
    - **Join and Return**:
        - `new_message = ''.join(letter_list)`
        - `return new_message`
        - The `join()` function concatenates all the characters in `letter_list` into a single string, forming the new (encrypted or decrypted) message, which is then returned.
        - *(Crucially, this `swap_letters()` function is **symmetric**: applying it once encrypts, applying it again decrypts.)*

**4. Main Program Loop**

This part orchestrates the user interaction and uses the functions defined above.

1. **Infinite Loop**:
    - `while True:`
    - This creates an **infinite loop**, meaning the program will continuously run and interact with the user until the `break` statement is encountered.
2. **Get Task from User**:
    - `task = get_task()`
    - The program first asks the user if they want to encrypt or decrypt, using the `get_task()` function.
3. **Conditional Logic (Encrypt/Decrypt/Quit)**:
    - `if task == 'encrypt':`
        - `message = get_message()`
        - `encrypted = swap_letters(message)`
        - `messagebox.showinfo('Ciphertext of the secret message is:', encrypted)`
        - If the user chose "encrypt", it gets the message, calls `swap_letters()` to encrypt it, and then displays the `encrypted` result in a `messagebox`.
    - `elif task == 'decrypt':`
        - `message = get_message()`
        - `decrypted = swap_letters(message)`
        - `messagebox.showinfo('Plaintext of the secret message is:', decrypted)`
        - If the user chose "decrypt", it gets the encrypted message, calls `swap_letters()` (which will now decrypt it), and displays the `decrypted` result.
    - `else:`
        - `break`
        - If the user types anything other than "encrypt" or "decrypt" (e.g., clicks "Cancel" or types "quit"), the `break` statement is executed, which exits the `while True` loop and effectively ends the program's main interaction cycle.
4. **`root.mainloop()` (Final Call)**:
    - This final `root.mainloop()` call ensures the Tkinter window and event loop continue to run after the `while True` loop has potentially exited (though the code seems to have `root.mainloop()` *inside* the `while True` loop, which is unusual for standard Tkinter practice, but the final project reference places it outside, making more sense for a continuous program that terminates on `break`).

**5. Hacks and Tweaks (Enhancements)**

The sources also describe ways to make the "Secret Messages" cipher more complex:

- **Reverse after swapping**: You can add another layer of encryption by reversing the message *after* swapping the letters. This requires separate `encrypt()` and `decrypt()` functions.
- **Add "fake" letters**: Introduce random, non-message letters between the real ones to make the ciphertext even harder to crack. This also uses dedicated `encrypt()` and `decrypt()` functions.

---

### Screen Pet

This program creates an interactive "Screen Pet" using Tkinter. The pet can blink, show happy/sad expressions, and stick out its tongue based on mouse interactions. It uses event-driven programming and "flag variables" to track its mood and state.

```python
from tkinter import HIDDEN, NORMAL, Tk, Canvas

def toggle_eyes():
    current_color = c.itemcget(eye_left, 'fill')
    new_color = c.body_color if current_color == 'white' else 'white'
    current_state = c.itemcget(pupil_left, 'state')
    new_state = NORMAL if current_state == HIDDEN else HIDDEN
    c.itemconfigure(pupil_left, state=new_state)
    c.itemconfigure(pupil_right, state=new_state)
    c.itemconfigure(eye_left, fill=new_color)
    c.itemconfigure(eye_right, fill=new_color)

def blink():
    toggle_eyes()
    root.after(250, toggle_eyes)
    root.after(3000, blink)

def toggle_pupils():
    if not c.eyes_crossed:
        c.move(pupil_left, 10, -5)
        c.move(pupil_right, -10, -5)
        c.eyes_crossed = True
    else:
        c.move(pupil_left, -10, 5)
        c.move(pupil_right, 10, 5)
        c.eyes_crossed = False

def toggle_tongue():
    if not c.tongue_out:
        c.itemconfigure(tongue_tip, state=NORMAL)
        c.itemconfigure(tongue_main, state=NORMAL)
        c.tongue_out = True
    else:
        c.itemconfigure(tongue_tip, state=HIDDEN)
        c.itemconfigure(tongue_main, state=HIDDEN)
        c.tongue_out = False

def cheeky(event):
    toggle_tongue()
    toggle_pupils()
    hide_happy(event)
    root.after(1000, toggle_tongue)
    root.after(1000, toggle_pupils)
    return

def show_happy(event):
    if (20 <= event.x and event.x <= 350) and (20 <= event.y and event.y <= 350):
        c.itemconfigure(cheek_left, state=NORMAL)
        c.itemconfigure(cheek_right, state=NORMAL)
        c.itemconfigure(mouth_happy, state=NORMAL)
        c.itemconfigure(mouth_normal, state=HIDDEN)
        c.itemconfigure(mouth_sad, state=HIDDEN)
        c.happy_level = 10
    return

def hide_happy(event):
    c.itemconfigure(cheek_left, state=HIDDEN)
    c.itemconfigure(cheek_right, state=HIDDEN)
    c.itemconfigure(mouth_happy, state=HIDDEN)
    c.itemconfigure(mouth_normal, state=NORMAL)
    c.itemconfigure(mouth_sad, state=HIDDEN)
    return

def sad():
    if c.happy_level == 0:
        c.itemconfigure(mouth_happy, state=HIDDEN)
        c.itemconfigure(mouth_normal, state=HIDDEN)
        c.itemconfigure(mouth_sad, state=NORMAL)
    else:
        c.happy_level -= 1
    root.after(5000, sad)

root = Tk()
c = Canvas(root, width=400, height=400)
c.configure(bg='dark blue', highlightthickness=0)
c.body_color = 'SkyBlue1'

body = c.create_oval(35, 20, 365, 350, outline=c.body_color, fill=c.body_color)
ear_left = c.create_polygon(75, 80, 75, 10, 165, 70, outline=c.body_color, fill=c.body_color)
ear_right = c.create_polygon(255, 45, 325, 10, 320, 70, outline=c.body_color, fill=c.body_color)
foot_left = c.create_oval(65, 320, 145, 360, outline=c.body_color, fill=c.body_color)
foot_right = c.create_oval(250, 320, 330, 360, outline=c.body_color, fill=c.body_color)

eye_left = c.create_oval(130, 110, 160, 170, outline='black', fill='white')
pupil_left = c.create_oval(140, 145, 150, 155, outline='black', fill='black')
eye_right = c.create_oval(230, 110, 260, 170, outline='black', fill='white')
pupil_right = c.create_oval(240, 145, 250, 155, outline='black', fill='black')

mouth_normal = c.create_line(170, 250, 200, 272, 230, 250, smooth=1, width=2, state=NORMAL)
mouth_happy = c.create_line(170, 250, 200, 282, 230, 250, smooth=1, width=2, state=HIDDEN)
mouth_sad = c.create_line(170, 250, 200, 232, 230, 250, smooth=1, width=2, state=HIDDEN)
tongue_main = c.create_rectangle(170, 250, 230, 290, outline='red', fill='red', state=HIDDEN)
tongue_tip = c.create_oval(170, 285, 230, 300, outline='red', fill='red', state=HIDDEN)

cheek_left = c.create_oval(70, 180, 120, 230, outline='pink', fill='pink', state=HIDDEN)
cheek_right = c.create_oval(280, 180, 330, 230, outline='pink', fill='pink', state=HIDDEN)

c.pack()

c.bind('<Motion>', show_happy)
c.bind('<Leave>', hide_happy)
c.bind('<Double-1>', cheeky)

c.happy_level = 10
c.eyes_crossed = False
c.tongue_out = False

root.after(1000, blink)
root.after(5000, sad)
root.mainloop()

```

The "Screen Pet" project allows you to create a virtual pet that "lives" on your computer screen within a Python Tkinter window. This pet can change its expression—from normal to happy, cheeky, or sad—based on your interactions, such as stroking it or double-clicking.

Here's a step-by-step explanation of the Python code for the Screen Pet:

### 1. Initial Setup and GUI Creation

The program is an **event-driven program**, meaning its actions depend on user input like mouse clicks.

- **Import Modules**: The project starts by importing necessary components from the `tkinter` module: `HIDDEN`, `NORMAL`, `Tk`, and `Canvas`.
- **Create Main Window (`root`)**: A `Tk()` object is created, which serves as the main window for the pet.
- **Create Canvas (`c`)**: A `Canvas` widget is set up within the main window. This is the drawing area for the pet. It's configured to be 400x400 pixels and dark blue, with no highlight border. The `c.pack()` command arranges the canvas within the Tkinter window.
- **Set Body Color Variable**: A variable `c.body_color` is initialized to 'SkyBlue1' for easy reuse when drawing the pet's parts.

### 2. Drawing the Screen Pet

Each part of the pet is drawn using Tkinter's Canvas functions and specific coordinates. Tkinter coordinates start at (0,0) in the top-left corner, with X increasing to the right and Y increasing downwards.

- **Body**: Drawn as an oval using `c.create_oval()`.
- **Ears**: Drawn as polygons using `c.create_polygon()`.
- **Feet**: Drawn as ovals using `c.create_oval()`.
- **Eyes and Pupils**: Drawn as ovals, with the pupils initially visible (`state=NORMAL`).
- **Mouths (Normal, Happy, Sad)**: Drawn as lines with `c.create_line()`. The `mouth_normal` is initially `NORMAL` (visible), while `mouth_happy` and `mouth_sad` are `HIDDEN`.
- **Tongue**: Drawn in two parts (rectangle and oval) using `c.create_rectangle()` and `c.create_oval()`, initially `HIDDEN`.
- **Cheeks**: Drawn as ovals using `c.create_oval()`, initially `HIDDEN`.

### 3. Blinking Functionality

The pet blinks by changing the visibility and color of its eye components.

- **`toggle_eyes()` Function**:
    - This function checks the current fill color of the left eye. If it's 'white' (open), it sets the new color to `c.body_color` (closed), and vice-versa.
    - It also toggles the `state` of the pupils between `NORMAL` (visible) and `HIDDEN`.
    - `c.itemconfigure()` is used to apply these changes to both pupils and eyes.
- **`blink()` Function**:
    - Calls `toggle_eyes()` to close the eyes.
    - Uses `root.after(250, toggle_eyes)` to schedule `toggle_eyes()` to run after 250 milliseconds (a quarter of a second), opening the eyes again.
    - Uses `root.after(3000, blink)` to schedule `blink()` itself to run again after 3000 milliseconds (3 seconds), creating a continuous blinking effect.
- **Start Blinking**: `root.after(1000, blink)` is called in the main program to start the blinking animation 1 second after the program begins.

### 4. Changing Moods (Happy)

The pet reacts to mouse movement.

- **`show_happy(event)` Function**:
    - This function is an **event handler**, called when a specific event occurs.
    - It checks if the mouse pointer's coordinates (`event.x`, `event.y`) are within the pet's body area.
    - If so, it uses `c.itemconfigure()` to change the state of the cheeks and `mouth_happy` to `NORMAL` (visible), and `mouth_normal` and `mouth_sad` to `HIDDEN`.
    - Crucially, it **resets `c.happy_level` to 10**, making the pet happy again and delaying the onset of sadness.
- **`hide_happy(event)` Function**: Reverts the pet's expression by hiding the cheeks and `mouth_happy`, and showing `mouth_normal`.
- **Bind Mouse Events**:
    - `c.bind('<Motion>', show_happy)` links the `<Motion>` event (mouse movement over the canvas) to the `show_happy` function.
    - `c.bind('<Leave>', hide_happy)` links the `<Leave>` event (mouse pointer leaving the canvas) to the `hide_happy` function.

### 5. Cheeky Functionality

The pet reacts to double-clicks.

- **Draw Tongue**: Lines of code are added to draw `tongue_main` (rectangle) and `tongue_tip` (oval) as hidden elements.
- **Flag Variables**: `c.eyes_crossed = False` and `c.tongue_out = False` are introduced to keep track of the pet's current state. **Flag variables** are used to indicate one of two states (e.g., True/False).
- **`toggle_tongue()` Function**:
    - Checks the `c.tongue_out` flag.
    - If `False`, it makes the tongue visible and sets `c.tongue_out` to `True`.
    - If `True`, it hides the tongue and sets `c.tongue_out` to `False`.
- **`toggle_pupils()` Function**:
    - Checks the `c.eyes_crossed` flag.
    - If `False`, it moves the `pupil_left` right by 10 pixels and up by 5 pixels, and `pupil_right` left by 10 pixels and up by 5 pixels using `c.move()`, then sets `c.eyes_crossed` to `True`.
    - If `True`, it moves the pupils back to their normal positions and sets `c.eyes_crossed` to `False`.
- **`cheeky(event)` Function**:
    - Calls `toggle_tongue()` and `toggle_pupils()` to make the pet stick out its tongue and cross its eyes.
    - Calls `hide_happy(event)` to ensure the happy face is not shown simultaneously.
    - Uses `root.after()` to schedule `toggle_tongue()` and `toggle_pupils()` again after 1000 milliseconds (1 second) to revert the cheeky expression.
- **Bind Double-Click Event**: `c.bind('<Double-1>', cheeky)` links the Tkinter `<Double-1>` event (a double-click with the left mouse button) to the `cheeky()` function.

### 6. Sad Pet Functionality

The pet becomes sad if ignored.

- **Happiness Level**: `c.happy_level = 10` is introduced as a variable to track the pet's mood, starting at 10.
- **`sad()` Function**:
    - Checks if `c.happy_level` is 0.
    - If it is, it hides the happy and normal mouths and shows the sad mouth (`mouth_sad`).
    - If `c.happy_level` is greater than 0, it subtracts 1 from `c.happy_level` (`c.happy_level -= 1`).
    - Schedules itself to run again after 5000 milliseconds (5 seconds) using `root.after(5000, sad)`.
- **Start Sad Timer**: `root.after(5000, sad)` is called in the main program to start checking for sadness 5 seconds after the program starts.

### 7. Main Loop

- **`root.mainloop()`**: This crucial function is called at the very end of the script. It starts the Tkinter event loop, which continuously checks for user inputs (events) and calls the appropriate event handler functions (like `show_happy`, `cheeky`, `sad`, `blink`) to make the pet interactive and animated.

### Caterpillar

This game involves steering a caterpillar to eat leaves, which makes it longer and faster. The code uses two turtles for the caterpillar and leaves, handles score display, and includes logic for game over if the caterpillar leaves the window.

```python
import random
import turtle as t

t.bgcolor('yellow')

caterpillar = t.Turtle()
caterpillar.shape('square')
caterpillar.color('red')
caterpillar.speed(0)
caterpillar.penup()
caterpillar.hideturtle()

leaf = t.Turtle()
leaf_shape = ((0, 0), (14, 2), (18, 6), (20, 20), (6, 18), (2, 14))
t.register_shape('leaf', leaf_shape)
leaf.shape('leaf')
leaf.color('green')
leaf.penup()
leaf.hideturtle()
leaf.speed(0)

game_started = False
text_turtle = t.Turtle()
text_turtle.write('Press SPACE to start', align='center', font=('Arial', 16, 'bold'))
text_turtle.hideturtle()

score_turtle = t.Turtle()
score_turtle.hideturtle()
score_turtle.speed(0)

def outside_window():
    left_wall = -t.window_width() / 2
    right_wall = t.window_width() / 2
    top_wall = t.window_height() / 2
    bottom_wall = -t.window_height() / 2
    (x, y) = caterpillar.pos()
    outside = \
            x < left_wall or \
            x > right_wall or \
            y < bottom_wall or \
            y > top_wall
    return outside

def game_over():
    caterpillar.color('yellow')
    leaf.color('yellow')
    t.penup()
    t.hideturtle()
    t.write('GAME OVER!', align='center', font=('Arial', 30, 'normal'))

def display_score(current_score):
    score_turtle.clear()
    score_turtle.penup()
    x = (t.window_width() / 2) - 50
    y = (t.window_height() / 2) - 50
    score_turtle.setpos(x, y)
    score_turtle.write(str(current_score), align='right', font=('Arial', 40, 'bold'))

def place_leaf():
    leaf.ht()
    leaf.setx(random.randint(-200, 200))
    leaf.sety(random.randint(-200, 200))
    leaf.st()

def start_game():
    global game_started
    if game_started:
        return
    game_started = True

    score = 0
    text_turtle.clear()

    caterpillar_speed = 2
    caterpillar_length = 3
    caterpillar.shapesize(1, caterpillar_length, 1)
    caterpillar.showturtle()
    display_score(score)
    place_leaf()

    while True:
        caterpillar.forward(caterpillar_speed)
        if caterpillar.distance(leaf) < 20:
            place_leaf()
            caterpillar_length = caterpillar_length + 1
            caterpillar.shapesize(1, caterpillar_length, 1)
            caterpillar_speed = caterpillar_speed + 1
            score = score + 10
            display_score(score)
        if outside_window():
            game_over()
            break

def move_up():
    if caterpillar.heading() == 0 or caterpillar.heading() == 180:
        caterpillar.setheading(90)

def move_down():
    if caterpillar.heading() == 0 or caterpillar.heading() == 180:
        caterpillar.setheading(270)

def move_left():
    if caterpillar.heading() == 90 or caterpillar.heading() == 270:
        caterpillar.setheading(180)

def move_right():
    if caterpillar.heading() == 90 or caterpillar.heading() == 270:
        caterpillar.setheading(0)

t.onkey(start_game, 'space')
t.onkey(move_up, 'Up')
t.onkey(move_right, 'Right')
t.onkey(move_down, 'Down')
t.onkey(move_left, 'Left')
t.listen()
t.mainloop()

```

### Snap

This is a two-player game of Snap where colored shapes appear on screen. Players hit 'q' or 'p' to "snap" if successive shapes have the same color. It tracks scores and declares a winner.

```python
import random
import time
from tkinter import Tk, Canvas, HIDDEN, NORMAL

def next_shape():
    global shape
    global previous_color
    global current_color

    previous_color = current_color

    c.delete(shape)
    if len(shapes) > 0:
        shape = shapes.pop()
        c.itemconfigure(shape, state=NORMAL)
        current_color = c.itemcget(shape, 'fill')
        root.after(1000, next_shape)
    else:
        c.unbind('q')
        c.unbind('p')
        if player1_score > player2_score:
            c.create_text(200, 200, text='Winner: Player 1')
        elif player2_score > player1_score:
            c.create_text(200, 200, text='Winner: Player 2')
        else:
            c.create_text(200, 200, text='Draw')
        c.pack()

def snap(event):
    global shape
    global player1_score
    global player2_score
    valid = False

    c.delete(shape)
    if previous_color == current_color:
        valid = True

    if valid:
        if event.char == 'q':
            player1_score = player1_score + 1
        else:
            player2_score = player2_score + 1
        shape = c.create_text(200, 200, text='SNAP! You score 1 point!')
    else:
        if event.char == 'q':
            player1_score = player1_score - 1
        else:
            player2_score = player2_score - 1
        shape = c.create_text(200, 200, text='WRONG! You lose 1 point!')
    c.pack()
    root.update_idletasks()
    time.sleep(1)

root = Tk()
root.title('Snap')
c = Canvas(root, width=400, height=400)

shapes = []

circle = c.create_oval(35, 20, 365, 350, outline='black', fill='black', state=HIDDEN)
shapes.append(circle)
circle = c.create_oval(35, 20, 365, 350, outline='red', fill='red', state=HIDDEN)
shapes.append(circle)
circle = c.create_oval(35, 20, 365, 350, outline='green', fill='green', state=HIDDEN)
shapes.append(circle)
circle = c.create_oval(35, 20, 365, 350, outline='blue', fill='blue', state=HIDDEN)
shapes.append(circle)

rectangle = c.create_rectangle(35, 100, 365, 270, outline='black', fill='black', state=HIDDEN)
shapes.append(rectangle)
rectangle = c.create_rectangle(35, 100, 365, 270, outline='red', fill='red', state=HIDDEN)
shapes.append(rectangle)
rectangle = c.create_rectangle(35, 100, 365, 270, outline='green', fill='green', state=HIDDEN)
shapes.append(rectangle)
rectangle = c.create_rectangle(35, 100, 365, 270, outline='blue', fill='blue', state=HIDDEN)
shapes.append(rectangle)

square = c.create_rectangle(35, 20, 365, 350, outline='black', fill='black', state=HIDDEN)
shapes.append(square)
square = c.create_rectangle(35, 20, 365, 350, outline='red', fill='red', state=HIDDEN)
shapes.append(square)
square = c.create_rectangle(35, 20, 365, 350, outline='green', fill='green', state=HIDDEN)
shapes.append(square)
square = c.create_rectangle(35, 20, 365, 350, outline='blue', fill='blue', state=HIDDEN)
shapes.append(square)
c.pack()

random.shuffle(shapes)

shape = None
previous_color = ''
current_color = ''
player1_score = 0
player2_score = 0

root.after(3000, next_shape)
c.bind('q', snap)
c.bind('p', snap)
c.focus_set()

root.mainloop()

```

### Matchmaker

This memory game challenges players to find matching pairs of hidden symbols in a grid of buttons. It uses Tkinter to create the GUI and handles button presses to reveal symbols and check for matches.

```python
import random
import time
from tkinter import Tk, Button, DISABLED

def show_symbol(x, y):
    global first
    global previousX, previousY
    buttons[x, y]['text'] = button_symbols[x, y]
    buttons[x, y].update_idletasks()

    if first:
        previousX = x
        previousY = y
        first = False
    elif previousX != x or previousY != y:
        if buttons[previousX, previousY]['text'] != buttons[x, y]['text']:
            time.sleep(0.5)
            buttons[previousX, previousY]['text'] = ''
            buttons[x, y]['text'] = ''
        else:
            buttons[previousX, previousY]['command'] = DISABLED
            buttons[x, y]['command'] = DISABLED
        first = True

root = Tk()
root.title('Matchmaker')
root.resizable(width=False, height=False)
buttons = {}
first = True
previousX = 0
previousY = 0
button_symbols = {}
symbols = [u'\u2702', u'\u2702', u'\u2705', u'\u2705', u'\u2708', u'\u2708',
            u'\u2709', u'\u2709', u'\u270A', u'\u270A', u'\u270B', u'\u270B',
            u'\u270C', u'\u270C', u'\u270F', u'\u270F', u'\u2712', u'\u2712',
            u'\u2714', u'\u2714', u'\u2716', u'\u2716', u'\u2728', u'\u2728']
random.shuffle(symbols)

for x in range(6):
    for y in range(4):
        button = Button(command=lambda x=x, y=y: show_symbol(x, y), width=3, height=3)
        button.grid(column=x, row=y)
        buttons[x, y] = button
        button_symbols[x, y] = symbols.pop()

root.mainloop()

```

### Egg Catcher

This arcade-style game involves moving a catcher to collect falling eggs. It uses Tkinter to draw the game elements and animate the eggs' movement. The game tracks scores, lives, and increases difficulty as more eggs are caught.

```python
from itertools import cycle
from random import randrange
from tkinter import Canvas, Tk, messagebox, font

canvas_width = 800
canvas_height = 400

root = Tk()
c = Canvas(root, width=canvas_width, height=canvas_height, background='deep sky blue')
c.create_rectangle(-5, canvas_height - 100, canvas_width + 5, canvas_height + 5, \
                    fill='sea green', width=0)
c.create_oval(-80, -80, 120, 120, fill='orange', width=0)
c.pack()

color_cycle = cycle(['light blue', 'light green', 'light pink', 'light yellow', 'light cyan'])
egg_width = 45
egg_height = 55
egg_score = 10
egg_speed = 500
egg_interval = 4000
difficulty_factor = 0.95

catcher_color = 'blue'
catcher_width = 100
catcher_height = 100
catcher_start_x = canvas_width / 2 - catcher_width / 2
catcher_start_y = canvas_height - catcher_height - 20
catcher_start_x2 = catcher_start_x + catcher_width
catcher_start_y2 = catcher_start_y + catcher_height

catcher = c.create_arc(catcher_start_x, catcher_start_y, \
                         catcher_start_x2, catcher_start_y2, start=200, extent=140, \
                         style='arc', outline=catcher_color, width=3)

game_font = font.nametofont('TkFixedFont')
game_font.config(size=18)

score = 0
score_text = c.create_text(10, 10, anchor='nw', font=game_font, fill='darkblue', \
                            text='Score: ' + str(score))

lives_remaining = 3
lives_text = c.create_text(canvas_width - 10, 10, anchor='ne', font=game_font, fill='darkblue', \
                            text='Lives: ' + str(lives_remaining))

eggs = []

def create_egg():
    x = randrange(10, 740)
    y = 40
    new_egg = c.create_oval(x, y, x + egg_width, y + egg_height, fill=next(color_cycle), width=0)
    eggs.append(new_egg)
    root.after(egg_interval, create_egg)

def move_eggs():
    for egg in eggs:
        (egg_x, egg_y, egg_x2, egg_y2) = c.coords(egg)
        c.move(egg, 0, 10)
        if egg_y2 > canvas_height:
            egg_dropped(egg)
    root.after(egg_speed, move_eggs)

def egg_dropped(egg):
    eggs.remove(egg)
    c.delete(egg)
    lose_a_life()
    if lives_remaining == 0:
        messagebox.showinfo('Game Over!', 'Final Score: ' + str(score))
        root.destroy()

def lose_a_life():
    global lives_remaining
    lives_remaining -= 1
    c.itemconfigure(lives_text, text='Lives: ' + str(lives_remaining))

def check_catch():
    (catcher_x, catcher_y, catcher_x2, catcher_y2) = c.coords(catcher)
    for egg in eggs:
        (egg_x, egg_y, egg_x2, egg_y2) = c.coords(egg)
        if catcher_x < egg_x and egg_x2 < catcher_x2 and catcher_y2 - egg_y2 < 40:
            eggs.remove(egg)
            c.delete(egg)
            increase_score(egg_score)
    root.after(100, check_catch)

def increase_score(points):
    global score, egg_speed, egg_interval
    score += points
    egg_speed = int(egg_speed * difficulty_factor)
    egg_interval = int(egg_interval * difficulty_factor)
    c.itemconfigure(score_text, text='Score: ' + str(score))

def move_left(event):
    (x1, y1, x2, y2) = c.coords(catcher)
    if x1 > 0:
        c.move(catcher, -20, 0)

def move_right(event):
    (x1, y1, x2, y2) = c.coords(catcher)
    if x2 < canvas_width:
        c.move(catcher, 20, 0)

c.bind('<Left>', move_left)
c.bind('<Right>', move_right)
c.focus_set()

root.after(1000, create_egg)
root.after(1000, move_eggs)
root.after(1000, check_catch)
root.mainloop()

```