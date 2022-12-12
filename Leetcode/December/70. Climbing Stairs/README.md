
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n = 2
<strong>Output:</strong> 2
</pre>
<pre>
There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
  </pre>
  
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
 

Constraints:
<pre>
1 <= n <= 45
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int climbStairs(int n) {
       long a[50]={0};
        a[0]=0;a[1]=1;
        for(int i=2;i<=n+2;i++) 
            a[i]=a[i-1]+a[i-2];
        return a[n+1];
    }
};
          
 </pre>

