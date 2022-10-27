
<h2><a href="https://leetcode.com/problems/image-overlap/description/">835. Image Overlap</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given two images, img1 and img2, represented as binary, square matrices of size n x n. A binary matrix has only 0s and 1s as values.

We translate one image however we choose by sliding all the 1 bits left, right, up, and/or down any number of units. We then place it on top of the other image. We can then calculate the overlap by counting the number of positions that have a 1 in both images.

Note also that a translation does not include any kind of rotation. Any 1 bits that are translated outside of the matrix borders are erased.

Return the largest possible overlap.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   img1 = [[1,1,0],[0,1,0],[0,1,0]], img2 = [[0,0,0],[0,1,1],[0,0,1]]
<strong>Output:</strong> 3
</pre>
<pre>
We translate img1 to right by 1 unit and down by 1 unit.

The number of positions that have a 1 in both images is 3 (shown in red).

  </pre>
  

 

Constraints:
<pre>
n == img1.length == img1[i].length
n == img2.length == img2[i].length
1 <= n <= 30
img1[i][j] is either 0 or 1.
img2[i][j] is either 0 or 1.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
          // brute force of all 1 that collide they have same difference of indexes
// we can use pair as a key in map
class Solution {
public:
    int largestOverlap(vector<vector<int>>& img1, vector<vector<int>>& img2) {
        vector<pair<int,int>> p1,p2;
        int n=img1.size();
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) if(img1[i][j]==1) p1.push_back({i,j});
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) if(img2[i][j]==1) p2.push_back({i,j});
        
        map<pair<int,int>,int> m;
        int ans=0;
        for(int i=0;i<p1.size();i++)
        {
            for(int j=0;j<p2.size();j++)
            {
                int x=p2[j].first-p1[i].first,y=p2[j].second- p1[i].second;
                m[{x,y }]++;
                ans=max(ans,m[{x,y}]);
            }
        }
    return ans;

    }
};
          
 </pre>

