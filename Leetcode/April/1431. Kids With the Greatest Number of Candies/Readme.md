
<h2><a href="https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/">1431. Kids With the Greatest Number of Candies</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are n kids with candies. You are given an integer array candies, where each candies[i] represents the number of candies the ith kid has, and an integer extraCandies, denoting the number of extra candies that you have.

Return a boolean array result of length n, where result[i] is true if, after giving the ith kid all the extraCandies, they will have the greatest number of candies among all the kids, or false otherwise.

Note that multiple kids can have the greatest number of candies.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> candies = [2,3,5,1,3], extraCandies = 3
<strong>Output:</strong>[true,true,true,false,true] 
</pre>
<pre>
Explanation: If you give all extraCandies to:
- Kid 1, they will have 2 + 3 = 5 candies, which is the greatest among the kids.
- Kid 2, they will have 3 + 3 = 6 candies, which is the greatest among the kids.
- Kid 3, they will have 5 + 3 = 8 candies, which is the greatest among the kids.
- Kid 4, they will have 1 + 3 = 4 candies, which is not the greatest among the kids.
- Kid 5, they will have 3 + 3 = 6 candies, which is the greatest among the kids.
  </pre>


Constraints:
<pre>
n == candies.length
2 <= n <= 100
1 <= candies[i] <= 100
1 <= extraCandies <= 50
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    vector<bool> kidsWithCandies(vector<int>& can, int e) {
        vector<bool> ans;
        int Ma=*max_element(can.begin(),can.end());
        for(int i=0;i<can.size();i++)
        {
          if(can[i]+e>=Ma) ans.push_back(true);
          else ans.push_back(false);
        }
        return ans;
    }
};
 </pre>

