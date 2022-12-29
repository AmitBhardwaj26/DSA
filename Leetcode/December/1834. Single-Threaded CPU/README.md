
<h2><a href="https://leetcode.com/problems/single-threaded-cpu/description/">1834. Single-Threaded CPU</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given n tasks labeled from 0 to n - 1 represented by a 2D integer array tasks, where tasks[i] = [enqueueTimei, processingTimei] means that the ih task will be available to process at enqueueTimei and will take processingTimei to finish processing.

You have a single-threaded CPU that can process at most one task at a time and will act in the following way:
  If the CPU is idle and there are no available tasks to process, the CPU remains idle.
If the CPU is idle and there are available tasks, the CPU will choose the one with the shortest processing time. If multiple tasks have the same shortest processing time, it will choose the task with the smallest index.
Once a task is started, the CPU will process the entire task without stopping.
The CPU can finish a task then start a new one instantly.
Return the order in which the CPU will process the tasks.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  tasks = [[1,2],[2,4],[3,2],[4,1]]
<strong>Output:</strong> [0,2,3,1]
</pre>
<pre>
The events go as follows: 
- At time = 1, task 0 is available to process. Available tasks = {0}.
- Also at time = 1, the idle CPU starts processing task 0. Available tasks = {}.
- At time = 2, task 1 is available to process. Available tasks = {1}.
- At time = 3, task 2 is available to process. Available tasks = {1, 2}.
- Also at time = 3, the CPU finishes task 0 and starts processing task 2 as it is the shortest. Available tasks = {1}.
- At time = 4, task 3 is available to process. Available tasks = {1, 3}.
- At time = 5, the CPU finishes task 2 and starts processing task 3 as it is the shortest. Available tasks = {1}.
- At time = 6, the CPU finishes task 3 and starts processing task 1. Available tasks = {}.
- At time = 10, the CPU finishes task 1 and becomes idle.

  </pre>

 

Constraints:
<pre>
tasks.length == n
1 <= n <= 105
1 <= enqueueTimei, processingTimei <= 109
</pre>
  
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
#define ll long long 
#define ss second
#define ff first
#define pii pair<ll,ll>
public:
    vector<int> getOrder(vector<vector<int>>& task) {
        vector<pair<ll,pii>> tasks;
        for(int i=0;i<task.size();i++)
        {
            tasks.push_back({task[i][0],{task[i][1],i}});
        }
        sort(tasks.begin(),tasks.end());
        priority_queue<pair<int,pii>,vector<pair<int,pii>>,greater<pair<int,pii>>> pq;
        vector<int> ans;
        ll i=0,t=1, n=tasks.size() ,prev=0;
        // pq.push({tasks[i][1],0});
        while(ans.size()!=n)
        {
            while(i<n && (prev>=tasks[i].ff || prev==0)) 
            {
                pq.push({tasks[i].ss.ff,{tasks[i].ss.ss , tasks[i].ff}}); 
                if(prev==0) prev=tasks[i].ff;
                i++; 
            }
            // cout<<prev<<"| "<<pq.top().ff<<" "<<pq.top().ss<<"\n";
            if(pq.size()==0) {prev=0; continue;}
            prev= max(prev,pq.top().ss.ss);
            prev+=pq.top().ff; ans.push_back(pq.top().ss.ff);
            // cout<<prev<<" ";
            pq.pop();
        }
        return ans;
    }
};
          
 </pre>

