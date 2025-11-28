# EX 4C Coin Change Problem - Dynamic Programming.

## AIM:

To write a Java program to for given constraints.
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

## Algorithm

1. Initialize a DP array `dp` of size `amount + 1` with all values as `amount + 1` (infinity-like), and set `dp[0] = 0`.
2. Loop through all amounts from 1 to `amount`.
3. For each coin in `coins`, if the coin ≤ current amount, update `dp[i] = Math.min(dp[i], dp[i - coin] + 1)`.
4. After filling the DP array, check if `dp[amount] > amount`; if so, return -1.
5. Otherwise, return `dp[amount]` as the minimum number of coins needed.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement coin change

```java
import java.util.Scanner;
import java.util.Arrays;

public class Main {

    public static int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1);
        dp[0] = 0;

        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (coin <= i) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }

        return dp[amount] > amount ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of coin types: ");
        int n = sc.nextInt();
        int[] coins = new int[n];

        System.out.println("Enter the coin denominations:");
        for (int i = 0; i < n; i++) coins[i] = sc.nextInt();

        System.out.print("Enter the amount: ");
        int amount = sc.nextInt();

        System.out.println("Minimum coins needed: " + coinChange(coins, amount));
        sc.close();
    }
}
```

## Output:

```
input:
Enter number of coin types: 3
Enter the coin denominations:
1 2 5
Enter the amount: 11

output:
Minimum coins needed: 3
```

## Result:

The program successfully implemented and the expected output is verified.
