
<h2><a href="https://leetcode.com/problems/valid-parentheses/description/">20. Valid Parentheses</a></h2>
<h3>Easy</h3>
<hr>
<div><p>
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   s = "()"
<strong>Output:</strong> true
</pre>

 

Constraints:
<pre>
1 <= s.length <= 104
s consists of parentheses only '()[]{}'.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    bool isValid(string s) {
        
        stack<int> st; bool c=true;
        for(int i=0;i<(int)s.size();i++)
        {
            
            if( s[i]=='(' || s[i]=='[' || s[i]=='{')
             {   st.push(s[i]);}
            else 
            { 
                if(st.empty()) return false;
                char ch=st.top();
                
                if(s[i]==')') if(ch!='(') return false; else st.pop();
                else if(s[i]=='}') if(ch!='{') return false; else st.pop();
                else if(s[i]==']') if(ch!='[') return false; else st.pop();
                
            }
                
        }
        if(!st.empty()) return false;
        return true;
    }
};
 </pre>

