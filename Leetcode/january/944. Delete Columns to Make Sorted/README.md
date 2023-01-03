
<h2><a href="https://leetcode.com/problems/delete-columns-to-make-sorted/description/">944. Delete Columns to Make Sorted</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array of n strings strs, all of the same length.

The strings can be arranged such that there is one on each line, making a grid. For example, strs = ["abc", "bce", "cae"] can be arranged as:

abc
bce
cae
You want to delete the columns that are not sorted lexicographically. In the above example (0-indexed), columns 0 ('a', 'b', 'c') and 2 ('c', 'e', 'e') are sorted while column 1 ('b', 'c', 'a') is not, so you would delete column 1.

Return the number of columns that you will delete.


</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  strs = ["cba","daf","ghi"]
<strong>Output:</strong> 1
</pre>
<pre>
The grid looks as follows:
  cba
  daf
  ghi
Columns 0 and 2 are sorted, but column 1 is not, so you only need to delete 1 column.
  </pre>
 

Constraints:
<pre>
n == strs.length
1 <= n <= 100
1 <= strs[i].length <= 1000
strs[i] consists of lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          class Solution {
              public:
                  int minDeletionSize(vector<string>& str) {
                    int ans=0;
                    for(int i=0;i<str[0].size();i++)  
                    {
                      bool check=1;
                      for(int j=1;j<str.size();j++)
                      {
                          if(str[j][i]<str[j-1][i])
                          {
                              check=0; break;
                          }
                      }
                      if(check==0) ans++;
                    }
                    return ans;
                  }
              };
          
 </pre>

