# EX 4D Longest Common SubSequence - Dynamic Programming.

## AIM:

To write a Java program to for given constraints.
Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.
A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.

Input: text1 = "abcde", text2 = "ace"
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
Constraints:

1 <= text1.length, text2.length <= 1000
text1 and text2 consist of only lowercase English characters.

## Algorithm

1. Create a 2D DP array `dp[m+1][n+1]`, where `m = text1.length()` and `n = text2.length()`.
2. Initialize the first row and first column to 0 (base cases).
3. Loop through both strings:
   - If `text1[i-1] == text2[j-1]`, set `dp[i][j] = dp[i-1][j-1] + 1`.
   - Otherwise, set `dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1])`.
4. Continue until the entire DP table is filled.
5. Return `dp[m][n]` as the length of the longest common subsequence.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement Longest Common Subsequence (LCS)

```java
import java.util.Scanner;

public class Main {

    public static int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter first string: ");
        String text1 = sc.nextLine();
        System.out.print("Enter second string: ");
        String text2 = sc.nextLine();

        System.out.println("Length of LCS: " + longestCommonSubsequence(text1, text2));
        sc.close();
    }
}
```

## Output:

```
input:
Enter first string: abcde
Enter second string: ace

output:
Length of LCS: 3
```

## Result:

The program successfully implemented and the expected output is verified.
