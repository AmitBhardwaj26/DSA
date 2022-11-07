
<h2><a href="https://leetcode.com/problems/maximum-69-number/description/">1323. Maximum 69 Number</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
You are given a positive integer num consisting only of digits 6 and 9.

Return the maximum number you can get by changing at most one digit (6 becomes 9, and 9 becomes 6).

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   num = 9669
<strong>Output:</strong> 9969
</pre>
<pre>
Changing the first digit results in 6669.
Changing the second digit results in 9969.
Changing the third digit results in 9699.
Changing the fourth digit results in 9666.
The maximum number is 9969.
  </pre>
  
Example 2:

Input: num = 9996
Output: 9999
Explanation: Changing the last digit 6 to 9 results in the maximum number.

Constraints:
<pre>
1 <= num <= 104
num consists of only 6 and 9 digits.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int maximum69Number (int num) {
        vector<int> a;
        while(num)
        {
            a.push_back(num%10);
            num/=10;
        }
        int ans=0,check=1;
        for(int i=a.size()-1;i>=0;i--)
        {
            if(a[i]==9 || check==0)
           ans=ans*10+a[i];  
            else {
                ans=ans*10+9;
                check=0;
            }
        }
        return ans;
    }
};
          
 </pre>

