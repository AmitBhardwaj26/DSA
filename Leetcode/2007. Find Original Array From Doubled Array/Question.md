
<h2><a href="https://leetcode.com/problems/find-original-array-from-doubled-array/">2007. Find Original Array From Doubled Array</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
An integer array original is transformed into a doubled array changed by appending twice the value of every element in original, and then randomly shuffling the resulting array.
Given an array changed, return original if changed is a doubled array. If changed is not a doubled array, return an empty array. The elements in original may be returned in any order.

</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> changed = [1,3,4,2,6,8]
<strong>Output:</strong> [1,3,4]
</pre>


Example 2:

Input: changed = [6,3,0,1]
Output: []
Explanation: changed is not a doubled array.
Example 3:

Input: changed = [1]
Output: []
Explanation: changed is not a doubled array.
 

Constraints:

1 <= changed.length <= 105
0 <= changed[i] <= 105
 
