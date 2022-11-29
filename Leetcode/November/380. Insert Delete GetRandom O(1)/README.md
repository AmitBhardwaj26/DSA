
<h2><a href="https://leetcode.com/problems/insert-delete-getrandom-o1/">380. Insert Delete GetRandom O(1)</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Implement the RandomizedSet class:

RandomizedSet() Initializes the RandomizedSet object.
bool insert(int val) Inserts an item val into the set if not present. Returns true if the item was not present, false otherwise.
bool remove(int val) Removes an item val from the set if present. Returns true if the item was present, false otherwise.
int getRandom() Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element must have the same probability of being returned.
You must implement the functions of the class such that each function works in average O(1) time complexity.

 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   ["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
[[], [1], [2], [2], [], [1], [2], []]
<strong>Output:</strong> [null, true, false, true, 2, true, false, 2]
</pre>
<pre>
RandomizedSet randomizedSet = new RandomizedSet();
randomizedSet.insert(1); // Inserts 1 to the set. Returns true as 1 was inserted successfully.
randomizedSet.remove(2); // Returns false as 2 does not exist in the set.
randomizedSet.insert(2); // Inserts 2 to the set, returns true. Set now contains [1,2].
randomizedSet.getRandom(); // getRandom() should return either 1 or 2 randomly.
randomizedSet.remove(1); // Removes 1 from the set, returns true. Set now contains [2].
randomizedSet.insert(2); // 2 was already in the set, so return false.
randomizedSet.getRandom(); // Since 2 is the only number in the set, getRandom() will always return 2.  </pre>


Constraints:
<pre>
-231 <= val <= 231 - 1
At most 2 * 105 calls will be made to insert, remove, and getRandom.
There will be at least one element in the data structure when getRandom is called.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        // make a vector map store the index in the vector swap with the last index while removing

class RandomizedSet {
public:
int x=-1,N=1e5; 
int l=0;
vector<int> v;
unordered_map<int,int> m;
    RandomizedSet() {
        v.resize(100001);
    }
    
    bool insert(int val) {
        if(m[val]!=0) return 0;

        v[l]=val; l++;
        m[val]=l;
        return 1;
    }
    
    bool remove(int val) {
        if(m[val]==0|| l==0) return 0;
        else { x=m[val]; l--; m[v[l]]=x; swap(v[x-1],v[l]); m[val]=0;  }
        return 1;
    }
    
    int getRandom() {
       x=rand()%l;
       return v[x];
    }
};


          
 </pre>

