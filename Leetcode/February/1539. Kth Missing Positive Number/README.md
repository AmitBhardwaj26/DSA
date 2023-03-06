
<h2><a href="https://leetcode.com/problems/kth-missing-positive-number/description/">1539. Kth Missing Positive Number</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given an array arr of positive integers sorted in a strictly increasing order, and an integer k.

Return the kth positive integer that is missing from this array.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  arr = [2,3,4,7,11], k = 5
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation:  The missing positive integers are [1,5,6,8,9,10,12,13,...]. The 5th missing positive integer is 9.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= arr.length <= 1000
1 <= arr[i] <= 1000
1 <= k <= 1000
arr[i] < arr[j] for 1 <= i < j <= arr.length
 
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    int findKthPositive(vector<int>& arr, int k) {
     int i=0,j=arr.size()-1;
        while(i<=j)
        {
            int mid=i+(j-i)/2;
            if(arr[mid]-mid-1>=k)  j=mid-1;
            else i=mid+1;
        }
        if(j>=0) return arr[j]-(arr[j]-j-1-k);
        else return k;
    }
};
 </pre>

