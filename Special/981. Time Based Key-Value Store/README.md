
<h2><a href="https://leetcode.com/problems/time-based-key-value-store/description/">981. Time Based Key-Value Store</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 You are given an integer array nums and an array queries where queries[i] = [vali, indexi].

For each query i, first, apply nums[indexi] = nums[indexi] + vali, then print the sum of the even values of nums.

Return an integer array answer where answer[i] is the answer to the ith query.
</p>
Design a time-based key-value data structure that can store multiple values for the same key at different time stamps and retrieve the key's value at a certain timestamp.

Implement the TimeMap class:

TimeMap() Initializes the object of the data structure.
void set(String key, String value, int timestamp) Stores the key key with the value value at the given time timestamp.
String get(String key, int timestamp) Returns a value such that set was called previously, with timestamp_prev <= timestamp. If there are multiple such values, it returns the value associated with the largest timestamp_prev. If there are no values, it returns "".
  </pre>
  <pre>
Input
["TimeMap", "set", "get", "get", "set", "get", "get"]
[[], ["foo", "bar", 1], ["foo", 1], ["foo", 3], ["foo", "bar2", 4], ["foo", 4], ["foo", 5]]
Output
[null, null, "bar", "bar", null, "bar2", "bar2"]
</pre> 

Constraints:
<pre>
1 <= key.length, value.length <= 100
key and value consist of lowercase English letters and digits.
1 <= timestamp <= 107
All the timestamps timestamp of set are strictly increasing.
At most 2 * 105 calls will be made to set and get.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        class TimeMap {
    unordered_map<string, vector<pair<int, string>>> mpp;
public:
    TimeMap() {
        
    }
    
    void set(string key, string value, int timestamp) {
        mpp[key].push_back(make_pair(timestamp, value));
    }
    
    string get(string key, int timestamp) {
        string res;
        int low = 0, high = mpp[key].size() - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (mpp[key][mid].first <= timestamp) {
                res = mpp[key][mid].second;
                low = mid + 1;
            }
            else
                high = mid - 1;
        }
        return res;
    }
};
 </pre>

