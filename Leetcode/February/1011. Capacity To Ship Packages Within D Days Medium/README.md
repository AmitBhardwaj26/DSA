
<h2><a href="https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/">1011. Capacity To Ship Packages Within D Days</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
A conveyor belt has packages that must be shipped from one port to another within days days.

The ith package on the conveyor belt has a weight of weights[i]. Each day, we load the ship with packages on the conveyor belt (in the order given by weights). We may not load more weight than the maximum weight capacity of the ship.

Return the least weight capacity of the ship that will result in all the packages on the conveyor belt being shipped within days days.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  weights = [1,2,3,4,5,6,7,8,9,10], days = 5
<strong>Output:</strong> 15
</pre>
<pre>
Explanation:  A ship capacity of 15 is the minimum to ship all the packages in 5 days like this:
1st day: 1, 2, 3, 4, 5
2nd day: 6, 7
3rd day: 8
4th day: 9
5th day: 10

Note that the cargo must be shipped in the order given, so using a ship of capacity 14 and splitting the packages into parts like (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) is not allowed.
  </pre>


Constraints:
<pre>
1 <= days <= weights.length <= 5 * 104
1 <= weights[i] <= 500
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:

    int numberofdays(vector<int> &wt,int mid,int days)
    {
        int count=1,sum=0;
        for(int i=0;i<wt.size();i++)
        {
            if(sum+wt[i]<=mid)                sum+=wt[i];
            else 
            {
                sum=wt[i];
                 count++;
            }
        }
       return count;
    } 
    int shipWithinDays(vector<int>& wt, int days) {
        
        int l=0,r=0;
        for(int i=0;i<wt.size();i++) 
        {
            l=max(l,wt[i]);
            r+=wt[i];
        }
        int ans=r;
        while(l<=r)
        {
            int mid=l+(r-l)/2, check=numberofdays(wt,mid,days);
            //cout<<mid<<" "<<check<<"\n";
            if(check<=days) { ans=min(ans,mid); r=mid-1; }
            else l=mid+1;  
        }
        return ans;
    }
};
          
 </pre>

