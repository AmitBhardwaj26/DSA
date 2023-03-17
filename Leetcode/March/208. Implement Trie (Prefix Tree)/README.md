
<h2><a href="https://leetcode.com/problems/implement-trie-prefix-tree/description/">985. Sum of Even Numbers After Queries</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

Trie() Initializes the trie object.
void insert(String word) Inserts the string word into the trie.
boolean search(String word) Returns true if the string word is in the trie (i.e., was inserted before), and false otherwise.
boolean startsWith(String prefix) Returns true if there is a previously inserted string word that has the prefix prefix, and false otherwise.
 
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   ["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
<strong>Output:</strong> [null, null, true, false, true, null, true]
</pre>
<pre>
Explanation:Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // return True
trie.search("app");     // return False
trie.startsWith("app"); // return True
trie.insert("app");
trie.search("app");     // return True
  </pre>
  
Example 2:

Input: nums = [1], queries = [[4,0]]
Output: [0]
 

Constraints:
<pre>
1 <= word.length, prefix.length <= 2000
word and prefix consist only of lowercase English letters.
At most 3 * 104 calls in total will be made to insert, search, and startsWith.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Trie {
public:
    struct Node
    {
        Node *links[26]={0};
        bool flag=false; // flag=1 if it is end else flag=0;
        
        bool ischeck(char ch) // check if that char present or not
        {
            return links[ch-'a']!=NULL;
        }
        void put(char ch, Node *node)// put that char with link of empty node
        {
            links[ch-'a']=node;
        }
        Node* get(char ch)// to move to the next node
        {
           return links[ch-'a'];
        }
        void setend()// set end node flag=1;
        {
            flag=true;
        }
        bool getend() // is it end or not
        {
            return flag;
        }
    };
    
    Node *root;
    Trie() {
        root=new Node;
    }
    
    void insert(string word) {
        Node *t=root;
        for(int i=0;i<word.size();i++)
        {
            if(!t->ischeck(word[i]))// check if that char is already presend or not
            {
                t->put(word[i],new Node); //if not then place it
            }
            t= t->get(word[i]);   // move to next node 
        }
        t->setend(); // at the end set the end flag =1
        return ;
    }
    
    bool search(string word) {
        Node *t=root;
        for(int i=0;i<word.size();i++)
        {
            if(!t->ischeck(word[i]))
            {
                return false; // if not present then return false
            }
            t=t->get(word[i]);
        }
        if(t->getend()) // check that is end found or is it substring  of another big string
        {
            return true;
        }
        return false;
    }
    
    bool startsWith(string prefix) {
        Node *t=root;
        for(int i=0;i<prefix.size();i++)
        {
            if(!t->ischeck(prefix[i]))
            {
                return false;
            }
            t=t->get(prefix[i]);
        }
        return true;
    }
};
 </pre>

