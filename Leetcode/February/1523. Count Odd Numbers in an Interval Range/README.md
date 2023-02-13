
<h2><a href="https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/">1523. Count Odd Numbers in an Interval Range</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given two non-negative integers low and high. Return the count of odd numbers between low and high (inclusive).
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> low = 3, high = 7
<strong>Output:</strong> 3
</pre>
<pre>
 Explanation: The odd numbers between 3 and 7 are [3,5,7].
  </pre>


Constraints:
<pre>
0 <= low <= high <= 10^9
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int countOdds(int low, int high) {
        return (low%2!=0 || high%2!=0)? (high-low)/2+1: (high-low)/2;
    }
};
          
 </pre>

