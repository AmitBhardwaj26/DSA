
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
 /*
push take order(1) time
take two stack s1,s2;
while taking the top or while poping check in satck 2;
if empty take O(n) time 
whole take O(1) amortised  time complexity
*/

class MyQueue {
public:
    stack<int> s1,s2;
    MyQueue() {
        
    }
    
    void push(int x) {
        s1.push(x);
    }
    
    int pop() {
        if(s1.empty()&& s2.empty()) return -1;
        if(s2.empty()) 
        {
          while(!s1.empty())
          { s2.push(s1.top()); s1.pop();}
        }
         
        int t= s2.top(); s2.pop(); 
        return t;
    }
    
    int peek() {
        if(s2.empty()&& s1.empty()) return -1;
        if(s2.empty())
        {
           while(!s1.empty())
           { s2.push(s1.top()); s1.pop();}        
        }
        return s2.top();
    }
    
    bool empty() {
        if(s2.empty()&& s1.empty()) return true;
         return false;
    }
};

          
 </pre>

