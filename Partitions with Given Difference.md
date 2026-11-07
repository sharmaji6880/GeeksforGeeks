**Problem Name:** Partitions with Given Difference  
**Problem Link:** [GeeksforGeeks - Partitions with Given Difference](https://www.geeksforgeeks.org/problems/partitions-with-given-difference/1)


```java
class Solution {
    public int countPartitions(int[] arr, int diff) {
        int n = arr.length, sum = 0;
        
        for(int num:arr) sum+=num;
        
        if( (sum+diff) % 2 != 0 || sum + diff < 0) return 0;
        
        int target = (sum+diff) / 2;
        
        if(target > sum ) return 0;
        
        int [][] dp = new int [n+1][sum+1];
        
        dp[0][0] = 1;
        
        
        for(int i=1;i<n+1;i++) {
            for(int j=0;j<sum+1;j++) {
                dp[i][j] = dp[i-1][j] + ( j >= arr[i-1] ? dp[i-1][j-arr[i-1]] : 0);
            }
        }
        
        return dp[n][(sum+diff)/2];
        
    }
}

```
