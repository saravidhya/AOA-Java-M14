# EX 4B Frog Jump - Dynamic Programming.

## AIM:

To write a Java program to for given constraints.
A Frog Jump 1 or 2 steps at a time.
Problem Statement:

A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

Input Format:

A single integer n (1 ≤ n ≤ 45) – number of steps.
Output Format:

A single integer – number of distinct ways to reach step n.

## Algorithm

1. If `n` is 1 or 2, return `n` (base cases).
2. Initialize two variables to represent ways to reach previous two steps.
3. Iterate from step 3 to `n`, updating the current number of ways = sum of previous two.
4. Continue until reaching the n-th step.
5. Return the computed number of ways.

#### Developed By: Vidhiya Lakshmi S

#### Register Number: 212223230238

## Program:

### to implement number of distinct ways a frog can reach the n-th step

```java
import java.util.Scanner;

public class Main {

    public static int frogJumpWays(int n) {
        if (n == 1) return 1;
        if (n == 2) return 2;

        int a = 1, b = 2, c = 0;
        for (int i = 3; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return c;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        System.out.println(frogJumpWays(n));
        sc.close();
    }
}
```

## Output:

```
input: 5
output: 8
```

## Result:

The program successfully implemented and the expected output is verified.
