
<h2><a href="https://leetcode.com/problems/minimize-deviation-in-array/description/">1675. Minimize Deviation in Array</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an array nums of n positive integers.

You can perform two types of operations on any element of the array any number of times:

If the element is even, divide it by 2.
For example, if the array is [1,2,3,4], then you can do this operation on the last element, and the array will be [1,2,3,2].
If the element is odd, multiply it by 2.
For example, if the array is [1,2,3,4], then you can do this operation on the first element, and the array will be [2,2,3,4].
The deviation of the array is the maximum difference between any two elements in the array.

Return the minimum deviation the array can have after performing some number of operations.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    nums = [1,2,3,4]
<strong>Output:</strong>  1
</pre>
<pre>
Explanation: You can transform the array to [1,2,3,2], then to [2,2,3,2], then the deviation will be 3 - 2 = 1.
  </pre>
  


Constraints:
<pre>
n == nums.length
2 <= n <= 5 * 104
1 <= nums[i] <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
    
//     class Solution {
// public:
//     int minimumDeviation(vector<int>& nums) {
//         int n = nums.size();
//         priority_queue<int> pq;
//         int minElement = INT_MAX, ans = INT_MAX;
        
//         for (auto num : nums) {
//             if (num & 1) { // if odd make it even
//                 pq.push(num * 2);
//                 minElement = min(minElement, num * 2);
//             } else {
//                 pq.push(num);
//                 minElement = min(minElement, num);
//             }
            
//         }
        
//         while (!pq.empty()) {
//             int num = pq.top(); pq.pop();
//             ans = min(ans, num - minElement); // get the minimum deviation
//             if(num & 1) break; // if odd break
//             else pq.push(num / 2); // if even decrease it by half
//             minElement = min(minElement, num / 2); // update the minElement
//         }
//         return ans;
//     }
// };

    class Solution {
public:
    int minimumDeviation(vector<int>& nums) {
        int n = nums.size();
        priority_queue<int> pq;
        int minElement = INT_MAX, ans = INT_MAX;
        
        for (auto num : nums) {
            if (num & 1) { // if odd make it even
                pq.push(num * 2);
                minElement = min(minElement, num * 2);
            } else {
                pq.push(num);
                minElement = min(minElement, num);
            }
            
        }
        
        while (!pq.empty()) {
            int num = pq.top(); pq.pop();
            ans = min(ans, num - minElement); // get the minimum deviation
            if(num & 1) break; // if odd break
            else pq.push(num / 2); // if even decrease it by half
            minElement = min(minElement, num / 2); // update the minElement
        }
        return ans;
    }
};  
 </pre>

