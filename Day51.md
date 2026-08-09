# Day 51-50 Days of Code

 Date: 08-08-2026

---

##  DSA Questions Solved
(Binary Trees)
Iterative methods
- [Preorder, Inorder, Postorder in one traversal]
- [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
- [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)
- [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

[Preorder, Inorder, Postorder in one traversal]
```cpp
#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    Node *left, *right;
    
    Node(int val) {
        data = val;
        left = right = NULL;
    }
};

void allTraversals(Node* root) {
    if (root == NULL) return;

    vector<int> preorder, inorder, postorder;
    
    stack<pair<Node*, int>> st;
    st.push({root, 1});

    while (!st.empty()) {
        auto it = st.top();
        st.pop();

        // State 1 → Preorder
        if (it.second == 1) {
            preorder.push_back(it.first->data);
            it.second++;
            st.push(it);

            if (it.first->left) {
                st.push({it.first->left, 1});
            }
        }
        // State 2 → Inorder
        else if (it.second == 2) {
            inorder.push_back(it.first->data);
            it.second++;
            st.push(it);

            if (it.first->right) {
                st.push({it.first->right, 1});
            }
        }
        // State 3 → Postorder
        else {
            postorder.push_back(it.first->data);
        }
    }

    // Print results
    cout << "Preorder: ";
    for (auto x : preorder) cout << x << " ";
    cout << endl;

    cout << "Inorder: ";
    for (auto x : inorder) cout << x << " ";
    cout << endl;

    cout << "Postorder: ";
    for (auto x : postorder) cout << x << " ";
    cout << endl;
}

// Example usage
int main() {
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);

    allTraversals(root);

    return 0;
}
```

Maximum Depth of Binary Tree
```cpp
    int maxDepth(TreeNode* root) {

        if(root==NULL) return 0;
        int lh=maxDepth(root->left);
        int rh=maxDepth(root->right);
        return 1+ max(lh,rh);
    }
```

Balanced BT
TC: O(N)
SC: O(N) [worst case for a skewed tree]
 ```cpp
 int depth(TreeNode* root){
        if(root==NULL) return 0;
        int lh=depth(root->left);
        if(lh==-1) return -1;
        
        int rh=depth(root->right);
        if(rh==-1) return -1;
        
        if(abs(lh-rh)>1) return -1;

        return 1+max(lh,rh);
    }

    bool isBalanced(TreeNode* root) {
        return depth(root)!=-1;
    }
```

Diameter of Binary Tree:

TC: O(N)
SC: O(h) {
    h: height of the BT
    h=log(Num of nodes) in balanced tree
    h=n in skewed bt 
}

```cpp
class Solution {
public:
    int maxi=0;

    int depth(TreeNode* root){
        if(root==NULL) return 0;
        int lh=depth(root->left);
        int rh=depth(root->right);
        maxi=max(maxi,lh+rh);
        return 1+max(lh,rh);
    }

    int diameterOfBinaryTree(TreeNode* root) {
        
        int i = depth(root);
        return maxi;
    }
};
```