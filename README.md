package guessingGame;

import java.util.random.RandomGenerator;
import java.util.Scanner;

public class Game {

    RandomGenerator gen = RandomGenerator.getDefault();
    Scanner scanner = new Scanner(System.in);

    public static void displayWelcomeMessage() {
        System.out.println("Welcome to the Guess the Number Game!");
        System.out.println("++++++++++++++++++++++++++++++++++++");
        System.out.println("I'm thinking of a number from 1 to 100.");
        System.out.println("Try to guess it.");
    }

    int generateNumberToBeGuessed() {
        // nextInt(100) gives 0-99, so add 1 to get 1-100
        int number = gen.nextInt(100) + 1;
        return number; // no longer printing the answer!
    }

    int makeGuess() {
        System.out.println("Enter a number between 1 and 100: ");
        int guess = scanner.nextInt();
        return guess;
    }

    int guessCounter(int numofguess) {
        numofguess += 1;
        return numofguess;
    }

    boolean isCorrectGuess(int number, int guess) {
        return number == guess;
    }

    public static void main(String[] args) {
        Game newGame = new Game();
        displayWelcomeMessage();

        int number = newGame.generateNumberToBeGuessed();
        int max = number + 10;
        int min = number - 10;
        int numOfGuesses = 0;
        boolean truth;

        int guess = newGame.makeGuess();
        numOfGuesses = newGame.guessCounter(numOfGuesses);

        do {
            truth = newGame.isCorrectGuess(number, guess);

            if (truth) {
                System.out.println("Correct!");
            } else if (guess < min) {
                System.out.println("Way too low!");
            } else if (guess < number) {
                System.out.println("Too low!");
            } else if (guess > max) {
                System.out.println("Way too high!");
            } else {
                System.out.println("Too high!");
            }

            if (!truth) {
                guess = newGame.makeGuess();          // now actually updates guess
                numOfGuesses = newGame.guessCounter(numOfGuesses);
            }
        } while (!truth);

        System.out.println("Good Job! It took you " + numOfGuesses + " guesses.");
        newGame.scanner.close();
    }
}
