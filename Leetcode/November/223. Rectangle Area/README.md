
<h2><a href="https://leetcode.com/problems/rectangle-area/">223. Rectangle Area</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Given the coordinates of two rectilinear rectangles in a 2D plane, return the total area covered by the two rectangles.

The first rectangle is defined by its bottom-left corner (ax1, ay1) and its top-right corner (ax2, ay2).

The second rectangle is defined by its bottom-left corner (bx1, by1) and its top-right corner (bx2, by2).
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    ax1 = -3, ay1 = 0, ax2 = 3, ay2 = 4, bx1 = 0, by1 = -1, bx2 = 9, by2 = 2
<strong>Output:</strong> 45
</pre>

Example 2:

Input: ax1 = -2, ay1 = -2, ax2 = 2, ay2 = 2, bx1 = -2, by1 = -2, bx2 = 2, by2 = 2
Output: 16
 

Constraints:
<pre>
-104 <= ax1 <= ax2 <= 104
-104 <= ay1 <= ay2 <= 104
-104 <= bx1 <= bx2 <= 104
-104 <= by1 <= by2 <= 104
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
class Solution {
public:
    int computeArea(int ax1, int ay1, int ax2, int ay2, int bx1, int by1, int bx2, int by2) {
        int Minx=min({ax1,ax2,bx1,bx2}) ,Miny=min({ay1,ay2,by1,by2});
        // made all the coordinates in positive X,Y axis; 
        Minx=abs(Minx); Miny=abs(Miny);
        ax1+=Minx; ax2+=Minx; bx1+=Minx; bx2+=Minx;
        ay1+=Miny; ay2+=Miny; by1+=Miny; by2+=Miny;
        
        // find the area occupied by both rectangles
        long ans= (long)abs(ax2-ax1)*(abs(ay2-ay1)) +
                  (long)abs(bx2-bx1)*(abs(by2-by1));
        
        // calculate the (x1,y1) , (x2,y2) part of overlap rectangle
        int x1 = max(ax1,bx1),x2=min(ax2,bx2);
        int y1=max(ay1,by1),y2=min(ay2,by2);
        
        // if no overlap found
        if((x2-x1)<=0 || (y2-y1)<=0) return ans;
        
         // substract the overlap rectangle
        return ans-(x2-x1)*(y2-y1);    
    }
};
          
 </pre>

