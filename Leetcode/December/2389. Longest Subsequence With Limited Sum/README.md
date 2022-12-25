
<h2><a href="https://leetcode.com/problems/longest-subsequence-with-limited-sum/description/">2389. Longest Subsequence With Limited Sum</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
You are given an integer array nums of length n, and an integer array queries of length m.

Return an array answer of length m where answer[i] is the maximum size of a subsequence that you can take from nums such that the sum of its elements is less than or equal to queries[i].

A subsequence is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [4,5,2,1], queries = [3,10,21]
<strong>Output:</strong> [2,3,4]
</pre>
<pre>
 We answer the queries as follows:
- The subsequence [2,1] has a sum less than or equal to 3. It can be proven that 2 is the maximum size of such a subsequence, so answer[0] = 2.
- The subsequence [4,5,1] has a sum less than or equal to 10. It can be proven that 3 is the maximum size of such a subsequence, so answer[1] = 3.
- The subsequence [4,5,2,1] has a sum less than or equal to 21. It can be proven that 4 is the maximum size of such a subsequence, so answer[2] = 4.
  </pre>
  

 

Constraints:
<pre>
n == nums.length
m == queries.length
1 <= n, m <= 1000
1 <= nums[i], queries[i] <= 106
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    vector<int> answerQueries(vector<int>& nums, vector<int>& q) {
        sort(nums.begin(),nums.end());
        vector<int> ans;
        for(int i=0;i<q.size();i++)
        {
           int sum=0,count=0;
           for(int j=0;j<nums.size();j++)
           {
               sum+=nums[j];
               if(sum<=q[i]) count++;
               else break;
           }  
           ans.push_back(count);
        }
        return ans;
    }
};
          
 </pre>

