**Problem Name:** Target Sum  
**Problem Link:** [GeeksforGeeks - Target Sum](https://www.geeksforgeeks.org/problems/target-sum-1626326450/1)


```java
class Solution {
    Integer[][] dp;
    public int totalWays(int[] arr, int target) {
        int n = arr.length;
        dp =  new Integer[n+1][2001];
        for(int i=0;i<n+1;i++) {
            for(int j=0;j<2001;j++) { 
                if(i==0) {
                    dp[i][j] = j==1000? 1 : 0;
                    continue;
                }
                int choice1 = (j-arr[i-1] < 0 || j-arr[i-1] > 2000) ? 0 : dp[i-1][j-arr[i-1]];
                int choice2 = (j+arr[i-1] < 0 || j+arr[i-1] > 2000) ? 0 : dp[i-1][j+arr[i-1]];
                dp[i][j] = choice1 + choice2;
            }
            
        }
        return dp[n][target+1000];
    }
}
```
