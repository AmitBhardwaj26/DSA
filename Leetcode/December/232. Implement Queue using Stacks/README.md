
<h2><a href="https://leetcode.com/problems/implement-queue-using-stacks/description/">232. Implement Queue using Stacks</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push, peek, pop, and empty).

Implement the MyQueue class:

void push(int x) Pushes element x to the back of the queue.
int pop() Removes the element from the front of the queue and returns it.
int peek() Returns the element at the front of the queue.
boolean empty() Returns true if the queue is empty, false otherwise.
 Notes:

You must use only standard operations of a stack, which means only push to top, peek/pop from top, size, and is empty operations are valid.
Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input: ["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
<strong>Output:</strong> [null, null, null, 1, 1, false]
</pre>
<pre>
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false
  </pre>
  


Constraints:
<pre>
1 <= x <= 9
At most 100 calls will be made to push, pop, peek, and empty.
All the calls to pop and peek are valid.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
          public:
              vector<int> sumEvenAfterQueries(vector<int>& nums, vector<vector<int>>& q) {
                  int ans=0;
                  for(int i=0;i<nums.size();i++)
                  {
                      if(nums[i]%2==0) ans+=nums[i];
                  }
                  vector<int> v;
                  for(int i=0;i<q.size();i++)
                  {
                      int val=q[i][0],ind=q[i][1];
                      if(nums[ind]%2==0) ans-=nums[ind];
                      nums[ind]+=val;
                      if(nums[ind]%2==0) ans+=nums[ind];
                      v.push_back(ans);
                  }
                  return v;
              }
          };
          
 </pre>

