
<h2><a href="https://leetcode.com/problems/ugly-number/description/">263. Ugly Number</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5.

Given an integer n, return true if n is an ugly number.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    n = 6
<strong>Output:</strong> true
</pre>

  
Example 2:

Input: n = 1
Output: true
Explanation: 1 has no prime factors, therefore all of its prime factors are limited to 2, 3, and 5.
 

Constraints:
<pre>
-231 <= n <= 231 - 1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    bool isUgly(int n) {
        if(n<=0) return 0;
        
        while(n%2==0) n=n/2;
         while(n%3==0) n=n/3;
         while(n%5==0) n=n/5;
         
            if( n==1) return 1;
        return 0;
        
    }
};
          
 </pre>

