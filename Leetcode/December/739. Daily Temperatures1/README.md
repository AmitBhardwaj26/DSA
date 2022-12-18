
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">739. Daily Temperatures</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    temperatures = [73,74,75,71,69,72,76,73]
<strong>Output:</strong> [1,1,4,2,1,1,0,0]
</pre>

 

Constraints:
<pre>
1 <= temperatures.length <= 105
30 <= temperatures[i] <= 100
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temp) {
        int n=temp.size();
        vector<int> ans(n,0);
        for(int i=n-1;i>=0;i--)
        {
            int j=i+1; bool check=1;
            while(j<n and temp[i]>=temp[j] ) 
            {
                if(ans[j]==0) {ans[i]=0; check=0; break;}
                j=ans[j]+j;  
            }
            if(j<n and check) ans[i]=j-i; 
        }
        return ans;
    }
};
          
 </pre>

