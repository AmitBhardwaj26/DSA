
<h2><a href="https://leetcode.com/problems/basic-calculator/description/">224. Basic Calculator</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
 Given a string s representing a valid expression, implement a basic calculator to evaluate it, and return the result of the evaluation.

Note: You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as eval().
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    s = "1 + 1"
<strong>Output:</strong>2
</pre>

  
Input: s = "(1+(4+5+2)-3)+(6+8)"
Output: 23

Constraints:
<pre>
1 <= s.length <= 3 * 105
s consists of digits, '+', '-', '(', ')', and ' '.
s represents a valid expression.
'+' is not used as a unary operation (i.e., "+1" and "+(2 + 3)" is invalid).
'-' could be used as a unary operation (i.e., "-1" and "-(2 + 3)" is valid).
There will be no two consecutive operators in the input.
Every number and running calculation will fit in a signed 32-bit integer.

</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
 public:
    int calculate(string s) 
    {
        long long ans = 0, level = 0, op = 0, sign = 1;
         stack<int> d; d.push(1);
        for (auto c : s)
        {
           if (c == ' ') continue;
           if (c == '-' || c == '+' || c == '(' || c == ')')
           {
               if (op)
               {
                   ans += op * sign;
                   op = 0;
                }
            }
      if (c == '-' || c == '+')
       {
         sign = (c == '-' ? -1 : 1) * d.top();
       }
      else if (c >= '0' && c <= '9')
       op = op * 10 + c - '0';

       else if (c == '(') d.push(sign);
      else if (c == ')') d.pop();
    }
     return ans + op * sign;
  }
};
 </pre>

