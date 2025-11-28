# EX 4E Longest Increasing Subsequence - Dynamic Programming.

## AIM:

To write a Java program to for given constraints.
Given an integer array nums, return the length of the longest strictly increasing subsequence.
Example 1:
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.

## Algorithm

1. Initialize a `dp` array of size `n` with all values set to 1 (each element is a subsequence of length 1).
2. Loop through the array from left to right. For each `nums[i]`, check all previous elements `nums[j]` where `j < i`.
3. If `nums[i] > nums[j]`, update `dp[i] = Math.max(dp[i], dp[j] + 1)`.
4. Keep track of the maximum value in the `dp` array.
5. Return the maximum value as the length of the LIS.
   
#### Developed By: VIDHIYA LAKSHMI S
#### Register Number: 212223230238
## Program:

### to implement longest strictly increasing subsequence

```java
import java.util.Scanner;

public class Main {

    public static int lengthOfLIS(int[] nums) {
        int n = nums.length;
        int[] dp = new int[n];
        int maxLen = 0;

        for (int i = 0; i < n; i++) {
            dp[i] = 1;
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLen = Math.max(maxLen, dp[i]);
        }

        return maxLen;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        int[] nums = new int[n];

        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < n; i++) nums[i] = sc.nextInt();

        System.out.println("Length of longest increasing subsequence: " + lengthOfLIS(nums));
        sc.close();
    }
}
```

## Output:

```
input:
Enter number of elements: 8
Enter the elements of the array:
10 9 2 5 3 7 101 18

output:
Length of longest increasing subsequence: 4
```

## Result:

The program successfully implemented and the expected output is verified.
