
<h2><a href="https://leetcode.com/problems/max-points-on-a-line/description/">149. Max Points on a Line</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane, return the maximum number of points that lie on the same straight line.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  points = [[1,1],[2,2],[3,3]]
<strong>Output:</strong> 3
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>

 

Constraints:
<pre>
1 <= points.length <= 300
points[i].length == 2
-104 <= xi, yi <= 104
All the points are unique.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    int maxPoints(vector<vector<int>>& points) {
        if(points.size()==1) return 1;
        int n=points.size(),ans=2;
        
        for(int i=0;i<n-2;i++)
        {
            int x1=points[i][0],y1=points[i][1];
            for(int j=i+1;j<n-1;j++)
            {
               int x2=points[j][0],y2=points[j][1];       
                
                int a=y1-y2,b=x2-x1,c=(x2-x1)*y1+(y1-y2)*x1;
                int count=2;
                for(int k=j+1;k<n;k++)
                {
                   int x3=points[k][0],y3=points[k][1];
                   if((a*x3+ b*y3) == c) 
                   {
                       count++  ;
                       //cout<<"[ "<<x3<<" "<<y3<<" ]\n";
                    } 
                }
                ans=max(ans,count);
            }
        }
        return ans;
    }
};
          
 </pre>

