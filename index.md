## Week 9 - Lab Report 5

**Part 1**

**Student:**

Subject: "Error Running JUnit Tests in Bash Script"

Hi everyone,

I'm trying to run JUnit tests using a bash script, but I keep encountering a strange issue. When I execute the script, it throws an error related to the classpath. I've attached a screenshot of the error message. My guess is that there might be an issue with the way I'm setting the classpath, but I can't pinpoint the exact problem. Any help would be appreciated!

<img width="799" alt="Screenshot 2023-12-03 at 10 19 07 PM" src="https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/1c9836c8-26c8-4a4f-8e26-0d87a27dc0a6">


**TA's Response:**

t looks like there might be an issue with how the classpath is defined in your script. Can you try updating the java command to ensure that the classpath is correctly specified? Specifically, check if there are any unnecessary characters or syntax errors in the classpath definition.

`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`
`java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore test`

The original script had an error in the classpath (..:lib/hamcrest-core-1.3.jar..:lib/junit-4.13.2.jar), which should be .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar. And also it needs to be test at the end and not test.class.

**Student:**

Subject: "JUnit Test Failing for reverseInPlace Method"

Hi all,

I've written a reverseInPlace method in Java and created JUnit tests to check its functionality. However, both of the tests keeps failing, and I'm not sure why. The method is supposed to reverse an array in place, but it seems to be doing something else. Here's a screenshot of the test result after running the bash script.

<img width="772" alt="Screenshot 2023-12-03 at 10 24 20 PM" src="https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/40387338-6715-4b3e-9360-2b20c1ebcccc">

My test code:

<img width="442" alt="Screenshot 2023-12-03 at 10 23 50 PM" src="https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/901c828c-9b2d-4ec3-96c5-3e6ac10c9c4d">

My code for reversing it:

<img width="400" alt="Screenshot 2023-12-03 at 10 25 26 PM" src="https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/b4aa8ae9-a74d-4e30-a81e-aaa331d35523">

**TA's Response:**

Based on the test result, it seems like the reverseInPlace method might not be reversing the array correctly. Could you check if your loop in the method correctly swaps the elements? Remember, you need to iterate only halfway through the array and swap elements from the start and end.

**Debugging Steps and Solution:**

After reviewing the reverseInPlace method, the student realizes that the loop is incorrectly replacing each element with the element from the end of the array without swapping them. The correct implementation would be:

    public class student {
        static void reverseInPlace(int [] arr) {
            for (int i = 0; i < arr.length / 2; i++) {
                int temp = arr[i];
                arr[i] = arr[arr.length - i - 1];
                arr[arr.length - i - 1] = temp;
            }
        }
    }

This change ensures that the array elements are properly swapped, and the method works as intended.

<img width="218" alt="Screenshot 2023-12-03 at 10 31 42 PM" src="https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/f860d748-c012-47db-a724-843933d6c95b">

Setup Information

File & Directory Structure:

`test.java`

`student.java`

`test.sh`

lib/ (contains JUnit and Hamcrest jar files)

Contents of Each File Before Fixing the Bug:

`test.java`: Contains JUnit tests for reverseInPlace method.

    import static org.junit.Assert.*;
    import org.junit.*;
    
    public class test {
        @Test
        public void testReverseInPlace() {
            int [] arr = {1, 2, 3, 4, 5};
            student.reverseInPlace(arr);
            assertArrayEquals(new int [] {5, 4, 3, 2, 1}, arr);
        }
    
        @Test
        public void testReverseInPlace2() {
            int [] arr = {1, 2, 3, 4};
            student.reverseInPlace(arr);
            assertArrayEquals(new int [] {4, 3, 2, 1}, arr);
        }
    }

`student.java`: Contains incorrect implementation of reverseInPlace.

    public class student {
        static void reverseInPlace(int [] arr) {
            for (int i = 0; i < arr.length; i += 1 ) {
                arr[i] = arr[arr.length - i -1];
            }
        }
    }

`test.sh`: Incorrect classpath in the java command.

`set -e
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp ..:lib/hamcrest-core-1.3.jar..:lib/junit-4.13.2.jar org.junit.runner.JUnitCore test.class`

Command Line to Trigger the Bug:

Run ` bash test.sh` in the terminal.

Description of What to Edit to Fix the Bug:

In `test.sh`, correct the classpath in the java command.

`set -e
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore test`

In `student.java`, update the reverseInPlace method to correctly swap elements.

    public class student {
        static void reverseInPlace(int [] arr) {
            for (int i = 0; i < arr.length / 2; i++) {
                int temp = arr[i];
                arr[i] = arr[arr.length - i - 1];
                arr[arr.length - i - 1] = temp;
            }
        }
    }


**Part 2**

Reflecting on the latter half of this quarter, I realized that the lab experience was not just about learning new technical skills, but also about developing a more refined approach to problem-solving in software development. Here are some key learnings:

**Advanced Debugging Techniques:**

I learned about more sophisticated debugging tools beyond the basic print statements, such as interactive debuggers in IDEs. These tools allowed me to step through code, examine variable states at different execution points, and understand the flow of the program in real-time. This deeper exploration into debugging helped me understand the nuances of how code executes, especially in complex scenarios.

**Importance of Unit Testing:**

Previously, I viewed unit testing as a chore. However, through lab exercises, I realized its critical role in ensuring code quality. I learned how to write effective test cases and use testing frameworks like JUnit. This practice helped me catch bugs early in the development cycle, saving time and effort in the long run.

**Version Control Best Practices:**

Working on labs, I learned to use version control systems like Git more effectively. Understanding branching strategies, merge conflicts, and the importance of committing changes frequently were crucial lessons. These practices are vital for collaboration in a team setting and for maintaining a clean and efficient development workflow.
