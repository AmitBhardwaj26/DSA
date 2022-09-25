
<h2><a href="https://leetcode.com/problems/design-circular-queue/">622. Design Circular Queue</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Design your implementation of the circular queue. The circular queue is a linear data structure in which the operations are performed based on FIFO (First In First Out) principle and the last position is connected back to the first position to make a circle. It is also called "Ring Buffer".

One of the benefits of the circular queue is that we can make use of the spaces in front of the queue. In a normal queue, once the queue becomes full, we cannot insert the next element even if there is a space in front of the queue. But using the circular queue, we can use the space to store new values.

Implementation the MyCircularQueue class:

MyCircularQueue(k) Initializes the object with the size of the queue to be k.
int Front() Gets the front item from the queue. If the queue is empty, return -1.
int Rear() Gets the last item from the queue. If the queue is empty, return -1.
boolean enQueue(int value) Inserts an element into the circular queue. Return true if the operation is successful.
boolean deQueue() Deletes an element from the circular queue. Return true if the operation is successful.
boolean isEmpty() Checks whether the circular queue is empty or not.
boolean isFull() Checks whether the circular queue is full or not.
You must solve the problem without using the built-in queue data structure in your programming language. 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  ["MyCircularQueue", "enQueue", "enQueue", "enQueue", "enQueue", "Rear", "isFull", "deQueue", "enQueue", "Rear"]
[[3], [1], [2], [3], [4], [], [], [], [4], []]
<strong>Output:</strong>[null, true, true, true, false, 3, true, true, true, 4]
</pre>
<pre>
MyCircularQueue myCircularQueue = new MyCircularQueue(3);
myCircularQueue.enQueue(1); // return True
myCircularQueue.enQueue(2); // return True
myCircularQueue.enQueue(3); // return True
myCircularQueue.enQueue(4); // return False
myCircularQueue.Rear();     // return 3
myCircularQueue.isFull();   // return True
myCircularQueue.deQueue();  // return True
myCircularQueue.enQueue(4); // return True
myCircularQueue.Rear();     // return 4
</pre>
  

Constraints:
<pre>
1 <= k <= 1000
0 <= value <= 1000
At most 3000 calls will be made to enQueue, deQueue, Front, Rear, isEmpty, and isFull.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 // the simple approch is that to made a vector of max  length and take two pointer take the size k=k+1 , 
 // initailise i and j to 0 and 0 front will be (i+1)%k and rear at j full is (j+1)%k==i empty if i==j

class MyCircularQueue {
public:
    int v[1002]; int i=0,j=0, k;
    MyCircularQueue(int p) 
    {
        k=p+1;
    }
    
    bool enQueue(int value) {
        if(!isFull()) 
        {
            j=(j+1)%k; 
            v[j]=value;
            return 1;
        }
        return 0;
    }
    
    bool deQueue() {
         if(!isEmpty()) {
            i=(i+1)%k; 
            return 1;
        }
        return 0;
    }
    
    int Front() {
        if(isEmpty()) return -1;
        return v[(i+1)%k];
    }
    
    int Rear() 
    {
        if(isEmpty()) return -1;
        return v[j];
    }
    
    bool isEmpty() {
        if(i==j) return 1;
        return 0;
    }
    
    bool isFull() 
    {
        if((j+1)%k ==i)    return 1;
        return 0;
    }
};


          
 </pre>

