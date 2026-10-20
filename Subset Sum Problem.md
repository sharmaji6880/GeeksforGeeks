> **Problem Name:** Subset Sum Problem  
> **Problem Link:** [https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1](https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1)  


    // Bottom Up DP Approach
    class Solution {
        static Boolean[][] dp;
        static boolean isSubsetSum(int arr[], int sum) {
            int n = arr.length;
            dp = new Boolean[n+1][sum+1];
            for(int j=0;j<sum+1;j++) {
                dp[0][j] = false;
            }
            for(int i=0;i<n+1;i++) {
                dp[i][0] = true;
            }
            for(int i=1;i<n+1;i++) {
                for(int j=1;j<sum+1;j++) {
                    dp[i][j] = (j >= arr[i-1] ? dp[i-1][j-arr[i-1]]:false) || dp[i-1][j];
                    
                }
            }
            
            return dp[n][sum];
        }
    }