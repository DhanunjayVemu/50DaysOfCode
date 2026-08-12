# Day 52-50 Days of Code

 Date: 11-08-2026

---

##  DSA Questions Solved
(Binary Trees)
- [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) ⭐
- [Same Tree](https://leetcode.com/problems/same-tree/description/)

### C++ Code


[Binary Tree Maximum Path Sum]:

```cpp
int maxpath(TreeNode* root, int&  maxi){
        if(root==nullptr) return 0;
        int lsum=max(0,maxpath(root->left, maxi));
        int rsum=max(0,maxpath(root->right, maxi));
        maxi=max(maxi, lsum+rsum+root->val);
        return max(lsum, rsum)+root->val;
    }

    int maxPathSum(TreeNode* root) {
        int maxi=INT_MIN;
        maxpath(root, maxi);
        return maxi;
    }
```


Same Tree:
(code to understand logic):
```cpp
class Solution {
public:
    bool ans=true;
    void trav(TreeNode* p, TreeNode* q){
        if(p==nullptr && q==nullptr) return;
        if(p==nullptr || q==nullptr){
            ans=false;
            return;
        } 
        if(p->val!=q->val) ans=false;
        trav(p->left, q->left);
        trav(p->right, q->right);
    }

    bool isSameTree(TreeNode* p, TreeNode* q) {
        trav(p,q);
        return ans;

    }
};
```

(Optimal and clean code):
```cpp
class Solution {
public:
    bool trav(TreeNode* p, TreeNode* q) {
        if(p == nullptr && q == nullptr)
            return true;

        if(p == nullptr || q == nullptr)
            return false;

        if(p->val != q->val)
            return false;

        return trav(p->left, q->left) &&
               trav(p->right, q->right);
    }

    bool isSameTree(TreeNode* p, TreeNode* q) {
        return trav(p, q);
    }
};
```
