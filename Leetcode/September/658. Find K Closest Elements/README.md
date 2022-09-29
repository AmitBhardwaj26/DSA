
<h2><a href="https://leetcode.com/problems/find-k-closest-elements/">658. Find K Closest Elements</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
  Given a sorted integer array arr, two integers k and x, return the k closest integers to x in the array. The result should also be sorted in ascending order.

An integer a is closer to x than an integer b if:

|a - x| < |b - x|, or
|a - x| == |b - x| and a < b
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  arr = [1,2,3,4,5], k = 4, x = 3
<strong>Output:</strong>  [1,2,3,4]
</pre>


<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong>  arr = [1,2,3,4,5], k = 4, x = -1
<strong>Output:</strong>  [1,2,3,4]
</pre>

 

Constraints:
<pre>
1 <= k <= arr.length
1 <= arr.length <= 104
arr is sorted in ascending order.
-104 <= arr[i], x <= 104
</pre>

<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        sort(arr.begin(),arr.end());
        vector<pair<int,int>> v;
        for(int i=0;i<arr.size();i++)
        {
            int y=abs(arr[i]-x);
          v.push_back({y,arr[i]});
        }
        sort(v.begin(),v.end());
        vector<int> ans;
        for(int i=0;i<k;i++)
        {
            ans.push_back(v[i].second);
        }
        sort(ans.begin(),ans.end());
        return ans;
    }
};
          
 </pre>

