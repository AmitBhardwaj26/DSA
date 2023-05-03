
<h2><a href="https://leetcode.com/problems/find-the-difference-of-two-arrays/description/">2215. Find the Difference of Two Arrays</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given two 0-indexed integer arrays nums1 and nums2, return a list answer of size 2 where:

answer[0] is a list of all distinct integers in nums1 which are not present in nums2.
answer[1] is a list of all distinct integers in nums2 which are not present in nums1.
Note that the integers in the lists may be returned in any order.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [1,2,3,4], queries = [[1,0],[-3,1],[-4,0],[2,3]]
<strong>Output:</strong>  [[1,3],[4,6]]
</pre>
<pre>
Explanation: For nums1, nums1[1] = 2 is present at index 0 of nums2, whereas nums1[0] = 1 and nums1[2] = 3 are not present in nums2. Therefore, answer[0] = [1,3].
For nums2, nums2[0] = 2 is present at index 1 of nums1, whereas nums2[1] = 4 and nums2[2] = 6 are not present in nums2. Therefore, answer[1] = [4,6].
  </pre>

 

Constraints:
<pre>
1 <= nums1.length, nums2.length <= 1000
-1000 <= nums1[i], nums2[i] <= 1000
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
       class Solution {
public:
    vector<vector<int>> findDifference(vector<int>& n1, vector<int>& n2) {
        //sort(n1.begin(),n1.end());
        //sort(n2.begin(),n2.end());
        set<int> s1,s2;
        for(int i=0;i<n1.size();i++)
        {
            s1.insert(n1[i]);
        }
        for(int i=0;i<n2.size();i++)
        {
            s2.insert(n2[i]);
        }
        vector<vector<int>> ans;
        vector<int> v1,v2;
        for(auto it: s1)
        {
            if(s2.find(it)==s2.end()) v1.push_back(it);
        }
        ans.push_back(v1);
         for(auto it: s2)
        {
            if(s1.find(it)==s1.end()) v2.push_back(it);
        }
        ans.push_back(v2);
      return ans;        
        
        
    }
};
 </pre>

