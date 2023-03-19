
<h2><a href="https://leetcode.com/problems/design-add-and-search-words-data-structure/description/">211. Design Add and Search Words Data Structure</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the WordDictionary class:

WordDictionary() Initializes the object.
void addWord(word) Adds word to the data structure, it can be matched later.
bool search(word) Returns true if there is any string in the data structure that matches word or false otherwise. word may contain dots '.' where dots can be matched with any letter.
 </p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  ["WordDictionary","addWord","addWord","addWord","search","search","search","search"]
[[],["bad"],["dad"],["mad"],["pad"],["bad"],[".ad"],["b.."]]
<strong>Output:</strong> [null,null,null,null,false,true,true,true]
</pre>
<pre>
Explanation: WordDictionary wordDictionary = new WordDictionary();
wordDictionary.addWord("bad");
wordDictionary.addWord("dad");
wordDictionary.addWord("mad");
wordDictionary.search("pad"); // return False
wordDictionary.search("bad"); // return True
wordDictionary.search(".ad"); // return True
wordDictionary.search("b.."); // return True
  </pre>
  


Constraints:
<pre>
1 <= word.length <= 25
word in addWord consists of lowercase English letters.
word in search consist of '.' or lowercase English letters.
There will be at most 3 dots in word for search queries.
At most 104 calls will be made to addWord and search.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>

class TrieNode {
public:
    unordered_map<char, TrieNode*> children;
    bool isWord;
    
    TrieNode() {
        isWord = false;
    }
};

class WordDictionary {
private:
    TrieNode* root;

public:
    WordDictionary() {
        root = new TrieNode();
    }

    void addWord(string word) {
        TrieNode* node = root;
        // Traverse the trie for each character in the word
        for (int i = 0; i < word.length(); i++) {
            char c = word[i];
            // If the current node does not have a child with character c,
            // create a new node and add it as a child of the current node
            if (node->children.find(c) == node->children.end()) {
                node->children[c] = new TrieNode();
            }
            // Move to the child node corresponding to character c
            node = node->children[c];
        }
        // Mark the last node as a word node
        node->isWord = true;
    }

    bool search(string word) {
        return searchHelper(root, word, 0);
    }

    bool searchHelper(TrieNode* node, string& word, int index) {
        // If we have reached the end of the word,
        // check if the current node is a word node
        if (index == word.length()) {
            return node->isWord;
        }
        char c = word[index];
        if (c == '.') {
            // If the current character is a dot, we need to check all children of the current node
            // recursively by skipping over the dot character and moving to the next character of the word
            for (auto& p : node->children) {
                if (searchHelper(p.second, word, index + 1)) {
                    return true;
                }
            }
            // If no child node matches the remaining characters of the word,
            // return false
            return false;
        } else {
            // If the current character is not a dot, move to the child node
            // corresponding to that character and continue recursively
            if (node->children.find(c) == node->children.end()) {
                // If there is no child node corresponding to the current character,
                // return false
                return false;
            }
            TrieNode* child = node->children[c];
            return searchHelper(child, word, index + 1);
        }
    }
};
 </pre>

