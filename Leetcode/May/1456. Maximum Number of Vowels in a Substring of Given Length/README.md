
<h2><a href="https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/description/">1456. Maximum Number of Vowels in a Substring of Given Length</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string s and an integer k, return the maximum number of vowel letters in any substring of s with length k.

Vowel letters in English are 'a', 'e', 'i', 'o', and 'u'.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    s = "abciiidef", k = 3
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: The substring "iii" contains 3 vowel letters.
  </pre>
  

Constraints:
<pre>
1 <= s.length <= 105
s consists of lowercase English letters.
1 <= k <= s.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
   static boolean isVowel(char c)
   {
       String s="aeiou";
       for(int i=0;i<5;i++) if(s.charAt(i)==c) return true;
       return false;
   }

    public int maxVowels(String s, int k) {
        int count=0,i=0,j=0,ans=0,n=s.length();

        for(i=0;i<k;i++)
        {
            if(isVowel(s.charAt(i))) count++;
        }
        ans=Math.max(ans,count);
        while(i<n)
        {
            if(isVowel(s.charAt(j))) count--;
            if(isVowel(s.charAt(i))) count++;
            ans=Math.max(ans,count);
            i++;j++;
        }
        return ans;
    }
}
 </pre>

