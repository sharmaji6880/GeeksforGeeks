**Problem Name:** Minimum Deletions for Palindrome  
**Problem Link:** [GeeksforGeeks - Minimum Deletions for Palindrome](https://www.geeksforgeeks.org/problems/minimum-deletitions1648/1)


```java
class Solution {
    static int minDeletions(String s) {
        int n = s.length();
        String reverse = "";
        for(int i=n-1;i>=0;i--) {
            reverse += s.charAt(i);
        }
        
        int[][] dp = new int[n+1][n+1];
        
        for(int i=1;i<n+1;i++) {
            for(int j=1;j<n+1;j++) {
                if(s.charAt(i-1) == reverse.charAt(j-1)) {
                    dp[i][j] = 1 + dp[i-1][j-1];
                }else {
                    dp[i][j] = Math.max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return n - dp[n][n];
        
    }
}
```
