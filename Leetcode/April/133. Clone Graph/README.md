
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a reference of a node in a connected undirected graph.

Return a deep copy (clone) of the graph.

Each node in the graph contains a value (int) and a list (List[Node]) of its neighbors.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,2,3,4], queries = [[1,0],[-3,1],[-4,0],[2,3]]
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

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
 /*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> neighbors;
    Node() {
        val = 0;
        neighbors = vector<Node*>();
    }
    Node(int _val) {
        val = _val;
        neighbors = vector<Node*>();
    }
    Node(int _val, vector<Node*> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/

class Solution {
public:
    void dfs(Node *node,Node *Real,vector<Node*> &visited)
    {
      //  if(node==NULL) return ;
        visited[Real->val]=Real;
        for(auto it:node->neighbors)
        {
            if(visited[it->val]==NULL)
            {
                
              Node *t=new Node(it->val);
              // visited[it->val]=t;
                Real->neighbors.push_back(t);
              dfs(it,t,visited);
                
            } 
            else Real->neighbors.push_back(visited[it->val]);
        }
    }
    
    Node* cloneGraph(Node* node) {
        if(node==NULL) return NULL;
        Node *Copy=new Node();
        Copy->val=node->val;
        vector<Node *> visited(105,NULL);
        visited[Copy->val] = Copy;
        for(auto it:node->neighbors)
        {
            if(visited[it->val]==NULL)
            {
                
              Node *t=new Node(it->val);
               Copy->neighbors.push_back(t);
              
              dfs(it,t,visited);
                
            } 
            else Copy->neighbors.push_back(visited[it->val]);
        }
        
        return Copy;
    }
};
 </pre>

