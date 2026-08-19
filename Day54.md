# Day 54-50 Days of Code

 Date: 18-08-2026

---

##  DSA Questions Solved
(Binary Trees)
-[Top View of Binary Tree](https://www.geeksforgeeks.org/problems/top-view-of-binary-tree/1)
-[Bottom View of Binary Tree](https://www.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1)
-[Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

### C++ Code

Top View of Binary Tree
```cpp
vector<int> topView(Node *root) {
        // code here
        if(root==nullptr) return {};
        if(root->left==nullptr && root->right == nullptr) return {root->data};
        map<int, pair<int, int>> mp; //{col,{row,val}}
        queue<pair<Node*,pair<int,int>>> q; //{node, {row, col}}
        int row=0, col=0;
        q.push({root,{row,col}});
        
        while(!q.empty()){
            int size=q.size();
            for(int i=0;i<size;i++){
                Node* node=q.front().first;
                row=q.front().second.first;
                col=q.front().second.second;
                q.pop();
                if(node->left!=nullptr) q.push({node->left, {row+1,col-1}});
                if(node->right!=nullptr) q.push({node->right, {row+1,col+1}});
                if(mp.find(col)==mp.end())
                    mp.insert({col,{row,node->data}});
            }
        }
        vector<int> ans;
        for(auto &col: mp){
                ans.push_back(col.second.second);
        }
        return ans;
    }
```

Bottom View of Binary Tree:

```cpp
class Solution {
public:
    vector<int> bottomView(Node *root) {
        if (root == nullptr) return {};

        map<int, int> mp;  // column -> node value
        queue<pair<Node*, int>> q;  // node, column

        q.push({root, 0});

        while (!q.empty()) {
            auto [node, col] = q.front();
            q.pop();

            // Later node at this column replaces earlier node
            mp[col] = node->data;

            if (node->left != nullptr)
                q.push({node->left, col - 1});

            if (node->right != nullptr)
                q.push({node->right, col + 1});
        }

        vector<int> ans;

        for (auto &col : mp) {
            ans.push_back(col.second);
        }

        return ans;
    }
};
```

Binary Tree Right Side View:
Using BFS:
TC: O(N)
SC: O(N)
```cpp
    vector<int> rightSideView(TreeNode* root) {
        if (root == nullptr) return {};

        vector<int> ans;
        queue<TreeNode*> q;
        q.push(root);

        while (!q.empty()) {
            int size = q.size();

            for (int i = 0; i < size; i++) {
                TreeNode* node = q.front();
                q.pop();

                if (node->left)
                    q.push(node->left);

                if (node->right)
                    q.push(node->right);

                if (i == size - 1)
                    ans.push_back(node->val);
            }
        }

        return ans;
    }
```

Using DFS (Optimal):
TC: O(N)
SC: O(H) {Height of the tree}
```cpp
   class Solution {
public:

    void rightview(TreeNode* node, int level, vector<int>&ans){
        if(node==nullptr) return;
        if(ans.size()==level) ans.push_back(node->val);
        rightview(node->right, level+1, ans);
        rightview(node->left, level+1, ans);
    }

    vector<int> rightSideView(TreeNode* root) {   //level order soln in github
        vector<int> ans;
       rightview(root, 0, ans);
        return ans;
    }
};
```