# Day 50-50 Days of Code

 Date: 07-08-2026

---

##  DSA Questions Solved
(Binary Trees)
Iterative methods
- [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)
- [Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)
- [Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)

### C++ Code
Iterative preorder traversal

```cpp
    vector<int> preorderTraversal(TreeNode* root) {
        
        stack<TreeNode*> st;
        vector<int> ans;
        st.push(root);
        if(root==nullptr) return ans;
        
        while(!st.empty()){
            TreeNode* node =st.top();
            st.pop();
            if(node->right!=nullptr) st.push(node->right);
            if(node->left!=nullptr) st.push(node->left);
            ans.push_back(node->val);
        }
        return ans;

    }
```

Iterative Inorder traversal

```cpp
 vector<int> inorderTraversal(TreeNode* root) {
        
        stack<TreeNode*> st;
        vector<int> ans;
        TreeNode* node=root;
        while(true){
            
            if(node!=nullptr){
                st.push(node);
                node=node->left;
            }
            else{
                if(st.empty()) break;
                node=st.top();
                st.pop();
                ans.push_back(node->val);
                node=node->right;
            }
        }
        return ans;
    }
```

Iterative Postorder traversal (using 2 stacks)

```cpp
 vector<int> postorderTraversal(TreeNode* root) {
        
        vector<int> ans;
        stack<TreeNode*> st1;
        stack<TreeNode*> st2;
        st1.push(root);
        TreeNode* node;
        
        if(root==nullptr) return {};

        while(true){
            
            if(!st1.empty()){
                node=st1.top();
                st2.push(node);
                st1.pop();
                if(node->left!=nullptr) st1.push(node->left);
                if(node->right!=nullptr) st1.push(node->right);
            }
            else{
                break;
            }
        }

        while(!st2.empty()){
            ans.push_back(st2.top()->val);
            st2.pop();
        }
        return ans;
    }
```