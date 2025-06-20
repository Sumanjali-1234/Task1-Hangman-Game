# Task1-Hangman-Game
import random
words = ["table", "cat", "lemon", "men", "movie"]
secret_word = random.choice(words)
guessed_letters = []
attempts_left = 6
display_word = ["_"] * len(secret_word)
print("Welcome to the Hangman Game!")
print("Guess the word, one letter at a time.")
print("You have 6 chances to guess incorrectly.\n")
while attempts_left > 0 and "_" in display_word:
    print("Word: " + " ".join(display_word))
    print(f"Guessed letters: {', '.join(guessed_letters)}")
    print(f"Attempts left: {attempts_left}")

    guess = input("Enter a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print("Please enter a single valid letter.\n")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.\n")
        continue

    guessed_letters.append(guess)

    if guess in secret_word:
        print("Correct guess!\n")
        for index, letter in enumerate(secret_word):
            if letter == guess:
                display_word[index] = guess
    else:
        print("Incorrect guess.\n")
        attempts_left -= 1
if "_" not in display_word:
    print("Congratulations! You guessed the word:", secret_word)
else:
    print("Out of attempts! The word was:", secret_word)
