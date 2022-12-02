
<h2><a href="https://leetcode.com/problems/determine-if-two-strings-are-close/">1657. Determine if Two Strings Are Close
<h3>Medium</h3>
<hr>
<div><p>
 Two strings are considered close if you can attain one from the other using the following operations:

Operation 1: Swap any two existing characters.
For example, abcde -> aecdb
Operation 2: Transform every occurrence of one existing character into another existing character, and do the same with the other character.
For example, aacabb -> bbcbaa (all a's turn into b's, and all b's turn into a's)
You can use the operations on either string as many times as necessary.

Given two strings, word1 and word2, return true if word1 and word2 are close, and false otherwise.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   word1 = "abc", word2 = "bca
<strong>Output:</strong> true
</pre>
<pre>
1 <= word1.length, word2.length <= 105
word1 and word2 contain only lowercase English letters.
  </pre>


Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 // if the count of each character of A must matches with count of any character in string B and that character of A must present in string B then return True
// else return false 
class Solution {
public:
    bool closeStrings(string w1, string w2) {
        int l1=w1.size(),l2=w2.size();
        if(l1!=l2) return 0;
        int a[26]={0},b[26]={0},c[26]={0};
        for(int i=0;i<l1;i++)  a[w1[i]-'a']++;
        for(int i=0;i<l2;i++)  b[w2[i]-'a']++;
        for(int i=0;i<26;i++)  c[i]=b[i];
        int count=0;
        for(int i=0;i<26;i++)
        {
            bool check=0;
            for(int j=0;j<26;j++)
            {
                if(a[i]==b[j] && c[i]!=0) 
                { 
                    //if(i!=j) count++; 
                    cout<<i<<" "<<j<<endl;
                    b[j]=-1; break;
                }
            }
        }
        for(int i=0;i<26;i++) if(b[i]>0) return 0;
         return 1;
        //else return 0;
    }
};
          
 </pre>

