
<h2><a href="https://leetcode.com/problems/concatenation-of-consecutive-binary-numbers/">1680. Concatenation of Consecutive Binary Numbers</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
  Given an integer n, return the decimal value of the binary string formed by concatenating the binary representations of 1 to n in order, modulo 109 + 7.
 

Constraints:

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n=12
<strong>Output:</strong> 505379714 1
</pre>
<pre>
The concatenation results in "1101110010111011110001001101010111100".
The decimal value of that is 118505380540.
After modulo 109 + 7, the result is 505379714.
</pre>

Constraints:
1 <= n <= 105

</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
          public:

              int concatenatedBinary(int n) {
                  int M=1e9+7;
                  long ans=0;
                  for(int i=1;i<=n;i++)
                  {
                      int x=floor(log2(i))+1;
                      long long y=pow((long long)2,x);
                      y%=M;
                      ans=(ans*y)+i; ans%=M;
                  }
                  return ans;
              }
          };
          
 </pre>

