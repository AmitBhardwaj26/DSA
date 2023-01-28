
<h2><a href="https://leetcode.com/problems/data-stream-as-disjoint-intervals/description/">352. Data Stream as Disjoint Intervals</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 
Given a data stream input of non-negative integers a1, a2, ..., an, summarize the numbers seen so far as a list of disjoint intervals.

Implement the SummaryRanges class:

SummaryRanges() Initializes the object with an empty stream.
void addNum(int value) Adds the integer value to the stream.
int[][] getIntervals() Returns a summary of the integers in the stream currently as a list of disjoint intervals [starti, endi]. The answer should be sorted by starti.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  ["SummaryRanges", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals"]
[[], [1], [], [3], [], [7], [], [2], [], [6], []]
<strong>Output:</strong> [null, null, [[1, 1]], null, [[1, 1], [3, 3]], null, [[1, 1], [3, 3], [7, 7]], null, [[1, 3], [7, 7]], null, [[1, 3], [6, 7]]]
</pre>
<pre>
Explanation: SummaryRanges summaryRanges = new SummaryRanges();
summaryRanges.addNum(1);      // arr = [1]
summaryRanges.getIntervals(); // return [[1, 1]]
summaryRanges.addNum(3);      // arr = [1, 3]
summaryRanges.getIntervals(); // return [[1, 1], [3, 3]]
summaryRanges.addNum(7);      // arr = [1, 3, 7]
summaryRanges.getIntervals(); // return [[1, 1], [3, 3], [7, 7]]
summaryRanges.addNum(2);      // arr = [1, 2, 3, 7]
summaryRanges.getIntervals(); // return [[1, 3], [7, 7]]
summaryRanges.addNum(6);      // arr = [1, 2, 3, 6, 7]
summaryRanges.getIntervals(); // return [[1, 3], [6, 7]]
  </pre>
  


Constraints:
<pre>
0 <= value <= 104
At most 3 * 104 calls will be made to addNum and getIntervals.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
         class SummaryRanges {
public:
    set<int> nums;
    SummaryRanges() {
        
    }
    
    void addNum(int value) {
        nums.insert(value);
    }
    
    vector<vector<int>> getIntervals() {
        vector<vector<int>> intervals;
        int start = *nums.begin();
        int end = *nums.begin();
        for (auto it = ++nums.begin(); it != nums.end(); it++) {
            int val = *it;
            if (val - end == 1) {
                end = val;
            } else {
                intervals.push_back({start, end});
                start = end = val;
            }
        }
        intervals.push_back({start, end});
        return intervals;
        
    }
};


          
 </pre>

