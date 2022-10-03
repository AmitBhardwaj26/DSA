
<h2><a href="https://leetcode.com/problems/minimum-time-to-make-rope-colorful/description/">1578. Minimum Time to Make Rope Colorful</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Alice has n balloons arranged on a rope. You are given a 0-indexed string colors where colors[i] is the color of the ith balloon.

Alice wants the rope to be colorful. She does not want two consecutive balloons to be of the same color, so she asks Bob for help. Bob can remove some balloons from the rope to make it colorful. You are given a 0-indexed integer array neededTime where neededTime[i] is the time (in seconds) that Bob needs to remove the ith balloon from the rope.

Return the minimum time Bob needs to make the rope colorful.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> colors = "abaac", neededTime = [1,2,3,4,5]
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: In the above image, 'a' is blue, 'b' is red, and 'c' is green.
Bob can remove the blue balloon at index 2. This takes 3 seconds.
There are no longer two consecutive balloons of the same color. Total time = 3.
  </pre>
  
Example 2:

Input: colors = "abc", neededTime = [1,2,3]
Output: 0
 

Constraints:
<pre>
n == colors.length == neededTime.length
1 <= n <= 105
1 <= neededTime[i] <= 104
colors contains only lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int minCost(string col, vector<int>& nt) {
        int ans=0,z=nt[0],sum=nt[0];
        // priority_queue<int,vector<int>,greater<int>()> pq; 
        for(int i=1;i<col.size();i++)
        {
            sum+=nt[i];
            if(col[i]==col[i-1]) z=max(z,nt[i]);
            else 
            {
                ans+=z;
                z=nt[i];
            }
        }
        return sum-ans-z;
    }
};
          
 </pre>

