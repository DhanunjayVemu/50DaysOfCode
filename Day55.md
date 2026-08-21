# Day 55-50 Days of Code

 Date: 22-08-2026

---

##  DSA Questions Solved
(Binary Trees)
- [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)
- [Root to Leaf Paths](https://www.geeksforgeeks.org/problems/root-to-leaf-paths/1)
- [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

### C++ Code

Symmetric Tree:
```cpp
class Solution {
public:

    bool trav(TreeNode* node1, TreeNode* node2){
        if(node1==NULL && node2==NULL) return true;
        if (node1==NULL || node2==NULL) return false;
        if(node1->val!=node2->val) return false;

        return trav(node1->left, node2->right) &&
                trav(node1->right, node2->left);
    }

    bool isSymmetric(TreeNode* root) {
        
        if(root==NULL) return true;
        return trav(root->left, root->right);
 
    }
};
```

Root to Leaf Paths:
TC: O(N+L*H) {N becs it visits every node once, copying arr to ans costs L(num of leaf nodes) *H(height of the leaf node)}
SC: O(H+L*H) {H auxillary space from recursion, L *H for ans 2D vector size}
```cpp
    void iter(Node* node, vector<int>& arr, vector<vector<int>>& ans){
            arr.push_back(node->data);
        if(node->left==NULL && node->right==NULL) {
            ans.push_back(arr);
            arr.pop_back();
            return;
        }
           if(node->left) iter(node->left, arr,ans);
            if(node->right) iter(node->right, arr, ans);
            arr.pop_back();
            
        }

class Solution {
  public:
    vector<vector<int>> paths(Node* root) {
        // code here
        vector<int> arr;
        vector<vector<int>> ans;
        if(root==NULL) return ans;
        iter(root, arr, ans);
        return ans;
        
    }
};
```

Lowest Common Ancestor of a Binary Tree:
```cpp
class Solution {
public:
    
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        
        if(root==NULL) return NULL;
        if(root->val==p->val || root->val==q->val) return root;
        TreeNode* left=lowestCommonAncestor(root->left,p,q);
        TreeNode* right= lowestCommonAncestor(root->right,p,q);
        
        // if(left!=NULL && right!=NULL) return root;
        // else if(left==NULL && right!=NULL) return right;
        // else if(left!=NULL && right==NULL) return left;
        // (or)
        if(left && right) return root;
        if(left) return left;
        return right;
        return NULL;
    }
};
```