# Online-Examination-System
Using java programming online examination system  is my mini project
import java.util.Scanner;

public class OnlineExaminationSystem {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String[] questions = {
            "Which language is used to develop Android apps?",
            "Which keyword is used to create a class in Java?",
            "Which method is the entry point of a Java program?",
            "Which data type stores whole numbers?",
            "Which symbol ends a Java statement?"
        };

        String[][] options = {
            {"1. Python", "2. Java", "3. HTML", "4. SQL"},
            {"1. function", "2. define", "3. class", "4. newclass"},
            {"1. start()", "2. run()", "3. main()", "4. init()"},
            {"1. int", "2. boolean", "3. char", "4. String"},
            {"1. :", "2. ;", "3. ,", "4. ."}
        };

        int[] correctAnswers = {2, 3, 3, 1, 2};
        int score = 0;

        System.out.println("==================================");
        System.out.println("   ONLINE EXAMINATION SYSTEM");
        System.out.println("==================================");
        System.out.print("Enter your name: ");
        String studentName = sc.nextLine().trim();

        if (studentName.isEmpty()) {
            studentName = "Student";
        }

        System.out.println("\nWelcome, " + studentName + "!");
        System.out.println("There are " + questions.length + " questions.");
        System.out.println("Enter an option number from 1 to 4.\n");

        for (int i = 0; i < questions.length; i++) {
            System.out.println("Q" + (i + 1) + ". " + questions[i]);

            for (String option : options[i]) {
                System.out.println(option);
            }

            int answer;
            while (true) {
                System.out.print("Your answer (1-4): ");
                if (sc.hasNextInt()) {
                    answer = sc.nextInt();
                    if (answer >= 1 && answer <= 4) {
                        break;
                    }
                } else {
                    sc.next(); // Discard invalid non-number input
                }
                System.out.println("Please enter a number from 1 to 4.");
            }

            if (answer == correctAnswers[i]) {
                score++;
            }
            System.out.println();
        }

        double percentage = (score * 100.0) / questions.length;

        System.out.println("==================================");
        System.out.println("          EXAM RESULT");
        System.out.println("==================================");
        System.out.println("Student Name : " + studentName);
        System.out.println("Total Marks  : " + questions.length);
        System.out.println("Score        : " + score);
        System.out.printf("Percentage   : %.2f%%%n", percentage);
        System.out.println("==================================");

        sc.close();
    }
}
