
<h2><a href="https://leetcode.com/problems/find-the-longest-valid-obstacle-course-at-each-position/description/">1964. Find the Longest Valid Obstacle Course at Each Position</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You want to build some obstacle courses. You are given a 0-indexed integer array obstacles of length n, where obstacles[i] describes the height of the ith obstacle.

For every index i between 0 and n - 1 (inclusive), find the length of the longest obstacle course in obstacles such that:

You choose any number of obstacles between 0 and i inclusive.
You must include the ith obstacle in the course.
You must put the chosen obstacles in the same order as they appear in obstacles.
Every obstacle (except the first) is taller than or the same height as the obstacle immediately before it.
Return an array ans of length n, where ans[i] is the length of the longest obstacle course for index i as described above.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   obstacles = [1,2,3,2]
<strong>Output:</strong> [1,2,3,3]
</pre>
<pre>
Explanation: The longest valid obstacle course at each position is:
- i = 0: [1], [1] has length 1.
- i = 1: [1,2], [1,2] has length 2.
- i = 2: [1,2,3], [1,2,3] has length 3.
- i = 3: [1,2,3,2], [1,2,2] has length 3.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
n == obstacles.length
1 <= n <= 105
1 <= obstacles[i] <= 107
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 //`the question is simple based on the approach of longest increasing subsequenece 
// as there are duplicate elements can be present that why use upper bound intead of lower bound at each point iterator is the answer
class Solution {
public:
    vector<int> longestObstacleCourseAtEachPosition(vector<int>& obs) {
        int n=obs.size();
        vector<int> ans;
        vector<int> dp;

        dp.push_back(obs[0]); 
        ans.push_back(1);
        
        for(int i=1;i<n;i++)
        {
            if(dp.back()<=obs[i]) 
            {
              dp.push_back(obs[i]); 
              ans.push_back(dp.size());
            }
            else
            {
                 int it=upper_bound(dp.begin(),dp.end(),obs[i])-dp.begin();
                //cout<<it<<" ";
                 dp[it]=obs[i];
                ans.push_back(it+1);  
            }
        }
        return ans;
    }
};
 </pre>

