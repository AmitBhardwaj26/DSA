
<h2><a href="https://leetcode.com/problems/minimum-rounds-to-complete-all-tasks/description/">2244. Minimum Rounds to Complete All Tasks</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given a 0-indexed integer array tasks, where tasks[i] represents the difficulty level of a task. In each round, you can complete either 2 or 3 tasks of the same difficulty level.

Return the minimum rounds required to complete all the tasks, or -1 if it is not possible to complete all the tasks.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   tasks = [2,2,3,3,2,4,4,4,4,4]
<strong>Output:</strong> 4
</pre>
<pre>
Explanation To complete all the tasks, a possible plan is:
- In the first round, you complete 3 tasks of difficulty level 2. 
- In the second round, you complete 2 tasks of difficulty level 3. 
- In the third round, you complete 3 tasks of difficulty level 4. 
- In the fourth round, you complete 2 tasks of difficulty level 4.  
It can be shown that all the tasks cannot be completed in fewer than 4 rounds, so the answer is 4.
  </pre>

 

Constraints:
<pre>
1 <= tasks.length <= 105
1 <= tasks[i] <= 109
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int minimumRounds(vector<int>& task) {
        int n=task.size();
        map<int,int > m;
        for(int i=0;i<n;i++)
        {
           m[task[i]]++;
        } 
        int ans=0;
        for(auto i : m)
        {
            int it=i.second;
            if(it==1) return -1;
           int x=it%3,y=it/3;
           if(x==0) ans+=y;
           else ans+=y+1;
           cout<<ans<<"\n";
        }
        return ans;
    }
};
          
 </pre>

