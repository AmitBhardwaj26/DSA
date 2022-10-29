
<h2><a href="https://leetcode.com/problems/earliest-possible-day-of-full-bloom/description/">2136. Earliest Possible Day of Full Bloom</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
  
You have n flower seeds. Every seed must be planted first before it can begin to grow, then bloom. Planting a seed takes time and so does the growth of a seed. You are given two 0-indexed integer arrays plantTime and growTime, of length n each:

plantTime[i] is the number of full days it takes you to plant the ith seed. Every day, you can work on planting exactly one seed. You do not have to work on planting the same seed on consecutive days, but the planting of a seed is not complete until you have worked plantTime[i] days on planting it in total.
growTime[i] is the number of full days it takes the ith seed to grow after being completely planted. After the last day of its growth, the flower blooms and stays bloomed forever.
From the beginning of day 0, you can plant the seeds in any order.

Return the earliest possible day where all seeds are blooming.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   plantTime = [1,4,3], 
<strong>Output:</strong> growTime = [2,3,1]
</pre>
<pre>
The grayed out pots represent planting days, colored pots represent growing days, and the flower represents the day it blooms.
One optimal way is:
On day 0, plant the 0th seed. The seed grows for 2 full days and blooms on day 3.
On days 1, 2, 3, and 4, plant the 1st seed. The seed grows for 3 full days and blooms on day 8.
On days 5, 6, and 7, plant the 2nd seed. The seed grows for 1 full day and blooms on day 9.
Thus, on day 9, all the seeds are blooming.
  </pre>
  


Constraints:
<pre>
n == plantTime.length == growTime.length
1 <= n <= 105
1 <= plantTime[i], growTime[i] <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         // main concept is sort with growtime with max sum planttime +growtime in end
        class Solution {
        public:
            int earliestFullBloom(vector<int>& p, vector<int>& g) {
                vector<pair<int,int>> v;
                for(int i=0;i<p.size();i++)
                {
                    v.push_back({g[i],p[i]});
                }
                sort(v.begin(),v.end(),[](pair<int,int> p1 ,pair<int,int> p2){
                    return p1.first>p2.first;
                } );
                int ans=0,start=0;
                for(int i=0;i<v.size();i++)
                {
                     start+=v[i].second;
                     ans=max(ans,start+v[i].first); // most imp line
                }
                return ans;
            }
        };
          
 </pre>

