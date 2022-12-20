
<h2><a href="https://leetcode.com/problems/keys-and-rooms/">841. Keys and Rooms</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are n rooms labeled from 0 to n - 1 and all the rooms are locked except for room 0. Your goal is to visit all the rooms. However, you cannot enter a locked room without having its key.

When you visit a room, you may find a set of distinct keys in it. Each key has a number on it, denoting which room it unlocks, and you can take all of them with you to unlock the other rooms.

Given an array rooms where rooms[i] is the set of keys that you can obtain if you visited room i, return true if you can visit all the rooms, or false otherwise.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   rooms = [[1],[2],[3],[]]
<strong>Output:</strong> true
</pre>
<pre>
We visit room 0 and pick up key 1.
We then visit room 1 and pick up key 2.
We then visit room 2 and pick up key 3.
We then visit room 3.
Since we were able to visit every room, we return true.
  </pre>
  
Input: rooms = [[1,3],[3,0,1],[2],[0]]
Output: false
Explanation: We can not enter room number 2 since the only key that unlocks it is in that room.
 

Constraints:
<pre>
n == rooms.length
2 <= n <= 1000
0 <= rooms[i].length <= 1000
1 <= sum(rooms[i].length) <= 3000
0 <= rooms[i][j] < n
All the values of rooms[i] are unique.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         //basic BFS
class Solution {
public:
    int vis[1001]={0};
    bool canVisitAllRooms(vector<vector<int>>& r) {
        int n=r.size();
        queue<int> q;
        q.push(0);
        vis[0]=1;
        while(!q.empty())
        {
            int x=q.front(); q.pop();
            vis[x]=1;
            for(int it:r[x])
            {
                if(vis[it]==0)
                    q.push(it);
            }
        }
        for(int i=0;i<r.size();i++)
        {
            if(vis[i]==0) return 0;
        }
        return 1;
    }
};
 </pre>

