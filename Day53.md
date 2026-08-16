# Day 53-50 Days of Code

 Date: 16-08-2026

---

##  DSA Questions Solved
(Binary Trees)
- [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
- [Boundary Traversal](https://www.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1)
- [Vertical Order Traversal of a Binary Tree](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)

### C++ Code

Binary Tree Zigzag Level Order Traversal:

```cpp
vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
          queue<TreeNode*> q;
          vector<vector<int>> ans;
          if(root==nullptr) return {};
          q. push(root);
          int alt=0;
          while(!q.empty()){
            int size=q.size();
            vector<int> lvl(size);
            int i=0, j=size-1;
            for(int l=0;l<size;l++){
                TreeNode* node=q.front();
                q.pop();
                if(alt==0){
                    lvl[i++]=node->val;
                }
                else{
                    lvl[j--]=node->val;
                }
                if(node->left != nullptr) q.push(node->left);
                if(node->right!=nullptr) q.push(node->right);
            }
            if(alt==0) alt=1;
            else alt=0;
            ans.push_back(lvl);
          } 
          return ans;
    }
```
Boundary Traversal
```cpp
class Solution {
  public:

    void left(Node* root, vector<int>& vec) {
        Node* node = root;

        while(node != nullptr) {
            if(node->left == nullptr && node->right == nullptr)
                break;

            vec.push_back(node->data);

            if(node->left != nullptr)
                node = node->left;
            else
                node = node->right;
        }
    }

    void leaf(Node* root, vector<int>& vec) {
        if(root == nullptr)
            return;

        leaf(root->left, vec);

        if(root->left == nullptr && root->right == nullptr)
            vec.push_back(root->data);

        leaf(root->right, vec);
    }

    void right(Node* root, vector<int>& vec) {
        Node* node = root;
        vector<int> rev;

        while(node != nullptr) {
            if(node->left == nullptr && node->right == nullptr)
                break;

            rev.push_back(node->data);

            if(node->right != nullptr)
                node = node->right;
            else
                node = node->left;
        }

        reverse(rev.begin(), rev.end());

        for(int x : rev)
            vec.push_back(x);
    }

    vector<int> boundaryTraversal(Node* root) {
        if(root == nullptr)
            return {};

        if(root->left == nullptr && root->right == nullptr)
            return {root->data};

        vector<int> ans;

        ans.push_back(root->data);

        if(root->left != nullptr)
            left(root->left, ans);

        leaf(root, ans);

        if(root->right != nullptr)
            right(root->right, ans);

        return ans;
    }
};
```

Vertical Order Traversal of a Binary Tree: ⭐
```cpp
 vector<vector<int>> verticalTraversal(TreeNode* root) {
        
        map<int, map<int, multiset<int>>> mp;
        queue<pair<TreeNode*,pair< int, int>>> q;
        int row=0, col=0;
        q.push({root,{row,col}});
        while(!q.empty()){
            int n = q.size();
            for(int i=0;i<n;i++){
                pair<TreeNode*,pair<int,int>> unit=q.front();
                q.pop();
                TreeNode* node = unit.first;
                int row = unit.second.first;
                int col = unit.second.second;
                if(unit.first->left!=nullptr) q.push({node->left, {row + 1, col - 1}});
                if(unit.first->right!=nullptr) q.push({node->right, {row + 1, col + 1}});
                mp[col][row].insert(node->val);
            }
        }
            vector<vector<int>> ans;
            for(auto &col:mp){
                vector<int> temp;
                for(auto &row: col.second){
                    for(int val: row.second){
                        temp.push_back(val);
                    }
                }
                ans.push_back(temp);
            }
        return ans;
    }
```