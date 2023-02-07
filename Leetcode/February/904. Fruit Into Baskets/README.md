
<h2><a href="https://leetcode.com/problems/fruit-into-baskets/description/">904. Fruit Into Baskets</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
Once you reach a tree with fruit that cannot fit in your baskets, you must stop.
Given the integer array fruits, return the maximum number of fruits you can pick.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   fruits = [1,2,1]
<strong>Output:</strong>3
</pre>
<pre>
Explanation: We can pick from all 3 trees.
  </pre>
  

Constraints:
<pre>
1 <= fruits.length <= 105
0 <= fruits[i] < fruits.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int totalFruit(vector<int>& f) {
        int i=0,j=0,n=f.size();
        map<int,int> m;
        while(j<n && m.size()!=2) m[f[j]]++, j++;
        int ans=j-i;
        while(j<n) 
        {
            m[f[j]]++;
            while(i<j and m.size()>2 ) 
            {
                if(m[f[i]]==1) m.erase(f[i]);
                else m[f[i]]--;
                i++;
            }
           ans=max(ans,j-i+1);
           j++;
        }
        return ans;
    }
};
          
 </pre>

