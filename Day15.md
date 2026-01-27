# Day 15-50 Days of Code

 Date: 27-01-2026

---

##  DSA Questions Solved
- [Longest consecutive sequence](https://leetcode.com/problems/longest-consecutive-sequence/description/)

####  C++ Code
[Longest consecutive sequence]

Better approach: 
I first, sorted the given array, then continued only when the number of elements in the array is >=1. Then I checked for the consecutive numbers in the sorted array.

```cpp
int longestConsecutive(vector<int>& nums) {
        
        int n =nums.size();
        sort(nums.begin(), nums.end());

        int cnt=0, longest=1, leastval=INT_MIN;
        if(n==0) return 0;
        for(int i=0;i<n;i++){
            if(nums[i]-1==leastval){
                cnt++;
                leastval = nums[i];
            }
            else if(nums[i]!= leastval){
                cnt=1;
                leastval=nums[i];
            }
            longest=max(longest, cnt);
        }
            return longest;
    }   
```

Optimal approach-
Used a set (avg time complexity O(n)), to keep checking for the element's predecessor, and successor accordingly.

```cpp
int longestConsecutive(vector<int>& nums) {
        
        int n =nums.size();
        if(n==0) return 0;
        unordered_set<int> st;
        for(int i: nums){
            st.insert(i);
        }
        int x;
        int cnt=0;
        int longest=1;
        for(auto it: st){
            if(st.find(it-1) == st.end()) {
                cnt=1;
                x=it;
                while(st.find(x+1)!=st.end()){
                    cnt++;
                    x++;
                }
                longest=max(longest, cnt);
            }

        }
        return longest;
    } 
```