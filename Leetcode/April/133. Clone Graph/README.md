
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a reference of a node in a connected undirected graph.

Return a deep copy (clone) of the graph.

Each node in the graph contains a value (int) and a list (List[Node]) of its neighbors.

class Node {
    public int val;
    public List<Node> neighbors;
}
 

Test case format:

For simplicity, each node's value is the same as the node's index (1-indexed). For example, the first node with val == 1, the second node with val == 2, and so on. The graph is represented in the test case using an adjacency list.

An adjacency list is a collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a node in the graph.

The given node will always be the first node with val = 1. You must return the copy of the given node as a reference to the cloned graph.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> adjList = [[2,4],[1,3],[2,4],[1,3]]
<strong>Output:</strong>  [[2,4],[1,3],[2,4],[1,3]]
</pre>
<pre>
Explanation:  There are 4 nodes in the graph.
1st node (val = 1)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
2nd node (val = 2)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).
3rd node (val = 3)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
4th node (val = 4)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).
  </pre>

 

Constraints:
<pre>
The number of nodes in the graph is in the range [0, 100].
1 <= Node.val <= 100
Node.val is unique for each node.
There are no repeated edges and no self-loops in the graph.
The Graph is connected and all nodes can be visited starting from the given node.
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

