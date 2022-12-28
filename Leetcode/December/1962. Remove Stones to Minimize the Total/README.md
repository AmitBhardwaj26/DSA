
<h2><a href="https://leetcode.com/problems/remove-stones-to-minimize-the-total/">1962. Remove Stones to Minimize the Total</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given a 0-indexed integer array piles, where piles[i] represents the number of stones in the ith pile, and an integer k. You should apply the following operation exactly k times:

Choose any piles[i] and remove floor(piles[i] / 2) stones from it.
Notice that you can apply the operation on the same pile more than once.

Return the minimum possible total number of stones remaining after applying the k operations.

floor(x) is the greatest integer that is smaller than or equal to x (i.e., rounds x down).
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  piles = [5,4,9], k = 2
<strong>Output:</strong> 12
</pre>
<pre>
Steps of a possible scenario are:
- Apply the operation on pile 2. The resulting piles are [5,4,5].
- Apply the operation on pile 0. The resulting piles are [3,4,5].
The total number of stones in [3,4,5] is 12.
  </pre>
  

 

Constraints:
<pre>
1 <= piles.length <= 105
1 <= piles[i] <= 104
1 <= k <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
       class Solution {
public:
    int minStoneSum(vector<int>& piles, int k) {
        int n=piles.size();
        priority_queue<int> pq;
        for(int i=0;i<n;i++)
        {
            pq.push(piles[i]);
        }
        while(k--)
        {
            int x=pq.top(); pq.pop();
            pq.push(x-x/2);
        }
        int ans=0;
        while(!pq.empty())
        {
            ans+=pq.top(); pq.pop();
        }
        return ans;
    }
};
          
 </pre>

