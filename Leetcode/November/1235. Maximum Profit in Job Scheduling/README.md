
<h2><a href="https://leetcode.com/problems/maximum-profit-in-job-scheduling/description/">1235. Maximum Profit in Job Scheduling</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 We have n jobs, where every job is scheduled to be done from startTime[i] to endTime[i], obtaining a profit of profit[i].

You're given the startTime, endTime and profit arrays, return the maximum profit you can take such that there are no two jobs in the subset with overlapping time range.

If you choose a job that ends at time X you will be able to start another job that starts at time X.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   startTime = [1,2,3,3], endTime = [3,4,5,6], profit = [50,10,40,70]
<strong>Output:</strong> 120
</pre>
<pre>
The subset chosen is the first and fourth job. 
Time range [1-3]+[3-6] , we get profit of 120 = 50 + 70.
  </pre>
  


Constraints:
<pre>
1 <= startTime.length == endTime.length == profit.length <= 5 * 104
1 <= startTime[i] < endTime[i] <= 109
1 <= profit[i] <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int jobScheduling(vector<int>& startTime, vector<int>& endTime, vector<int>& profit) {
        // step 1: generate the sorting index such that endTime[index[i]] <= endTime[index[i+1]] for 0 <= i < n-1
        auto comp = [&endTime](const int i1, const int i2) { return endTime[i1] < endTime[i2]; };
        int n = endTime.size();
        vector<int> index(n);
        iota(index.begin(), index.end(), 0);
        sort(index.begin(), index.end(), comp);
        
        // step 2: in order to perform binary search, we also need the sorting endTime array
        vector<int> endSorted(endTime.begin(), endTime.end());
        sort(endSorted.begin(), endSorted.end());
        
        // step 3: calculate dp table
        vector<int> dp(n + 1);
        for (int i = 1; i <= n; i++) {
            int j = upper_bound(endSorted.begin(), endSorted.end(), startTime[index[i-1]]) - endSorted.begin();
            dp[i] = max(dp[i-1], profit[index[i-1]] + dp[j]);
        }
        return dp[n];
    }
};
          
 </pre>

