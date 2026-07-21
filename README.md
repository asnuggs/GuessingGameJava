//Ashley Snuggs CIS407 Week 2 - Guessing Game

package guessingGame;

import java.util.random.RandomGenerator; import java.util.Scanner;

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
	int number = gen.nextInt(100);
	System.out.println(number);
	return number;
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
	boolean truth;
	if (number == guess) {
		truth = true;
	} else {
		truth = false;
	}
	return truth;
}

public static void main(String[] args) {
	// TODO Auto-generated method stub
	boolean truth;
	displayWelcomeMessage();
	Game newGame = new Game();
	int number = newGame.generateNumberToBeGuessed();
	int guess = newGame.makeGuess();
	int max = number + 10;
	int min = number - 10;
	do {
		truth = newGame.isCorrectGuess(number,guess);
		if (guess < min) {
			System.out.println("Way too low!");
		} else if (guess > min && guess < number) {
			System.out.println("Too low!");
		} else if (guess > max) {
			System.out.println("Way too high!");
		} else {
			System.out.println("Too high!");
		}
		newGame.makeGuess();
	} while(!truth);
	
	System.out.println("Good Job!");
}
}
