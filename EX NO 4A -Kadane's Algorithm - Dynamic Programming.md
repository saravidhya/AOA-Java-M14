
# EX 4A Kadane's Algorithm - Dynamic Programming.

## AIM:

To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6

## Algorithm

1. Compute the maximum subarray sum using standard Kadane’s Algorithm (`max_kadane`).
2. Compute the total sum of the array and find the minimum subarray sum (`min_kadane`).
3. Maximum circular sum = total sum − minimum subarray sum.
4. Handle the edge case: if all numbers are negative, `max_circular` would be 0, so return `max_kadane`.
5. The result = `Math.max(max_kadane, max_circular)`.

#### Developed By: Vidhiya Lakshmi S

#### Register Number: 212223230238

## Program:

### to implement kandanes algorithm

```java
import java.util.Scanner;

public class Main {

    public static int kadane(int[] arr) {
        int maxEnding = arr[0];
        int maxSoFar = arr[0];
        for (int i = 1; i < arr.length; i++) {
            maxEnding = Math.max(arr[i], maxEnding + arr[i]);
            maxSoFar = Math.max(maxSoFar, maxEnding);
        }
        return maxSoFar;
    }

    public static int maxCircularSum(int[] arr) {
        int max_kadane = kadane(arr);

        int total = 0;
        for (int i = 0; i < arr.length; i++) total += arr[i];

        // Invert the array for finding minimum subarray sum
        for (int i = 0; i < arr.length; i++) arr[i] = -arr[i];

        int max_inverted = kadane(arr);
        int max_circular = total + max_inverted; // total - min_subarray

        if (max_circular == 0) return max_kadane; // all negative numbers

        return Math.max(max_kadane, max_circular);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = sc.nextInt();

        System.out.println(maxCircularSum(arr));
        sc.close();
    }
}
```

## Output:

```
input: 5
8 -1 3 4 -5
output 14
```

## Result:

The program successfully Implemented and the output is verified.
