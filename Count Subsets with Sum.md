> **Problem Name:** Count Subsets with Sum  
> **Problem Link:** [https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1](https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1)  


    class Solution {
        static Integer[][] dp;
        static int perfectSum(int[] arr, int target) {
            int n = arr.length;
            dp = new Integer[n+1][target+1];
            for(int i=0;i<n+1;i++) {
                for(int j=0;j<target+1;j++) {
                    if(i==0) {
                        dp[i][j] = j == 0 ? 1 : 0;
                        continue;
                    }
                    dp[i][j] = (j >= arr[i-1] ? dp[i-1][j-arr[i-1]] : 0) + dp[i-1][j];
                }
            }
            return dp[n][target];
        }
    }
    
    