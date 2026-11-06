**Problem Name:** Partition Into 2 Subsets with Min Sum Diff  
**Problem Link:** [GeeksforGeeks - Partition Into 2 Subsets with Min Sum Diff](https://www.geeksforgeeks.org/problems/minimum-sum-partition3317/1)


```java
class Solution {
	static Boolean[][] dp;
	public int minDifference(int arr[]) {
		int n = arr.length;
		int sum = 0;
		for(int num:arr) sum += num;
		dp = new Boolean[n + 1][sum + 1];
		
		for (int j = 0; j<sum + 1; j++) {
			dp[0][j] = false;
		}
		for (int i = 0; i<n + 1; i++) {
			dp[i][0] = true;
		}
		for (int i = 1; i<n + 1; i++) {
			for (int j = 1; j<sum + 1; j++) {
				dp[i][j] = dp[i - 1][j] ||
				(j >= arr[i - 1] ? dp[i - 1][j - arr[i - 1]] : false);
			}
		}
		
		
		for(int j=sum/2;j>=0;j--) {
		    if(dp[n][j] == true) {
		        return sum - (2 * j);
		    }
		}
		return -1;
		
	}
}

```
