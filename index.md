# Lab Report 5
------------------
# Part 1 – Debugging Scenario
## NEW QUESTION

#### -What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?

Apple MacBook Pro, using visual studio.

#### -Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.

#### -Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.

The syptom is that my coding goes to failed for bash test script even though I think my coding is correct.

JAVA file
```
import java.util.Scanner;

public class SumCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("First number: ");
        int num1 = scanner.nextInt();

        System.out.print("Second number: ");
        int num2 = scanner.nextInt();

        int sum = num1 + num2;
        System.out.println("Sum: " + sum);
    }
}
```

Tester.bash
```
javac SumCalculator.java


if [ $1 -eq 0 ]; then
    echo "Java file successfully open!"

    java SumCalculator
else
    echo "failed"
fi
```

Output:
```
Frankie-Chiude-MacBook-Pro:~ frankiechiu$ bash Tester.sh
Tester.sh: line 7: [: -eq: unary operator expected
failed
```
----------------------
## ANSWER QUESTION

To fix the code, please try to see the argument of the main code and the bash file and check if the bash file code is correct for the condition!

For the bash file, I change $1 to $?. $1 means that the first argument of the code is going over the bash file, and $? means that find the return value that the code is operate, so $? is good since there are no argument inside the main code.

Fixed Code:
```
javac SumCalculator.java


if [ $? -eq 0 ]; then
    echo "Java file successfully open!"

    java SumCalculator
else
    echo "failed"
fi
```

Output:
```
Frankie-Chiude-MacBook-Pro:~ frankiechiu$ bash Tester.sh
Java file successfully open!
first number: 3
second number: 2
Sum: 5
```

Using [What is echo $1 in Bash - Java2Blog](https://java2blog.com/echo-1-bash/) and
[Special Variables in Bash Scripting - Knoldus Blogs](https://blog.knoldus.com/special-variables-in-bash-scripting/) for reference!


# Part 2 – Reflection

For this ten-week course, I learned how to operate the computer faster! I did not even know how to use those skills before I enrolled in this class! The most interesting material I learned is 
Vim. It can help us more effective to edit, delete and add without open the comprehensive file. Thank you everyone for helping me learn more about the computer skills.

-----------------------

-Thanks for watching!

-LAB REPORT END-


