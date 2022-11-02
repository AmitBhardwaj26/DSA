
<h2><a href="https://leetcode.com/problems/minimum-genetic-mutation/description/">433. Minimum Genetic Mutation</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
  A gene string can be represented by an 8-character long string, with choices from 'A', 'C', 'G', and 'T'.

Suppose we need to investigate a mutation from a gene string start to a gene string end where one mutation is defined as one single character changed in the gene string.

For example, "AACCGGTT" --> "AACCGGTA" is one mutation.
There is also a gene bank bank that records all the valid gene mutations. A gene must be in bank to make it a valid gene string.

Given the two gene strings start and end and the gene bank bank, return the minimum number of mutations needed to mutate from start to end. If there is no such a mutation, return -1.

Note that the starting point is assumed to be valid, so it might not be included in the bank
 </p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  start = "AACCGGTT", end = "AACCGGTA", bank = ["AACCGGTA"]
<strong>Output:</strong> 1
</pre>



Constraints:
<pre>
start.length == 8
end.length == 8
0 <= bank.length <= 10
bank[i].length == 8
start, end, and bank[i] consist of only the characters ['A', 'C', 'G', 'T'].
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
            public:
                int minMutation(string start, string end, vector<string>& bank) {
                    int n = bank.size();
                    int len = start.length();
                    set<string> s;
                    for(int i = 0; i < n; i++)
                        s.insert(bank[i]);
                    if(s.count(end) == 0)
                        return -1;
                    string all = "ACGT";
                    unordered_map<string, bool> vis;
                    queue<pair<string, int>> q;
                    q.push({start, 0});
                    while(!q.empty())
                    {
                        string node = q.front().first;
                        int dis = q.front().second;
                        q.pop();
                        if(node == end)
                            return dis;
                        for(int i = 0; i < len; i++)
                        {
                            for(int j = 0; j < 4; j++)
                            {
                                string check = node;
                                check[i] = all[j];
                                if(s.count(check) != 0 && vis[check] != true)
                                {
                                    vis[check] = true;
                                    q.push({check, dis + 1});
                                }
                            }
                        }
                    }
                    return -1;
                }
            };
          
 </pre>

