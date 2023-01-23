
<h2><a href="https://leetcode.com/problems/find-the-town-judge/description/">9997. Find the Town Judge</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
In a town, there are n people labeled from 1 to n. There is a rumor that one of these people is secretly the town judge.

If the town judge exists, then:

The town judge trusts nobody.
Everybody (except for the town judge) trusts the town judge.
There is exactly one person that satisfies properties 1 and 2.
You are given an array trust where trust[i] = [ai, bi] representing that the person labeled ai trusts the person labeled bi.

Return the label of the town judge if the town judge exists and can be identified, or return -1 otherwise.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   n = 2, trust = [[1,2]]
<strong>Output:</strong>  2
</pre>



Constraints:
<pre>
1 <= n <= 1000
0 <= trust.length <= 104
trust[i].length == 2
All the pairs of trust are unique.
ai != bi
1 <= ai, bi <= n
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int findJudge(int n, vector<vector<int>>& t) {
        map<int,int> m,m2;
        for(int i=0;i<t.size();i++)
        {
            m2[t[i][0]]++;
            m[t[i][1]]++; m[t[i][1]]+=1;
        }
        for(int i=1;i<=n;i++)
        {
            if(m[i]==2*(n-1) && m2[i]==0 )
            {
                return i;
            }
        }
        
        return -1;
    }
};
          
 </pre>

