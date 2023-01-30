
<h2><a href="https://leetcode.com/problems/n-th-tribonacci-number/description/">1137. N-th Tribonacci Number</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
The Tribonacci sequence Tn is defined as follows: 

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given n, return the value of Tn.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    n = 4
<strong>Output:</strong>  4
</pre>
<pre>
Explanation: T_3 = 0 + 1 + 1 = 2
T_4 = 1 + 1 + 2 = 4
  </pre>
  

Constraints:
<pre>
0 <= n <= 37
The answer is guaranteed to fit within a 32-bit integer, ie. answer <= 2^31 - 1.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
      int dp[39]={0};
     
    int tribonacci(int n) {
       
        if(n==0) return 0;
        if(n==2||n==1) return 1;
        if(dp[n]!=0) return dp[n];
        return dp[n]=tribonacci(n-1)+tribonacci(n-2)+tribonacci(n-3) ;
    }
};4
          
 </pre>

