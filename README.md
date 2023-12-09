import random

wordlist = ['lauracafe', 'gokart', 'biddapark', 'Metro', 'Noble_international_school', 'december', 'september', 'january',]

print("Welcome to my Hangman game")
print("Lets get started on this game")

# will print this first before the game starts
word = random.choice(wordlist)  # this will choose a random word from the list

for x in word:
    print("_", end=" ")  # this will print the word with dashes with how many letters are in the word

def print_hangman(wrong):
    if wrong==0:
        print("\n------")
        print("|     ")
        print("|     ")
        print("|     ")
        print("|     ")
        print("===    ")
    elif wrong==1:
        print("\n------")
        print("|    0")
        print("|     ")
        print("|     ")
        print("|     ")
        print("===    ")
    elif wrong==2:
        print("\n------")
        print("|    0")
        print("|    |")
        print("|     ")
        print("|     ")
        print("===    ")
    elif wrong==3:
        print("\n------")
        print("|     0 ")
        print("|    /| ")
        print("|       ")
        print("|       ")
        print("===     ")
    elif wrong==4:
        print("\n------")
        print("|    0  ")
        print("|   /|\ ")
        print("|       ")
        print("|       ")
        print("===     ")
    elif wrong==5:
        print("\n------")
        print("|    0  ")
        print("|   /|\ ")
        print("|   /   ")
        print("|       ")
        print("===     ")
    elif wrong==6:
        print("\n------")
        print("|    0  ")
        print("|   /|\ ")
        print("|   / \ ")
        print("|       ")
        print("===     ")
  
                                                    #this is where the function comes from the guessed letter
def print_word(guessedletters):                      #this part is used to print the letter which have been guessed correctly
    
    rightletters = 0
    for char in word:
        if char in guessedletters:
            print(char, end=" ")
            rightletters += 1
        else:
            print("_", end=" ")
        
    print("\n")
    return rightletters

length = len(word)
amountofwrongguesses = 0
guessedletters = []

while amountofwrongguesses < 6:
    print("\n")
    print("Guess a letter: ")
    guess = input()
    if guess in guessedletters:
        print("You already guessed that letter")
        continue
    guessedletters.append(guess) #this connects the guessed words into the guessletters list
    if guess in word:
        current_right_letters = print_word(guessedletters)     #if the word is in guessed letter it will send control to (print_word function)
        print("\n")
        print("You guessed a letter correctly")
        print("You have guessed", current_right_letters, "out of", length, "letters correctly")
        if current_right_letters == length:
            print("Congratulations! You've guessed the word correctly.")
            break
    else:
        amountofwrongguesses += 1
        print("You guessed a letter incorrectly")
        print("You have", 6 - amountofwrongguesses, "guesses left")
    print_hangman(amountofwrongguesses)
    print("\n")
