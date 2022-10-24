
<h2><a href="https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/description/">1239. Maximum Length of a Concatenated String with Unique Characters</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array of strings arr. A string s is formed by the concatenation of a subsequence of arr that has unique characters.

Return the maximum possible length of s.

A subsequence is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.

 
</p>


 Input: arr = ["un","iq","ue"]
Output: 4
Explanation: All the valid concatenations are:
- ""
- "un"
- "iq"
- "ue"
- "uniq" ("un" + "iq")
- "ique" ("iq" + "ue")
Maximum length is 4.
Example 2:

Input: arr = ["cha","r","act","ers"]
Output: 6
Explanation: Possible longest valid concatenations are "chaers" ("cha" + "ers") and "acters" ("act" + "ers").
Example 3:

Input: arr = ["abcdefghijklmnopqrstuvwxyz"]
Output: 26
Explanation: The only string in arr has all 26 characters.
 

Constraints:

1 <= arr.length <= 16
1 <= arr[i].length <= 26
arr[i] contains only lowercase English letters.
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int maxLength(vector<string>& arr) {
        int maxlength=0;
        int n=arr.size();
        int nos=pow(2,n)-1;
        for(int num=0;num<=nos;num++)
        {
            vector<string> temp;
            for(int i=0;i<n;i++)
            {
                int bit=(num&(1<<i));
                if(bit) temp.push_back(arr[i]);
            }
            string s1="";
            for(int i=0;i<temp.size();i++)
            {
                s1+=temp[i];
            }
            int freq[26]={0};
            for(int i=0;i<s1.size();i++)
            {
                freq[s1[i]-'a']++;
            }
            int cnt=0;
            for(int i=0;i<26;i++)
            {
                if(freq[i]==1)
                {
                    cnt++;
                }
                else if(freq[i]>1)
                {
                    cnt=0;
                    break;
                }
            }
            maxlength=max(maxlength,cnt);            
        }
        return maxlength;
    }
};
          
 </pre>

