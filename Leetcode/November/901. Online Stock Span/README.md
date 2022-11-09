
<h2><a href="https://leetcode.com/problems/online-stock-span/">901. Online Stock Span</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Design an algorithm that collects daily price quotes for some stock and returns the span of that stock's price for the current day.

The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backward) for which the stock price was less than or equal to today's price.

For example, if the price of a stock over the next 7 days were [100,80,60,70,60,75,85], then the stock spans would be [1,1,1,2,1,4,6].
Implement the StockSpanner class:

StockSpanner() Initializes the object of the class.
int next(int price) Returns the span of the stock's price given that today's price is price.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   ["StockSpanner", "next", "next", "next", "next", "next", "next", "next"]
[[], [100], [80], [60], [70], [60], [75], [85]]
<strong>Output:</strong>[null, 1, 1, 1, 2, 1, 4, 6]
</pre>
<pre>
StockSpanner stockSpanner = new StockSpanner();
stockSpanner.next(100); // return 1
stockSpanner.next(80);  // return 1
stockSpanner.next(60);  // return 1
stockSpanner.next(70);  // return 2
stockSpanner.next(60);  // return 1
stockSpanner.next(75);  // return 4, because the last 4 prices (including today's price of 75) were less than or equal to today's price.
stockSpanner.next(85);  // return 6
  </pre>
  

Constraints:
<pre>
1 <= price <= 105
At most 104 calls will be made to next.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class StockSpanner {
            public:
                stack<pair<int,int>> st;
                int i=0;
                StockSpanner() {

                }

                int next(int price) {

                    i++;
                    if(st.size()==0)  { st.push({price,i}); return i;}
                    while(!st.empty() and st.top().first <= price) st.pop();
                    int ans=i;
                    if(!st.empty() ) ans=i - st.top().second ;  

                    st.push({price,i});
                    return ans;
                }
            };

          
 </pre>

