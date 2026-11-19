**Problem Name:** Coin Change (Count Ways)  
**Problem Link:** [GeeksforGeeks - Coin Change (Count Ways)](https://www.geeksforgeeks.org/problems/coin-change2448/1)

<!--### Brute Force Method-->

```java
class Solution {
    static Integer dp[][];
    public int count(int coins[], int sum) {
        int n = coins.length;
        dp = new Integer[n+1][sum+1];
        for(int j=0;j<sum+1;j++) {
            dp[0][j] = 0;
        }
        for(int i=0;i<n+1;i++) {
            dp[i][0] = 1;
        }
        for(int i=1;i<n+1;i++) {
            for(int j=1;j<sum+1;j++) {
                dp[i][j] = dp[i-1][j];
                dp[i][j] += j >= coins[i-1] ? dp[i][j-coins[i-1]] : 0;
            }
        }
        return dp[n][sum];
    }
}
```
