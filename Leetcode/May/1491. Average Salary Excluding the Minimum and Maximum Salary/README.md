
<h2><a href="https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary/description/">1491. Average Salary Excluding the Minimum and Maximum Salary</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array of unique integers salary where salary[i] is the salary of the ith employee.

Return the average salary of employees excluding the minimum and maximum salary. Answers within 10-5 of the actual answer will be accepted.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    salary = [4000,3000,1000,2000]
<strong>Output:</strong> [8,6,2,4]
</pre>
<pre>
Explanation: Minimum salary and maximum salary are 1000 and 4000 respectively.
Average salary excluding minimum and maximum salary is (2000+3000) / 2 = 2500
  </pre>
  
Constraints:
<pre>
3 <= salary.length <= 100
1000 <= salary[i] <= 106
All the integers of salary are unique.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    double average(vector<int>& salary) {
        double sum=0;
        for(int i=0;i<salary.size();i++)
            sum+=salary[i];
        int a=*min_element(salary.begin(),salary.end());
        int b=*max_element(salary.begin(),salary.end());
        int avg=salary.size()-2;
        return (double)(sum-a-b)/avg;
        
    }
}; 
 </pre>

