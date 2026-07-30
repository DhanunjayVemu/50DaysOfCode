# Day 46-50 Days of Code

 Date: 28-07-2026

---

##  DSA Questions Solved
(Stacks & Queues)
- [Next Smaller Element](https://www.geeksforgeeks.org/problems/immediate-smaller-element1142/1)
- [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)

### C++ Code


[Next Smaller Element]
```cpp
vector<int> nextSmallerEle(vector<int>& arr) {
        //  code here
        int n = arr.size();
        stack<int> st;
        vector<int> ans(n);
        
        for(int i=n-1;i>=0;i--){
            while(!st.empty() && arr[i]<=st.top()){
                st.pop();
            }
            ans[i]=st.empty()?-1:st.top();
            st.push(arr[i]);
        }
        
        return ans;
    }
```

[Next Greater Element II]

```cpp

vector<int> nextGreaterElements(vector<int>& nums) {
        
        int n = nums.size();
        vector<int> ans(n);
        stack<int> st;

        int idx=0;

        for(int i=2*n-1;i>=0;i--){
            idx=i%n;
            while(!st.empty() && nums[idx]>=st.top()){
                st.pop();
            }
            if(i<n){
            ans[i]=st.empty()?-1:st.top();
            }
            st.push(nums[idx]);
        }
        return ans;
    }
```