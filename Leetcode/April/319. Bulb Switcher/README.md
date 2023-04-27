
<h2><a href="https://leetcode.com/problems/bulb-switcher/description/">319. Bulb Switcher</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are n bulbs that are initially off. You first turn on all the bulbs, then you turn off every second bulb.

On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the ith round, you toggle every i bulb. For the nth round, you only toggle the last bulb.

Return the number of bulbs that are on after n rounds.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  n = 0
<strong>Output:</strong> 0
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>


Constraints:
<pre>
0 <= n <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int bulbSwitch(int n) {
       return sqrt(n);
    }
};
 </pre>

