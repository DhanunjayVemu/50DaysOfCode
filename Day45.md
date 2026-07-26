
# Day 45-50 Days of Code

 Date: 26-07-2026

---

##  DSA Questions Solved
(Stacks & Queues)
- [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
- []()

### C++ Code 

[Next Greater Element I]

Brute force:
TC: O(N^2)
SC: O(N)
```cpp

    int idx(int x, vector<int>& nums){
        int n=nums.size();
        for(int i=0;i<n;i++){
            if(nums[i]==x) return i;
        }
        return -1;
    }

    int nex(int ind, vector<int>& nums){
        int n =nums.size();
        for(int i=ind;i<n;i++){
            if(nums[i]>nums[ind]) return nums[i];
        }
        return -1;
    }

    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        
        int n1=nums1.size();
        int n2=nums2.size();

        vector<int> ans;

        for(int i=0;i<n1;i++){
            int x = idx(nums1[i],nums2);
            ans.push_back(nex(x,nums2));
        }

        return ans;
    }

```