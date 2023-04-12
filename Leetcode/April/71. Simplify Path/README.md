
<h2><a href="https://leetcode.com/problems/simplify-path/description/">71. Simplify Path</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given a string path, which is an absolute path (starting with a slash '/') to a file or directory in a Unix-style file system, convert it to the simplified canonical path.

In a Unix-style file system, a period '.' refers to the current directory, a double period '..' refers to the directory up a level, and any multiple consecutive slashes (i.e. '//') are treated as a single slash '/'. For this problem, any other format of periods such as '...' are treated as file/directory names.

The canonical path should have the following format:

The path starts with a single slash '/'.
Any two directories are separated by a single slash '/'.
The path does not end with a trailing '/'.
The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period '.' or double period '..')
Return the simplified canonical path.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  path = "/home/"
<strong>Output:</strong> "/home"
</pre>
<pre>
Explanation:  Note that there is no trailing slash after the last directory name.
  </pre>


Constraints:
<pre>
1 <= path.length <= 3000
path consists of English letters, digits, period '.', slash '/' or '_'.
path is a valid absolute Unix path.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
   class Solution {
public:
    string simplifyPath(string p) {
        stack<string> s;
        int n=p.size();
        for(int i=0;i<n;i++)
        {
            if(p[i]=='/') continue;
            string temp="";
            int j=i;
            while(i<n && p[i]!='/')
               { temp+=p[i]; i++;}
            if(temp==".." || temp==".") 
            {if(temp==".." && !s.empty()) s.pop();}
            else s.push(temp);
        }
        string ans="";
        while(!s.empty())
        {
            ans="/" + s.top()+ans;
            s.pop();
        }
        return ans==""?"/":ans;
    }
}; 
 </pre>

