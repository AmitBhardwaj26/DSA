
<h2><a href="https://leetcode.com/problems/validate-stack-sequences/description/">946. Validate Stack Sequences</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given two integer arrays pushed and popped each with distinct values, return true if this could have been the result of a sequence of push and pop operations on an initially empty stack, or false otherwise.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
<strong>Output:</strong>  true
</pre>
<pre>
Explanation: We might do the following sequence:
push(1), push(2), push(3), push(4),
pop() -> 4,
push(5),
pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1
  </pre>
  

Constraints:
<pre>
1 <= pushed.length <= 1000
0 <= pushed[i] <= 1000
All the elements of pushed are unique.
popped.length == pushed.length
popped is a permutation of pushed.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    bool validateStackSequences(vector<int>& pushed, vector<int>& popped) {
        int i=0,j=0,n=popped.size();
        stack<int> st;
        for(auto it: pushed)
        {
            st.push(it);
            while(j<n && !st.empty() && popped[j]==st.top())
                {st.pop(); j++;}
              
        }
        return n==j;
    }
};
 </pre>

