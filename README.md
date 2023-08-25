import java.util.Scanner;
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int lowerRange = 1;
        int upperRange = 100;
        int numberToGuess = random.nextInt(upperRange - lowerRange + 1) + lowerRange;
        int maxAttempts = 10;
        int attempts = 0;

        System.out.println("Welcome to the Guess the Number game!");
        System.out.printf("I'm thinking of a number between %d and %d. Can you guess it?\n", lowerRange, upperRange);

        while (attempts < maxAttempts) {
            System.out.print("Enter your guess: ");
            int userGuess;

            try {
                userGuess = scanner.nextInt();
            } catch (Exception e) {
                System.out.println("Invalid input. Please enter a valid number.");
                scanner.nextLine(); // Clear the input buffer
                continue;
            }

            attempts++;

            if (userGuess < numberToGuess) {
                System.out.println("Too low! Try again.");
            } else if (userGuess > numberToGuess) {
                System.out.println("Too high! Try again.");
            } else {
                System.out.printf("Congratulations! You guessed the number %d in %d attempts.\n", numberToGuess, attempts);
                break;
            }
        }

        if (attempts == maxAttempts) {
            System.out.printf("Sorry, you've reached the maximum number of attempts. The correct number was %d.\n", numberToGuess);
        }

        scanner.close();
    }
}
