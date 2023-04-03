
<h2><a href="https://leetcode.com/problems/boats-to-save-people/">881. Boats to Save People</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array people where people[i] is the weight of the ith person, and an infinite number of boats where each boat can carry a maximum weight of limit. Each boat carries at most two people at the same time, provided the sum of the weight of those people is at most limit.

Return the minimum number of boats to carry every given person.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  people = [1,2], limit = 3
<strong>Output:</strong> 1
</pre>
<pre>
Explanation: 1 boat (1, 2)
  </pre>
  

Constraints:
<pre>
1 <= people.length <= 5 * 104
1 <= people[i] <= limit <= 3 * 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int numRescueBoats(vector<int>& p, int l) {
        sort(p.begin(),p.end());
        int i=0,j=p.size()-1;
        int ans=0;
        while(i<=j)
        {
            if((p[i]+p[j])<=l)
            {
                ans++; i++;j--;
            }
            else { ans++; j--; }
        }
        return ans;
    }
};
 </pre>

