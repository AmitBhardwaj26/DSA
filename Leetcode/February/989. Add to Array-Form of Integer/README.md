
<h2><a href="https://leetcode.com/problems/add-to-array-form-of-integer/description/">989. Add to Array-Form of Integer </a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 You are given an integer array nums and an array queries where queries[i] = [vali, indexi].

For each query i, first, apply nums[indexi] = nums[indexi] + vali, then print the sum of the even values of nums.

Return an integer array answer where answer[i] is the answer to the ith query.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  num = [1,2,0,0], k = 34
<strong>Output:</strong>  [1,2,3,4]
</pre>
<pre>
Explanation: 1200 + 34 = 1234
  </pre>
  


Constraints:
<pre>
1 <= num.length <= 104
0 <= num[i] <= 9
num does not contain any leading zeros except for the zero itself.
1 <= k <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    vector<int> addToArrayForm(vector<int>& num, int k) {
        
        vector<int> num2;
        while(k)
        {
            num2.push_back(k%10); k/=10;
        }
       int i=0,j=num.size()-1;
       int c=0,sum=0;
       vector<int> ans;
       while(i<num2.size() && j>=0)
       {
           sum=num2[i++] + num[j--] +c;
           c=sum/10;
           ans.push_back(sum%10);
       }
       while(i<num2.size())
       {
           sum=num2[i++] +c;
           c=sum/10;
           ans.push_back(sum%10);
       }
        while( j>=0 )
       {
           sum= num[j--] + c;
           c=sum/10;
           ans.push_back(sum%10);
       }
       if(c) ans.push_back(c);
       reverse(ans.begin(),ans.end());
       return ans;
    }
};
          
 </pre>

