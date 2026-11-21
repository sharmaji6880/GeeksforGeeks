**Problem Name:** Longest Common Substring  
**Problem Link:** [GeeksforGeeks - Longest Common Substring](https://www.geeksforgeeks.org/problems/longest-common-substring1452/1)


```java
class Solution {
    public int longCommSubstr(String s1, String s2) {
        int m = s1.length(), n = s2.length();
        
        int[][] dp = new int[m+1][n+1];
        int result = 0;
        for(int i=1;i<m+1;i++) {
            for(int j=1;j<n+1;j++) {
                if(s1.charAt(i-1) == s2.charAt(j-1)) {
                    dp[i][j] = 1 + dp[i-1][j-1];
                    result = Math.max(result,dp[i][j]);
                }
            }
        }
        return result;
    }
}
```
