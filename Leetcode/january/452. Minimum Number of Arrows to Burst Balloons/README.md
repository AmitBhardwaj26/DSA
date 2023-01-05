
<h2><a href="https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/">452. Minimum Number of Arrows to Burst Balloons</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
There are some spherical balloons taped onto a flat wall that represents the XY-plane. The balloons are represented as a 2D integer array points where points[i] = [xstart, xend] denotes a balloon whose horizontal diameter stretches between xstart and xend. You do not know the exact y-coordinates of the balloons.

Arrows can be shot up directly vertically (in the positive y-direction) from different points along the x-axis. A balloon with xstart and xend is burst by an arrow shot at x if xstart <= x <= xend. There is no limit to the number of arrows that can be shot. A shot arrow keeps traveling up infinitely, bursting any balloons in its path.

Given the array points, return the minimum number of arrows that must be shot to burst all balloons.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  points = [[10,16],[2,8],[1,6],[7,12]]
<strong>Output:</strong> 2
</pre>
<pre>
Explanation:The balloons can be burst by 2 arrows:
- Shoot an arrow at x = 6, bursting the balloons [2,8] and [1,6].
- Shoot an arrow at x = 11, bursting the balloons [10,16] and [7,12].
  </pre>
  


Constraints:
<pre>
1 <= points.length <= 105
points[i].length == 2
-231 <= xstart < xend <= 231 - 1
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& p) {
        sort(p.begin(),p.end(),[](vector<int> &v1,vector<int> &v2)
             {return v1[0]<v2[0]; });
        int count=0,i=0;
        while(i<p.size())
        {
            cout<<p[i][0]<<" "<<p[i][1]<<" \n";
            int x=p[i][1]; count++;  i++;
            while(i<p.size() && x>=p[i][0]  ) 
                { x=min(x,p[i][1]); i++;  }
            
        }
        
        return count;
    }
};
          
 </pre>

