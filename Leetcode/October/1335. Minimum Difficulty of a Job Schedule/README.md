
<h2><a href="https://leetcode.com/problems/minimum-difficulty-of-a-job-schedule/description/">1335. Minimum Difficulty of a Job Schedule</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
You want to schedule a list of jobs in d days. Jobs are dependent (i.e To work on the ith job, you have to finish all the jobs j where 0 <= j < i).

You have to finish at least one task every day. The difficulty of a job schedule is the sum of difficulties of each day of the d days. The difficulty of a day is the maximum difficulty of a job done on that day.

You are given an integer array jobDifficulty and an integer d. The difficulty of the ith job is jobDifficulty[i].
Return the minimum difficulty of a job schedule. If you cannot find a schedule for the jobs return -1.
  </p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   jobDifficulty = [6,5,4,3,2,1], d = 2
<strong>Output:</strong>7
</pre>
<pre>
First day you can finish the first 5 jobs, total difficulty = 6.
Second day you can finish the last job, total difficulty = 1.
The difficulty of the schedule = 6 + 1 = 7
  </pre>

 

Constraints:
<pre>
1 <= jobDifficulty.length <= 300
0 <= jobDifficulty[i] <= 1000
1 <= d <= 10
</pre>
<hr>
 
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int t[301][11];
    int solve(vector<int>& mat, int n, int idx, int d) {
        if(d == 1)
            return *max_element(begin(mat)+idx, end(mat));
        
        if(t[idx][d] != -1)
            return t[idx][d];
    
        
        int Max = INT_MIN;
        int result = INT_MAX;
        
        for(int i = idx; i<=n-d; i++) {
            Max = max(Max, mat[i]);
            result = min(result, Max + solve(mat, n, i+1, d-1));
        }
        return t[idx][d] = result;
    }
    
    int minDifficulty(vector<int>& jobDifficulty, int d) {
        int n = jobDifficulty.size();
        if(n < d)
            return -1;
        memset(t, -1, sizeof(t));
        return solve(jobDifficulty, n, 0, d);
    }
};
          
 </pre>

