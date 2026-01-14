# Day8 – 50 Days of Code

 Date: 14-01-2026

---

##  DSA Questions Solved
- [Longest subarry with sum k](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)
- [2 sum](https://leetcode.com/problems/two-sum/)

####  C++ Code
[Longest subarry with sum k (obtmized yesterday's code)]

```cpp
int longestSubarray(vector<int>& arr, int k) {
        unordered_map<int,int>store;
        int n=arr.size();
        int sum=0,maxlen=0;
        for(int i=0;i<n;i++){
            sum+=arr[i];
            if(sum==k) {
                maxlen=max(maxlen,i+1);
            }
            int rem=sum-k;
            if (store.find(rem)!=store.end()){
            int len=i-store[rem];
            maxlen=max(len,maxlen);
              }
              if(store.find(sum)==store.end()){
                  store[sum]=i;
              }
            }
            return maxlen; 
    }

```

[2 sum]
Brute force: Used two 'for' loops, and iterating over each pair of elements in the array.
Optimal: Used an unordered map to hash the number and its index, then searched for the difference between the target value and the current value 'i' is pointing at in the hash table, if its present then that is the answer or else I added the pair to the hash table for further checks.

``` cpp
    vector<int> twoSum(vector<int>& nums, int target) {
        int n=nums.size();
        unordered_map<int,int> mapp;
        for(int i=0;i<n;i++){
            int num=nums[i];
            int more=target-num;
            if(mapp.find(more)!=mapp.end()){
                return {mapp[more],i};
            }
            mapp[num]=i;
        }
        return {-1,-1};
    }

```