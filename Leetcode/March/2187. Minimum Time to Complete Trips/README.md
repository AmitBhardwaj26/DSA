
<h2><a href="https://leetcode.com/problems/minimum-time-to-complete-trips/">2187. Minimum Time to Complete Trips</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an array time where time[i] denotes the time taken by the ith bus to complete one trip.

Each bus can make multiple trips successively; that is, the next trip can start immediately after completing the current trip. Also, each bus operates independently; that is, the trips of one bus do not influence the trips of any other bus.

You are also given an integer totalTrips, which denotes the number of trips all buses should make in total. Return the minimum time required for all buses to complete at least totalTrips trips.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   time = [1,2,3], totalTrips = 5
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: - At time t = 1, the number of trips completed by each bus are [1,0,0]. 
  The total number of trips completed is 1 + 0 + 0 = 1.
- At time t = 2, the number of trips completed by each bus are [2,1,0]. 
  The total number of trips completed is 2 + 1 + 0 = 3.
- At time t = 3, the number of trips completed by each bus are [3,1,1]. 
  The total number of trips completed is 3 + 1 + 1 = 5.
So the minimum time needed for all buses to complete at least 5 trips is 3.
  </pre>


Constraints:
<pre>
1 <= time.length <= 105
1 <= time[i], totalTrips <= 107
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
#define ll long long
   ll cal(ll mid ,vector<int> &time)
   {
       ll count=0;
       for(int i=0;i<time.size();i++)
       {
           count+=mid/time[i];
       }
       return count;
   }
    long long minimumTime(vector<int>& time, ll total) {
        sort(time.begin(),time.end());
        ll l=time[0], r=time[0]*total, ans=r;
        while(l<=r)
        {
            ll mid=l+(r-l)/2;
            if(cal(mid,time) >=total) 
            {
                ans=min(ans,mid); r=mid-1;
            }
            else l=mid+1;
        }
        return ans;
    }
};
 </pre>

