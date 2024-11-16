import java.util.Scanner;

public class Calculator {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String continueCalculating = "yes"; // Variable to control whether the user wants to continue

        System.out.println("Welcome to the Java Calculator!");

        while (continueCalculating.equalsIgnoreCase("yes")) {
        
            System.out.print("Enter an operation (+, -, *, /, or exit): ");
            String operation = scanner.next();

    
            if (operation.equalsIgnoreCase("exit")) {
                System.out.println("Thank you for using the Java Calculator! Goodbye!");
                break;
            }

            if (!operation.equals("+") && !operation.equals("-") && !operation.equals("*") && !operation.equals("/")) {
                System.out.println("Error: Invalid operation. Please choose +, -, *, /, or exit.");
                continue;
            }

            System.out.print("Enter the first number: ");
            double num1 = getValidNumber(scanner);
            
            System.out.print("Enter the second number: ");
            double num2 = getValidNumber(scanner);

            double result = 0;
            boolean validOperation = true;

            switch (operation) {
                case "+":
                    result = num1 + num2;
                    break;
                case "-":
                    result = num1 - num2;
                    break;
                case "*":
                    result = num1 * num2;
                    break;
                case "/":
                    if (num2 == 0) {
                        System.out.println("Error: Division by zero is not allowed.");
                        validOperation = false;  // Don't print result if division by zero occurs
                    } else {
                        result = num1 / num2;
                    }
                    break;
            }
            if (validOperation) {
                System.out.println("The result of " + num1 + " " + operation + " " + num2 + " = " + result);
            }
            System.out.print("Would you like to perform another operation (yes/no)? ");
            continueCalculating = scanner.next();
        }

        scanner.close();
    }
    public static double getValidNumber(Scanner scanner) {
        double number = 0;
        boolean valid = false;

        while (!valid) {
            if (scanner.hasNextDouble()) {
                number = scanner.nextDouble();
                
                if (number >= -1000 && number <= 1000) {
                    valid = true;
                } else {
                    System.out.println("Error: Please enter a number between -1000 and 1000.");
                }
            } else {
                System.out.println("Error: Invalid input. Please enter a valid number.");
                scanner.next(); // Consume the invalid input
            }
        }

        return number;
    }
}
