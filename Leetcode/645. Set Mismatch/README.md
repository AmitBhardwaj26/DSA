
<h2><a href="https://leetcode.com/problems/set-mismatch/description/">645. Set Mismatch</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.

You are given an integer array nums representing the data status of this set after the error.

Find the number that occurs twice and the number that is missing and return them in the form of an array.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    nums = [1,2,2,4]
<strong>Output:</strong>[2,3]
</pre>

  
Example 2:

Input: nums = [1,1]
Output: [1,2]
 

Constraints:
<pre>
2 <= nums.length <= 104
1 <= nums[i] <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
       class Solution {
public:
    vector<int> findErrorNums(vector<int>& nums) {
        int n=nums.size(), m[10001]={0};
        vector<int> ans;
        for(int i=0;i<n;i++)
            m[nums[i]]+=1;
            int x,y; 
        for(int i=1;i<=n;i++)
        {
            if(m[i]==0) x=i;
            else if(m[i]==2) y=i; 
        }
        ans.push_back(y); ans.push_back(x);
        return ans;
    }
};
          
 </pre>

