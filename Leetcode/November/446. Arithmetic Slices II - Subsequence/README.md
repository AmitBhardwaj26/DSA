
<h2><a href="https://leetcode.com/problems/arithmetic-slices-ii-subsequence/">446. Arithmetic Slices II - Subsequence</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
Given an integer array nums, return the number of all the arithmetic subsequences of nums.

A sequence of numbers is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

For example, [1, 3, 5, 7, 9], [7, 7, 7, 7], and [3, -1, -5, -9] are arithmetic sequences.
For example, [1, 1, 2, 5, 7] is not an arithmetic sequence.
A subsequence of an array is a sequence that can be formed by removing some elements (possibly none) of the array.

For example, [2,5,10] is a subsequence of [1,2,1,2,4,1,5,10].
The test cases are generated so that the answer fits in 32-bit integer.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  nums = [2,4,6,8,10]
<strong>Output:</strong> 7
</pre>
<pre>
All arithmetic subsequence slices are:
[2,4,6]
[4,6,8]
[6,8,10]
[2,4,6,8]
[4,6,8,10]
[2,4,6,8,10]
[2,6,10]
  </pre>
  


Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         // use unordered map , to calculate the dirrence add the past map value to put into answer as [1-> 2] next if same difference come then [1->2->3] then add old map value.
class Solution {
public:
    int numberOfArithmeticSlices(vector<int>& nums) {
        int n=nums.size();
        vector<long long> v(n,0);
        for(int i=0;i<n;i++)
        {
            v[i]=nums[i]+1e10;
        }
        vector<unordered_map<long long,int>> m(n+1);
        int ans=0;
        for(int i=0;i<n;i++)
        {
            for(int j=i-1;j>=0;j--)
            {
               long long x=v[i]-v[j];
               ans+=m[j][x];
               m[i][x]+=m[j][x]+1;
            }
        }
       return ans;       
    }
};
          
 </pre>

