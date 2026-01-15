# Day9 – 50 Days of Code

 Date: 15-01-2026

---

##  DSA Questions Solved
- [sort-colors](https://leetcode.com/problems/sort-colors/)
- [Majority Element](https://leetcode.com/problems/majority-element/)

####  C++ Code
[Sort colors]

First method I used was with a hash table to store count of each color and then I pasted those many number of 0s, 1s and 2s in a new vector and made the nums point to the new vector. -surprisngly this worked well, but technically this isn't in-place as asked in the question, TC: avg: O(n), worst: O(n^2) - unordered_map collisions
```cpp
void sortColors(vector<int>& nums) {
        int n=nums.size();
        unordered_map<int,int> mp;
        for(int i=0;i<n;i++){
            mp[nums[i]]++;
        }   
        vector<int> num;
        for(int i=0;i<mp[0];i++){
            num.push_back(0);
        }
        for(int i=0;i<mp[1];i++){
            num.push_back(1);
        }
        for(int i=0;i<mp[2];i++){
            num.push_back(2);
        }
        nums=num;
    }

```
optimized solution of sort colors:
[Dutch national flag algorithm] 

```cpp
void sortColors(vector<int>& nums) {
        int low=0,mid=0,high=nums.size()-1;
        while(mid<=high){
            if(nums[mid]==0){
                swap(nums[low],nums[mid]);
                low++;
                mid++;
            }
            else if(nums[mid]==1){
                mid++;
            }
            else{
                swap(nums[mid],nums[high]);
                high--;
            }
        }
    }
```

[Majority Element]
Moore's algorithm

```cpp
int majorityElement(vector<int>& nums) {

        int n =nums.size();
        int ele=nums[0], cnt=0;
        for(int i=0;i<n;i++){
             if(cnt==0){
             ele=nums[i];
             cnt=1;
             }
             else if(nums[i]==ele)
             cnt++;
             else { 
                cnt--;
             }
        }
            return ele;
            
    }

```