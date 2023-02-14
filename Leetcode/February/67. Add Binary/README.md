
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">67. Add Binary</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
 Given two binary strings a and b, return their sum as a binary string.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  a = "11", b = "1"
<strong>Output:</strong>  "100"
</pre>


Constraints:
<pre>
1 <= a.length, b.length <= 104
a and b consist only of '0' or '1' characters.
Each string does not contain leading zeros except for the zero itself.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
 class Solution {
  public:
     string addBinary(string a, string b) {
         int i=a.size()-1,j=b.size()-1;
         string ans=""; int carry=0;
         while(i>=0 && j>=0)
         {
             int x=a[i]-'0'; int y=b[j]-'0';
             if((x+y+carry)==3 ) {ans+='1'; carry=1;}
             else if((x+y+carry)==2) { ans+='0'; carry=1;}
             else if((x+y+carry)==1) { ans+='1'; carry=0;}
             else { ans+='0'; carry=0;}
             i--;j--;
         }
         while(i>=0)
         {
             int x=a[i]-'0';
              if((x+carry)==2) { ans+='0'; carry=1;}
             else if((x+carry)==1) { ans+='1'; carry=0;}
             else { ans+='0'; carry=0;}
             i--;
         }
         while(j>=0)
         {
             int y=b[j]-'0';
              if((y+carry)==2) { ans+='0'; carry=1;}
             else if((y+carry)==1) { ans+='1'; carry=0;}
             else { ans+='0'; carry=0;}
             j--;
         }
         if(carry==1) ans+='1';
          reverse(ans.begin(),ans.end());
         return ans;
    }
};
          
 </pre>

