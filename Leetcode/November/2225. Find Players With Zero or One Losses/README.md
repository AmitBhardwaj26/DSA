
<h2><a href="https://leetcode.com/problems/find-players-with-zero-or-one-losses/description/">2225. Find Players With Zero or One Losses</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an integer array matches where matches[i] = [winneri, loseri] indicates that the player winneri defeated player loseri in a match.

Return a list answer of size 2 where:

answer[0] is a list of all players that have not lost any matches.
answer[1] is a list of all players that have lost exactly one match.
The values in the two lists should be returned in increasing order.

Note:

You should only consider the players that have played at least one match.
The testcases will be generated such that no two matches will have the same outcome.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   matches = [[1,3],[2,3],[3,6],[5,6],[5,7],[4,5],[4,8],[4,9],[10,4],[10,9]]
<strong>Output:</strong> [[1,2,10],[4,5,7,8]]
</pre>
<pre>
Players 1, 2, and 10 have not lost any matches.
Players 4, 5, 7, and 8 each have lost one match.
Players 3, 6, and 9 each have lost two matches.
Thus, answer[0] = [1,2,10] and answer[1] = [4,5,7,8].
  </pre>
  


Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    vector<vector<int>> findWinners(vector<vector<int>>& mat) {
     map<int,int> m1,m2;
        for(int i=0;i<mat.size();i++)
        {
            m1[mat[i][0]]++;
            m2[mat[i][1]]++;
        }
        vector<vector<int>> ans;
        vector<int> v;
        for(auto it:m1)
        {
            if(m2.find(it.first)==m2.end() ) v.push_back(it.first);
        }
        ans.push_back(v);
        v.clear();
        for(auto it:m2)
        {
            if(it.second ==1) v.push_back(it.first);
        }
        ans.push_back(v);
        return ans;
        
    }
};
 </pre>

