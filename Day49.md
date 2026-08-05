
# Day 49-50 Days of Code

 Date: 05-08-2026

---

##  DSA Questions Solved
(Binary Trees)
- [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)
- [Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)
- [Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)
- [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

### C++ Code

Binary Tree Preorder Traversal
```cpp
void preorder(TreeNode* root, vector<int> & ans){
        if(root==nullptr) return;
        ans.push_back(root->val);
        preorder(root->left,ans);
        preorder(root->right,ans);
    }

    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> ans;
        preorder(root,ans);
        return ans;
    }
```

Binary Tree Inorder Traversal
```cpp

void inorder(TreeNode* root, vector<int>& ans){
        if(root==nullptr) return;
        inorder(root->left,ans);
        ans.push_back(root->val);
        inorder(root->right,ans);
    }

    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> ans;
        inorder(root, ans);
        return ans;
    }
```

Binary Tree Postorder Traversal

```cpp
 void postorder(TreeNode* root, vector<int>& ans){
        if(root==nullptr) return;
        postorder(root->left,ans);
        postorder(root->right,ans);
        ans.push_back(root-> val);
    }

    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> ans;
        postorder(root, ans);
        return ans;
    }
```

Binary Tree Level Order Traversal
```cpp
vector<vector<int>> levelOrder(TreeNode* root) {
        
        queue<TreeNode*> q;
        vector<vector<int>> ans;
        if(root==nullptr) return ans;
        q.push(root);

        while(!q.empty()){
            int size = q.size();
            vector<int> level;
            for(int i=0;i<size;i++){
                TreeNode* node=q.front();
                q.pop();
                if(node->left!=nullptr ) q.push(node->left);
                if(node->right!=nullptr) q.push(node->right);
                level.push_back(node->val);
            }
            ans.push_back(level);
        }
        return ans;

    }
```