
<h2><a href="https://leetcode.com/problems/number-of-ways-to-form-a-target-string-given-a-dictionary/description/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given a list of strings of the same length words and a string target.

Your task is to form target using the given words under the following rules:

target should be formed from left to right.
To form the ith character (0-indexed) of target, you can choose the kth character of the jth string in words if target[i] = words[j][k].
Once you use the kth character of the jth string of words, you can no longer use the xth character of any string in words where x <= k. In other words, all characters to the left of or at index k become unusuable for every string.
Repeat the process until you form the string target.
Notice that you can use multiple characters from the same string in words provided the conditions above are met.

Return the number of ways to form target from words. Since the answer may be too large, return it modulo 109 + 7.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  words = ["acca","bbbb","caca"], target = "aba"
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: There are 6 ways to form target.
"aba" -> index 0 ("acca"), index 1 ("bbbb"), index 3 ("caca")
"aba" -> index 0 ("acca"), index 2 ("bbbb"), index 3 ("caca")
"aba" -> index 0 ("acca"), index 1 ("bbbb"), index 3 ("acca")
"aba" -> index 0 ("acca"), index 2 ("bbbb"), index 3 ("acca")
"aba" -> index 1 ("caca"), index 2 ("bbbb"), index 3 ("acca")
"aba" -> index 1 ("caca"), index 2 ("bbbb"), index 3 ("caca")
  </pre>
 

Constraints:
<pre>
1 <= words.length <= 1000
1 <= words[i].length <= 1000
All strings in words have the same length.
1 <= target.length <= 1000
words[i] and target contain only lowercase English letters.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
#define ll long long
class Solution {
    int md = 1e9+7;

    int solve(vector<string>& words, string &target,
     vector<vector<ll>> &ichar, int i, int j, vector<vector<ll>> &dp){
        if (j>=target.size())
            return 1;
        if (i>=words[0].size())
            return 0;
        if (dp[i][j]!=-1)
            return dp[i][j] ;

        ll inc = 0 , exc = 0;

        if (ichar[i][target[j]-'a'])
            inc = ( (ichar[i][target[j]-'a'])*(solve(words,target,ichar,i+1,j+1,dp)) )%md;
        
        exc = solve(words,target,ichar,i+1,j,dp) ;

        return dp[i][j] = (inc+exc)%md;
    }

public:
    int numWays(vector<string>& words, string target) {
        int N = words.size() , M = words[0].size() ;

        vector<vector<ll>> ichar(M,vector<ll>(26)) ;

        for (string &s : words){
            for (int i=0; i<M; i++)
                ichar[i][s[i]-'a']++;
        }

        vector<vector<ll>> dp(M+1,vector<ll>(target.size()+1,-1)) ;

        return solve(words,target,ichar,0,0,dp) ;
    }
};
 </pre>

