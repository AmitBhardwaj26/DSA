
<h2><a href="https://leetcode.com/problems/sum-of-even-numbers-after-queries/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
A city's skyline is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance. Given the locations and heights of all the buildings, return the skyline formed by these buildings collectively.

The geometric information of each building is given in the array buildings where buildings[i] = [lefti, righti, heighti]:

lefti is the x coordinate of the left edge of the ith building.
righti is the x coordinate of the right edge of the ith building.
heighti is the height of the ith building.
You may assume all buildings are perfect rectangles grounded on an absolutely flat surface at height 0.

The skyline should be represented as a list of "key points" sorted by their x-coordinate in the form [[x1,y1],[x2,y2],...]. Each key point is the left endpoint of some horizontal segment in the skyline except the last point in the list, which always has a y-coordinate 0 and is used to mark the skyline's termination where the rightmost building ends. Any ground between the leftmost and rightmost buildings should be part of the skyline's contour.

Note: There must be no consecutive horizontal lines of equal height in the output skyline. For instance, [...,[2 3],[4 5],[7 5],[11 5],[12 7],...] is not acceptable; the three lines of height 5 should be merged into one in the final output as such: [...,[2 3],[4 5],[12 7],...]

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  buildings = [[2,9,10],[3,7,15],[5,12,12],[15,20,10],[19,24,8]]
<strong>Output:</strong> [[2,10],[3,15],[7,12],[12,0],[15,10],[20,8],[24,0]]
</pre>
<pre>
Explanation: At the beginning, the array is [1,2,3,4].
After adding 1 to nums[0], the array is [2,2,3,4], and the sum of even values is 2 + 2 + 4 = 8.
After adding -3 to nums[1], the array is [2,-1,3,4], and the sum of even values is 2 + 4 = 6.
After adding -4 to nums[0], the array is [-2,-1,3,4], and the sum of even values is -2 + 4 = 2.
After adding 2 to nums[3], the array is [-2,-1,3,6], and the sum of even values is -2 + 6 = 4.
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= nums.length <= 104
-104 <= nums[i] <= 104
1 <= queries.length <= 104
-104 <= vali <= 104
0 <= indexi < nums.length
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class Solution {
public:
    vector<vector<int>> getSkyline(vector<vector<int>>& buildings) 
  {
    // upper corner points of all buildings (sorted by x)
    set<vector<int>> upper_corners;     
    for (auto& building : buildings) {
      int L = building[0],  R = building[1], H = building[2];
      
      // NOTE: when x coordinates are same:
      upper_corners.insert({L,-H}); // corner (L,-H): higher left upper corner comes before lower left upper corner;
      upper_corners.insert({R, H}); // corner (R, H): left upper corner comes before right upper corner
    }
    
    vector<vector<int>> res;
    multiset<int> heights = {0}; // sorted building heights (up to sweep line) 
    
    // sweep line to scan upper_corners (to detect max height change)
    for (auto& upper_corner : upper_corners) 
    {
      int preMaxH = *heights.rbegin(); // previous max height (before upper_corner)
      int X = upper_corner[0], H = upper_corner[1];
      if (H < 0)
        heights.insert(-H); // start a new build
      else
        heights.erase(heights.find(H)); // end a previous building
      
      int curMaxH = *heights.rbegin(); // current max height
      if (curMaxH != preMaxH) // max height change found
        res.push_back({X, curMaxH});
    }
    
    return res;
  }
};
 </pre>

