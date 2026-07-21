//Ashley Snuggs CIS407 Week 2 - Guessing Game

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
		int number = gen.nextInt(100);
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
		boolean truth = false;
		if (number == guess) {
			truth = true;
		} else {
			truth = false;
			System.out.println("Guess again");
		}
		return truth;
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		displayWelcomeMessage();
		Game newGame = new Game();
		int number = newGame.generateNumberToBeGuessed();
		int guess = newGame.makeGuess();
		boolean truth = newGame.isCorrectGuess(number,guess);
		if (truth == true) {
			System.out.println("Good Job!");
		} else {
			System.out.println("Try again.");
			newGame.makeGuess();
		}
	}

}
