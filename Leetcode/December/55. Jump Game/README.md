
<h2><a href="https://leetcode.com/problems/jump-game/description/">55. Jump Game</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   nums = [2,3,1,1,4]
<strong>Output:</strong> true
</pre>
<pre>
Jump 1 step from index 0 to 1, then 3 steps to the last index.
  </pre>

 

Constraints:
<pre>
1 <= nums.length <= 104
0 <= nums[i] <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
       /*
1,2 short ans easy 
find the location of visited note that can be reached from any point if any point we move and we cannot reached then return false
3= dp approch best parent problem ans
*/

class Solution {
public:
    bool canJump(vector<int>& nums) {
     
        int vis=0;
        for(int i=0;i<nums.size();i++)
        {
            if(vis<i) return false;
            vis=max(vis,nums[i]+i);
        }
        return true;
    }
};


// approch 2

// class Solution {
// public:
//     bool canJump(vector<int>& s) {
       
//         int store = 0;
//         bool check = true;
//         for(int i=s.size()-2; i>=0 ; i--){
//            store++;
//             if(s[i]>=store){
//                 store = 0;
//             }
//         }
//         if(store>0){
//             return false;
//         }
//         else return true;
//     }
// };




// class Solution {
// public:
//     int dp[10005];
//     bool solve(vector<int>& nums,  int m)
//     {
//         if(m>=nums.size()-1) return true;
//         //if(m==nums.size()-1) return true;
       
//         if(dp[m]!=-1) return dp[m];
        
//         for(int i=1;i<=nums[m];i++)
//         {
//             if(m+i<nums.size()  && solve(nums,m+i))
//              return dp[m]=true;
//         }
//         return dp[m]=false;
//     }
    
//     bool canJump(vector<int>& nums) {
//       memset(dp,-1,sizeof(dp));
        
//         return solve(nums,0);
        
//     }
// };
          
 </pre>

