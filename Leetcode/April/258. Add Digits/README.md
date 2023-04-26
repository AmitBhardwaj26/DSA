
<h2><a href="https://leetcode.com/problems/add-digits/description/">258. Add Digits</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an integer array nums and an array queries where queries[i] = [vali, indexi].

For each query i, first, apply nums[indexi] = nums[indexi] + vali, then print the sum of the even values of nums.

Return an integer array answer where answer[i] is the answer to the ith query.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   num = 38
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: The process is
38 --> 3 + 8 --> 11
11 --> 1 + 1 --> 2 
Since 2 has only one digit, return it.
  </pre>
  


Constraints:
<pre>
0 <= num <= 231 - 1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int addDigits(int num) {
       return num==0?0:( num%9==0?9:num%9);
    }
};
 </pre>

