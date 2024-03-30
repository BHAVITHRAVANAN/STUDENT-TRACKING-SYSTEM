import java.util.ArrayList;
import java.util.Scanner;
public class StudentGradeTracker {
  public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();
        // Get number of students
        System.out.print("Enter the number of students: ");
        int numStudents = scanner.nextInt();
       // Input data for each student
        for (int i = 0; i < numStudents; i++) {
            System.out.println("\nEnter details for student " + (i + 1));
            System.out.print("Name: ");
            String name = scanner.nextLine();
            scanner.nextLine(); // Consume extra newline character
            ArrayList<Double> grades = new ArrayList<>();
            double totalScore = 0;
            // Get grades for each student (assuming multiple assignments)
            while (true) {
                System.out.print("Enter grade (-1 to finish): ");
                double grade = scanner.nextDouble();
                if (grade == -1) {
                    break;
                }
                grades.add(grade);
                totalScore += grade;
            }
            // Calculate average grade
            double averageGrade = totalScore / grades.size();
            // Find highest and lowest grades
            double highestGrade = grades.get(0);
            double lowestGrade = grades.get(0);
            for (double grade : grades) {
                highestGrade = Math.max(highestGrade, grade);
                lowestGrade = Math.min(lowestGrade, grade);
            }

            // Create student object and add to list
            Student student = new Student(name, grades, averageGrade, highestGrade, lowestGrade);
            students.add(student);
        }
        // Print student reports
        System.out.println("\nStudent Reports:");
        for (Student student : students) {
            student.printReport();
            }
            scanner.close();
    }
}
class Student {
    private String name;
    private ArrayList<Double> grades;
    private double averageGrade;
    private double highestGrade;
    private double lowestGrade;
    public Student(String name, ArrayList<Double> grades, double averageGrade, double highestGrade, double lowestGrade) {
        this.name = name;
        this.grades = grades;
        this.averageGrade = averageGrade;
        this.highestGrade = highestGrade;
        this.lowestGrade = lowestGrade;
    }
    public void printReport() {
        System.out.println("Name: " + name);
        System.out.println("Grades: " + grades);
        System.out.println("Average Grade: " + averageGrade);
        System.out.println("Highest Grade: " + highestGrade);
        System.out.println("Lowest Grade: " + lowestGrade);
        System.out.println();
    }
}
