
<h2><a href="https://practice.geeksforgeeks.org/problems/minimum-characters-to-be-added-at-front-to-make-string-palindrome/1">Minimum characters to be added at front to make string palindrome</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
  Given string str of length N. The task is to find the minimum characters to be added at the front to make string palindrome.
Note: A palindrome is a word which reads the same backward as forward. Example: "madam".
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   S = "abc"
<strong>Output:</strong> 2
</pre>
<pre>



Constraints:
<pre>
You don't need to read input or print anything. Your task is to complete the function minChar() which takes a string S and returns an integer as output.

Expected Time Complexity: O(N)
Expected Auxiliary Space: O(N)
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int minChar(string str)
    {
        int n=str.size();
        int i=0,j=n-1,j2=j,count=0;
        while(i<j)
        {
            if(str[i]==str[j])
            {
                i++,j--;
            }
            else 
            {
                count++;
                j2--;
                j=j2; 
                i=0;
            }
        }
        return count;
        //Write your code here
    }
};
          
 </pre>

