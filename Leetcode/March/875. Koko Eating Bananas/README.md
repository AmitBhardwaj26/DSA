
<h2><a href="https://leetcode.com/problems/koko-eating-bananas/description/">875. Koko Eating Bananas</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.

Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer k such that she can eat all the bananas within h hours.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  piles = [3,6,7,11], h = 8
<strong>Output:</strong> 4
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>

Constraints:
<pre>
1 <= piles.length <= 104
piles.length <= h <= 109
1 <= piles[i] <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
class Solution {
public:
    int bananahour(vector<int>& p, int beh) //beh=banana eat per hour
    {
        long th=0;   //total time taken by him
        for(int i=0;i<p.size();i++)
        { 
             th+=ceil((double)p[i]/beh);
        }
        return th;
    }
   
    int minEatingSpeed(vector<int>& p, int h) {
       
        int M=INT_MIN;
        for(int i=0;i<p.size();i++)
        {
             M=max(M,p[i]);
        }
          if(p.size()==h) return M; //max banana eated
        
        int s=1;
        int e=M;
        int ans=0;
        while(s<e)
        {
            int z=(s+e)/2;
           int mid=bananahour(p,z) ;
             //cout<<z<<"| ";
             if(mid<=h)  e=z;
            else s=z+1; 
        }
        return e;
    }
};
 </pre>

