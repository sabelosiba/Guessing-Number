# Guess the Number Game
## Logic
import random

bot_Number = random.randint(1,100)

print('Im thinking of a number ')

guessNumber  = 0 
attempts = 0

while  guessNumber != bot_Number:

    guessNumber = int(input('Guess number!: '))
    attempts+=1

    if (guessNumber > bot_Number): 
     print('Guess smaller')

    elif(guessNumber < bot_Number):
     print ('Guess bigger!')

    else: 

     print('You guessed right ! after {attempts} attempts')

## GUI
import tkinter <br>
class Random_Number_Guesser:
   
    def __init__(self):
        BACKGROUND_HEX = "#111111"  # This is the Colour of the Background
        BUTTON_HEX = "#05C36A"  # This is the Colour of the Button
        MAIN_FONT = "Cambria"  # This is the type of Font
        PRIMARY_HEADER = 18  # This is the size of the font: Primary Header
        SECONDARY_HEADER = 14  # This is the size of the font: Secondary Header
        TERTIARY_HEADER = 10  # This is the size of the font: Tertiary Header

        self.root = tkinter.Tk() # Assigns the tkinter to the variable root
        self.root.geometry("700x400") # Sets the size of the frame
        self.root.title("Random Number Guesser") # Changes the Title of frame
        self.root.configure(bg=BACKGROUND_HEX) # Changes the background of frame

        # This refers to the main title
        self.title = tkinter.Label(self.root, text="Random Number Guesser", font=(MAIN_FONT,PRIMARY_HEADER) , background=BACKGROUND_HEX, foreground="white")
        self.title.pack(padx=20, pady = 20)

        # This refers to the description of the Game
        p_Description = tkinter.Label(self.root, text="""
        The Game is Simple! The program will select a random number between 1 and 100, 
        and your goal is to guess what number it is. If you guess lower than the 
        generated number, the program will prompt you to guess higher, and the same if
        you guess too high. Goodluck!""", font=(MAIN_FONT,TERTIARY_HEADER), background=BACKGROUND_HEX, foreground="white")
        p_Description.pack(padx=20)

        # This refers to the input box
        user_Input = tkinter.Entry(self.root, font=MAIN_FONT, width=10)
        user_Input.pack(padx=20, pady=30)

        # This refers to the result of the input box
        results = tkinter.Label(self.root, text="The Value You Inputted Was: ", font=MAIN_FONT, background=BACKGROUND_HEX, foreground="white")
        results.pack(pady=20, padx=20)

        # This function will be called when the button (btn_Submit) is pressed
        def display_Result():
            user = user_Input.get()
            results.config(text=f"The Value You Inputted Was: {user}")

        # This refers to the submit button
        btn_Submit = tkinter.Button(self.root, text="Submit", font=(MAIN_FONT, SECONDARY_HEADER, 'bold'), background=BUTTON_HEX, command=display_Result , foreground='white',justify='center')
        btn_Submit.pack()

        # This runs the GUI
        self.root.mainloop()

Random_Number_Guesser()


## LOGIC+GUI Intergration
```python
import tkinter
import random

class Random_Number_Guesser:

    def __init__(self):
        BACKGROUND_HEX = "#111111"  # This is the Colour of the Background
        BUTTON_HEX = "#05C36A"  # This is the Colour of the Button
        MAIN_FONT = "Cambria"  # This is the type of Font
        PRIMARY_HEADER = 18  # This is the size of the font: Primary Header
        SECONDARY_HEADER = 14  # This is the size of the font: Secondary Header
        TERTIARY_HEADER = 10  # This is the size of the font: Tertiary Header

        self.root = tkinter.Tk() # Assigns the tkinter to the variable root
        self.root.geometry("700x400") # Sets the size of the frame
        self.root.title("Random Number Guesser") # Changes the Title of frame
        self.root.configure(bg=BACKGROUND_HEX) # Changes the background of frame

        # This generates a random number between 1 and 100
        self.bot_number = random.randint(1,100)
        self.attempts = 0 # This keep counts of the attempts made guessing

        # This refers to the main title
        self.title = tkinter.Label(self.root, text="Random Number Guesser", font=(MAIN_FONT,PRIMARY_HEADER) , background=BACKGROUND_HEX, foreground="white")
        self.title.pack(padx=20, pady = 20)

        # This refers to the description of the Game
        p_Description = tkinter.Label(self.root, text="""
        The Game is Simple! The program will select a random number between 1 and 100, 
        and your goal is to guess what number it is. If you guess lower than the 
        generated number, the program will prompt you to guess higher, and the same if
        you guess too high. Goodluck!""", font=(MAIN_FONT,TERTIARY_HEADER), background=BACKGROUND_HEX, foreground="white")
        p_Description.pack(padx=20)

        # This refers to the input box
        user_Input = tkinter.Entry(self.root, font=MAIN_FONT, width=10)
        user_Input.pack(padx=20, pady=30)

        # This refers to the result of the input box
        results = tkinter.Label(self.root, text="The Value You Inputted Was: ", font=MAIN_FONT, background=BACKGROUND_HEX, foreground="white")
        results.pack(pady=20, padx=20)

        # This function will be called when the button (btn_Submit) is pressed
        def display_Result():
            user_guess = int(user_Input.get()) #  Gets the value from the Entry Box
            self.attempts += 1 # Increases by one each time the button is clicked 
            
            if user_guess == self.bot_number: #  Checks if the User has Won or Lost
                message = f"You guessed right! after {self.attempts} attempts"
            elif user_guess < self.bot_number: #   Prompts the User to guess Higher
                message = "Guess bigger!"
            else:
                 message = "Guess smaller!"
            
            results.config(text=message)

        # This refers to the submit button
        btn_Submit = tkinter.Button(self.root, text="Submit", font=(MAIN_FONT, SECONDARY_HEADER, 'bold'), background=BUTTON_HEX, command=display_Result , foreground='white',justify='center')
        btn_Submit.pack()

        # This runs the GUI
        self.root.mainloop()
Random_Number_Guesser()
```
