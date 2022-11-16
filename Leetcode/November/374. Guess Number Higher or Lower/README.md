
<h2><a href="https://leetcode.com/problems/guess-number-higher-or-lower/description/">374. Guess Number Higher or Lower</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
We are playing the Guess Game. The game is as follows:

I pick a number from 1 to n. You have to guess which number I picked.

Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess.

You call a pre-defined API int guess(int num), which returns three possible results:

-1: Your guess is higher than the number I picked (i.e. num > pick).
1: Your guess is lower than the number I picked (i.e. num < pick).
0: your guess is equal to the number I picked (i.e. num == pick).
Return the number that I picked.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    n = 10, pick = 6
<strong>Output:</strong> 6
</pre>

Example 2:

Input: n = 1, pick = 1
Output: 1
 

Constraints:
<pre>
1 <= n <= 231 - 1
1 <= pick <= n
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
          public:
              int guessNumber(int n) {
                 long long i=0,j=n,mid=(i+j)/2;
                  while(i<=j)
                  {
                       mid=(i+j)/2;
                      if(guess(mid)==0) return mid;
                      else if(guess(mid)==1) i=mid+1;
                      else j=mid-1;
                  }
                  return mid;
              }
          };
          
 </pre>

