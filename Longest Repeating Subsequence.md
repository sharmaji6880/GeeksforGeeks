**Problem Name:** Longest Repeating Subsequence  
**Problem Link:** [GeeksforGeeks - Longest Repeating Subsequence](https://www.geeksforgeeks.org/problems/longest-repeating-subsequence2004/1)


```java
class Solution {
    public int longestRepSubseq(String s) {
        int n = s.length();
        
        int[][] dp = new int[n+1][n+1];
        
        for(int i=1;i<n+1;i++) {
            for(int j=1;j<n+1;j++) {
                if(s.charAt(i-1) == s.charAt(j-1) && i!=j) {
                    dp[i][j] = 1 + dp[i-1][j-1];
                }else {
                    dp[i][j] = Math.max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return dp[n][n];
        
    }
}
```
