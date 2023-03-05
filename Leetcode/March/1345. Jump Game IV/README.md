
<h2><a href="https://leetcode.com/problems/jump-game-iv/description/">1345. Jump Game IV</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an array of integers arr, you are initially positioned at the first index of the array.

In one step you can jump from index i to index:

i + 1 where: i + 1 < arr.length.
i - 1 where: i - 1 >= 0.
j where: arr[i] == arr[j] and i != j.
Return the minimum number of steps to reach the last index of the array.

Notice that you can not jump outside of the array at any time.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   arr = [100,-23,-23,404,100,23,23,23,3,404]
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: You need three jumps from index 0 --> 4 --> 3 --> 9. Note that index 9 is the last index of the array.
  </pre>
 

Constraints:
<pre>
1 <= arr.length <= 5 * 104
-108 <= arr[i] <= 108
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int minJumps(vector<int>& arr) {
        int n = arr.size();
        unordered_map<int,vector<int>> mp; // unique elements to their indices
        for(int i=0;i<n;i++)
            mp[arr[i]].push_back(i);
        queue<pair<int,int>> q; // {element,jumps}
        vector<bool> vis(n);
        vis[0] = true;
        q.push({0,0});
        int ans;
        while(!q.empty()){
            int v = q.front().first,jumps = q.front().second;
            q.pop();
            if(v==n-1){
                ans = jumps;
                break;
            }
            if(v+1<n and !vis[v+1]){
                vis[v+1] = true;
                q.push({v+1,jumps+1});
            }
            if(v-1>=0 and !vis[v-1]){
                vis[v-1] = true;
                q.push({v-1,jumps+1});
            }
            if(!mp.count(arr[v]))
                continue;
            for(auto& j:mp[arr[v]]){
                if(!vis[j]){
                    vis[j] = true;
                    q.push({j,jumps+1});
                }
            }
            mp.erase(arr[v]);
        }
        return ans;
    }
};
 </pre>

