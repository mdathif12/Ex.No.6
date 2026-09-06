# Ex.No.6 – AI-Assisted Programming and Debugging


## Register No:212223220058
________________________

## Aim

To write and implement Python code that integrates with multiple AI tools to automate the
task of interacting with APIs, comparing outputs, identifying bugs, optimizing code,
explaining complexity, generating unit tests, and producing actionable insights.

## AI Tools Required

- ChatGPT
- Google Gemini
- Microsoft Copilot

## Explanation

AI-assisted programming uses Artificial Intelligence tools to help programmers generate,
debug, optimize, test, and analyze source code.

In this experiment, the **Persona Pattern** is used by assigning the AI the role of an
experienced programmer. The same programming problem is provided to multiple AI tools,
and the generated code is compared and evaluated.

The experiment covers:

1. Python code generation using AI
2. C code generation using AI
3. Java code generation using AI
4. Bug identification and debugging
5. Code optimization
6. Time and space complexity analysis
7. Unit test generation
8. Comparison of manual coding and AI-assisted coding
9. Code quality analysis

---

# Application Selected

## Student Marks Management System

The application accepts student marks, calculates the total and average, determines the
grade, and displays the result.

---

# 1. Persona Pattern

### Prompt Used

```text
You are an experienced software programmer and debugging expert.

Develop a simple Student Marks Management System that accepts marks for five subjects,
calculates the total and average, and assigns a grade.

Generate the program in Python, C, and Java.

After generating the code:
1. Identify possible bugs.
2. Optimize the code.
3. Explain time and space complexity.
4. Generate suitable unit test cases.
5. Explain the advantages and limitations of AI-generated code.
2. Python Program
AI-Generated Python Code
Python


Run
def calculate_result(marks):
    total = sum(marks)
    average = total / len(marks)

    if average >= 90:
        grade = "A"
    elif average >= 75:
        grade = "B"
    elif average >= 60:
        grade = "C"
    elif average >= 50:
        grade = "D"
    else:
        grade = "F"

    return total, average, grade


marks = []

for i in range(5):
    mark = float(input(f"Enter mark for subject {i + 1}: "))
    marks.append(mark)

total, average, grade = calculate_result(marks)

print("Total Marks:", total)
print("Average:", average)
print("Grade:", grade)
3. C Program
AI-Generated C Code
C

#include <stdio.h>

int main() {
    float marks[5];
    float total = 0;
    float average;
    char grade;

    for (int i = 0; i < 5; i++) {
        printf("Enter mark for subject %d: ", i + 1);
        scanf("%f", &marks[i]);
        total += marks[i];
    }

    average = total / 5;

    if (average >= 90)
        grade = 'A';
    else if (average >= 75)
        grade = 'B';
    else if (average >= 60)
        grade = 'C';
    else if (average >= 50)
        grade = 'D';
    else
        grade = 'F';

    printf("Total Marks: %.2f\n", total);
    printf("Average: %.2f\n", average);
    printf("Grade: %c\n", grade);

    return 0;
}
4. Java Program
AI-Generated Java Code
Java

import java.util.Scanner;

public class StudentMarks {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        double total = 0;

        for (int i = 0; i < 5; i++) {
            System.out.print("Enter mark for subject " + (i + 1) + ": ");
            double mark = scanner.nextDouble();
            total += mark;
        }

        double average = total / 5;
        char grade;

        if (average >= 90)
            grade = 'A';
        else if (average >= 75)
            grade = 'B';
        else if (average >= 60)
            grade = 'C';
        else if (average >= 50)
            grade = 'D';
        else
            grade = 'F';

        System.out.println("Total Marks: " + total);
        System.out.println("Average: " + average);
        System.out.println("Grade: " + grade);

        scanner.close();
    }
}
5. Bug Identification
Buggy Python Code
Python


Run
def calculate_average(marks):
    total = sum(marks)
    average = total / len(marks)
    return average

marks = []
print("Enter marks")

for i in range(5):
    mark = float(input("Enter mark: "))
    marks.append(mark)

average = calculate_average(marks)

if average > 90:
    print("Grade A")
elif average > 75:
    print("Grade B")
elif average > 60:
    print("Grade C")
else:
    print("Grade F")
Identified Issues

1. Marks are not validated.
2. Negative marks can be entered.
3. Marks greater than 100 can be entered.
4. Grade boundary conditions may not match the required specification.
5. Empty input can cause a ValueError.
6. The program does not clearly separate input, processing, and output.
6. Optimized Python Code
Python


Run
def calculate_result(marks):
    if not marks:
        raise ValueError("Marks list cannot be empty.")

    if any(mark < 0 or mark > 100 for mark in marks):
        raise ValueError("Marks must be between 0 and 100.")

    total = sum(marks)
    average = total / len(marks)

    if average >= 90:
        grade = "A"
    elif average >= 75:
        grade = "B"
    elif average >= 60:
        grade = "C"
    elif average >= 50:
        grade = "D"
    else:
        grade = "F"

    return total, average, grade


marks = []

for i in range(5):
    while True:
        try:
            mark = float(input(f"Enter mark for subject {i + 1}: "))

            if 0 <= mark <= 100:
                marks.append(mark)
                break

            print("Enter a mark between 0 and 100.")

        except ValueError:
            print("Invalid input. Enter a numeric value.")

total, average, grade = calculate_result(marks)

print("\n--- Result ---")
print("Total:", total)
print("Average:", round(average, 2))
print("Grade:", grade)
7. Complexity Analysis
Let n be the number of subjects.

Time Complexity

O(n)
The program processes each mark once to calculate the total and validate the values.

Space Complexity

O(n)
The marks are stored in a list containing n elements.

For five subjects, the practical memory usage is constant, but the general algorithmic
space complexity is O(n).

8. Unit Tests
Python Unit Test Code
Python


Run
import unittest


def calculate_result(marks):
    if not marks:
        raise ValueError("Marks list cannot be empty.")

    if any(mark < 0 or mark > 100 for mark in marks):
        raise ValueError("Marks must be between 0 and 100.")

    total = sum(marks)
    average = total / len(marks)

    if average >= 90:
        grade = "A"
    elif average >= 75:
        grade = "B"
    elif average >= 60:
        grade = "C"
    elif average >= 50:
        grade = "D"
    else:
        grade = "F"

    return total, average, grade


class TestStudentMarks(unittest.TestCase):

    def test_grade_a(self):
        result = calculate_result([90, 95, 92, 91, 94])
        self.assertEqual(result[2], "A")

    def test_grade_b(self):
        result = calculate_result([75, 80, 78, 76, 79])
        self.assertEqual(result[2], "B")

    def test_grade_c(self):
        result = calculate_result([60, 65, 62, 61, 64])
        self.assertEqual(result[2], "C")

    def test_grade_d(self):
        result = calculate_result([50, 55, 52, 51, 54])
        self.assertEqual(result[2], "D")

    def test_grade_f(self):
        result = calculate_result([30, 40, 45, 35, 42])
        self.assertEqual(result[2], "F")

    def test_invalid_marks(self):
        with self.assertRaises(ValueError):
            calculate_result([90, 95, 110, 85, 90])


if __name__ == "__main__":
    unittest.main()
9. Comparison of AI Tools
Feature	ChatGPT	Gemini	Microsoft Copilot
Code Generation	Excellent	Excellent	Very Good
Debugging	Excellent	Very Good	Very Good
Code Explanation	Excellent	Excellent	Very Good
Optimization	Excellent	Very Good	Very Good
Unit Test Generation	Excellent	Very Good	Very Good
Complexity Analysis	Excellent	Excellent	Very Good
Ease of Use	Excellent	Excellent	Excellent

10. Manual Coding vs AI-Assisted Coding
Parameter	Manual Coding	AI-Assisted Coding
Development Speed	Moderate	Fast
Code Generation	Programmer writes code	AI generates code
Debugging	Manual	AI-assisted
Testing	Manual test creation	AI can generate tests
Learning	High	High with verification
Error Detection	Depends on programmer	Faster initial detection
Code Optimization	Manual	AI suggestions available
Accuracy	Depends on experience	Requires verification
Productivity	Moderate	High

11. Code Quality Analysis
The AI-generated programs were analyzed based on the following parameters:


1. Readability
2. Maintainability
3. Correctness
4. Error Handling
5. Efficiency
6. Testing
7. Code Structure
Evaluation
Parameter	Score / 5
Readability	5
Maintainability	4
Correctness	5
Error Handling	4
Efficiency	5
Testing	4
Code Structure	5

Total Score

32 / 35
The AI-generated code provides good quality and reduces development time. However, the
generated code must be reviewed and tested by the programmer before being used in a
real-world application.

Conclusion
AI-assisted programming tools can significantly improve software development by
generating source code, identifying bugs, optimizing programs, explaining complexity,
and creating unit tests. The Persona Pattern helped generate programming solutions from
the perspective of an experienced programmer.

The comparison of multiple AI tools showed that AI-assisted coding can improve
development speed and productivity, while manual verification is still necessary to
ensure correctness, security, and reliability.

Result
The corresponding prompt was successfully executed using multiple AI tools. Python, C,
and Java programs were generated, bugs were identified and corrected, the code was
optimized, complexity was analyzed, unit tests were generated, and manual coding was
compared with AI-assisted programming.








coding was compared with AI-assisted programming.
