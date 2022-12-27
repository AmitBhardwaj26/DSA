
<h2><a href="https://leetcode.com/problems/maximum-bags-with-full-capacity-of-rocks/description/">2279. Maximum Bags With Full Capacity of Rocks</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You have n bags numbered from 0 to n - 1. You are given two 0-indexed integer arrays capacity and rocks. The ith bag can hold a maximum of capacity[i] rocks and currently contains rocks[i] rocks. You are also given an integer additionalRocks, the number of additional rocks you can place in any of the bags.

Return the maximum number of bags that could have full capacity after placing the additional rocks in some bags.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   capacity = [2,3,4,5], rocks = [1,2,4,4], additionalRocks = 2
<strong>Output:</strong> 3
</pre>
<pre>
Place 1 rock in bag 0 and 1 rock in bag 1.
The number of rocks in each bag are now [2,3,4,4].
Bags 0, 1, and 2 have full capacity.
There are 3 bags at full capacity, so we return 3.
It can be shown that it is not possible to have more than 3 bags at full capacity.
Note that there may be other ways of placing the rocks that result in an answer of 3.
  </pre>


Constraints:
<pre>
n == capacity.length == rocks.length
1 <= n <= 5 * 104
1 <= capacity[i] <= 109
0 <= rocks[i] <= capacity[i]
1 <= additionalRocks <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
public:
    int maximumBags(vector<int>& c, vector<int>& rocks, int b) {
        vector<int>v;
        for(int i=0;i<rocks.size();i++)     v.push_back(c[i]-rocks[i]);
        sort(v.begin(),v.end());
        int i=0;
        while(b>0 and i<c.size()){
            b-=v[i];
            i++;
        }
        return b<0 ? i-1 : i;
    }
};
          
 </pre>

