
<h2><a href="https://leetcode.com/problems/find-median-from-data-stream/description/">295. Find Median from Data Stream</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
The median is the middle value in an ordered integer list. If the size of the list is even, there is no middle value, and the median is the mean of the two middle values.

For example, for arr = [2,3,4], the median is 3.
For example, for arr = [2,3], the median is (2 + 3) / 2 = 2.5.
Implement the MedianFinder class:

MedianFinder() initializes the MedianFinder object.
void addNum(int num) adds the integer num from the data stream to the data structure.
double findMedian() returns the median of all elements so far. Answers within 10-5 of the actual answer will be accepted.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   ["MedianFinder", "addNum", "addNum", "findMedian", "addNum", "findMedian"]  [[], [1], [2], [], [3], []]

<strong>Output:</strong> [null, null, null, 1.5, null, 2.0]
</pre>
<pre>
MedianFinder medianFinder = new MedianFinder();
medianFinder.addNum(1);    // arr = [1]
medianFinder.addNum(2);    // arr = [1, 2]
medianFinder.findMedian(); // return 1.5 (i.e., (1 + 2) / 2)
medianFinder.addNum(3);    // arr[1, 2, 3]
medianFinder.findMedian(); // return 2.0
  </pre>


Constraints:
<pre>
-105 <= num <= 105
There will be at least one element in the data structure before calling findMedian.
At most 5 * 104 calls will be made to addNum and findMedian.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class MedianFinder {
public:
   priority_queue<int> fst;
   priority_queue<int,vector<int>,greater<int>> scnd;
    MedianFinder() {
        
    }
    
    void addNum(int num) {
        if(fst.size()>0 and fst.top()>num) fst.push(num);
        else scnd.push(num);
       if(fst.size()>scnd.size()+1 ) 
       {
           num=fst.top(); fst.pop(); scnd.push(num);
       }
       else if(fst.size()+1<scnd.size())
       {
           num=scnd.top(); scnd.pop(); fst.push(num);
       }
    }
    
    double findMedian() {
        if(fst.size()==scnd.size() ) return ((double)(fst.top()+scnd.top()))/2;
        else if(fst.size()>scnd.size()) return fst.top();
        return scnd.top();
    }
};


          
 </pre>

