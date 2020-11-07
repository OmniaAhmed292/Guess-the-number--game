# guess the number game.


import random
attempts = []
def show_score():
    if len(attempts) <= 0:
        print("No high scores")
    else:
        print("High score is {} attempts".format(min(attempts)))
def start_game():
    random_number = int(random.randint(1, 100))
    print("Hello There. The game started ")
    player_name = input("What is your name? ")
    wanna_play = input("Hi, {}, would you like to play the guessing game? (Enter Yes/No) ".format(player_name))
   
    attempts_num = 0
    show_score()
    while wanna_play.lower() == "yes":
        try:
            guess = input("Choose a number between 1 and 100 ")
            if int(guess) < 1 or int(guess) > 100:
                raise ValueError("Please guess a number within the given range")
            if int(guess) == random_number:
                print("Nice! You got it!")
                attempts_num += 1
                attempts.append(attempts_num)
                print("It took you {} attempts".format(attempts_num))
                play_again = input("Would you like to play again? (Enter Yes/No) ")
                attempts = 0
                show_score()
                random_number = int(random.randint(1, 100))
                if play_again.lower() == "no":
                    print("Ok thank you")
                    break
            elif int(guess) > random_number:
                print("It's lower")
                attempts += 1
            elif int(guess) < random_number:
                print("It's higher")
                attempts += 1
        except ValueError as err:
            print("That is not a valid value. Please Try again...")
            print("({})".format(err))
    else:
        print("Ok thank you")
if __name__ == '__main__':
    start_game()
                
