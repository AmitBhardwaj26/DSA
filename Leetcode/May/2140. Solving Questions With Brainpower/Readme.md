
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">2140. Solving Questions With Brainpower</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given a 0-indexed 2D integer array questions where questions[i] = [pointsi, brainpoweri].

The array describes the questions of an exam, where you have to process the questions in order (i.e., starting from question 0) and make a decision whether to solve or skip each question. Solving question i will earn you pointsi points but you will be unable to solve each of the next brainpoweri questions. If you skip question i, you get to make the decision on the next question.

For example, given questions = [[3, 2], [4, 3], [4, 4], [2, 5]]:
If question 0 is solved, you will earn 3 points but you will be unable to solve questions 1 and 2.
If instead, question 0 is skipped and question 1 is solved, you will earn 4 points but you will be unable to solve questions 2 and 3.
Return the maximum points you can earn for the exam.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  questions = [[3,2],[4,3],[4,4],[2,5]]
<strong>Output:</strong>  5
</pre>
<pre>
Explanation:The maximum points can be earned by solving questions 0 and 3.
- Solve question 0: Earn 3 points, will be unable to solve the next 2 questions
- Unable to solve questions 1 and 2
- Solve question 3: Earn 2 points
Total points earned: 3 + 2 = 5. There is no other way to earn 5 or more points.

  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= questions.length <= 105
questions[i].length == 2
1 <= pointsi, brainpoweri <= 105
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
     vector<long long> dp;
    long long solve(vector<vector<int>>& q, int n ) 
    {
        //base case
        if(n>=q.size() ) return 0;
        
         if( dp[n]!=-1) return dp[n]; 
         
         
        //choice diagram
        return dp[n]=max((long long)q[n][0]+(long long)solve(q,n+q[n][1]+1) , (long long)solve(q,n+1) );
       
    }
    
    
    long long mostPoints(vector<vector<int>>& qu) {
        int n=qu.size();
         dp.resize(n+1,-1);
        //memset(dp,-1,sizeof(dp));
        return solve(qu,0);
    }
};
 </pre>

