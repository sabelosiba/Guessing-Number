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

     print('You guseed right ! after {attempts} attempts')
