 **Problem Name:** Shortest Common Supersequence  
**Problem Link:** [GeeksforGeeks - Shortest Common Supersequence](https://www.geeksforgeeks.org/problems/shortest-common-supersequence0322/1)


```java
class Solution {
    public static int minSuperSeq(String s1, String s2) {
        int m = s1.length(), n = s2.length();
        
        int[][] dp = new int[m+1][n+1];
        
        for(int i=1;i<m+1;i++) {
            for(int j=1;j<n+1;j++) {
                if(s1.charAt(i-1) == s2.charAt(j-1)) {
                    dp[i][j] = 1 + dp[i-1][j-1];
                }else {
                    dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
        }
        return m + n - dp[m][n];
        
    }
}
```
