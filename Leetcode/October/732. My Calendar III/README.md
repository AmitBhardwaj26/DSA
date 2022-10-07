
<h2><a href="https://leetcode.com/problems/my-calendar-iii/description/">732. My Calendar III</a></h2>
<h3>Hard</h3>
<hr>
<div><p>
 A k-booking happens when k events have some non-empty intersection (i.e., there is some time that is common to all k events.)

You are given some events [start, end), after each given event, return an integer k representing the maximum k-booking between all the previous events.

Implement the MyCalendarThree class:

MyCalendarThree() Initializes the object.
int book(int start, int end) Returns an integer k representing the largest integer such that there exists a k-booking in the calendar.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  ["MyCalendarThree", "book", "book", "book", "book", "book", "book"]
[[], [10, 20], [50, 60], [10, 40], [5, 15], [5, 10], [25, 55]]
<strong>Output:</strong> [null, 1, 1, 2, 3, 3, 3]
</pre>
<pre>
MyCalendarThree myCalendarThree = new MyCalendarThree();
myCalendarThree.book(10, 20); // return 1, The first event can be booked and is disjoint, so the maximum k-booking is a 1-booking.
myCalendarThree.book(50, 60); // return 1, The second event can be booked and is disjoint, so the maximum k-booking is a 1-booking.
myCalendarThree.book(10, 40); // return 2, The third event [10, 40) intersects the first event, and the maximum k-booking is a 2-booking.
myCalendarThree.book(5, 15); // return 3, The remaining events cause the maximum K-booking to be only a 3-booking.
myCalendarThree.book(5, 10); // return 3
myCalendarThree.book(25, 55); // return 3
  </pre>
  


Constraints:
<pre>
0 <= start < end <= 109
At most 400 calls will be made to book.
</pre>

<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
//this question is based on continious allocation and dealcation in the memory 
//version of kadane algo
class MyCalendarThree {
public:
    map<int,int> m;
    MyCalendarThree() {
        
    }
    
    int book(int start, int end) {
        m[start]++;
        m[end]--;
        int val=0,ans=0;
        for(auto it:m)
        {
            val+=it.second;
            ans=max(ans,val);
        }
        return ans;
    }
};

          
 </pre>

