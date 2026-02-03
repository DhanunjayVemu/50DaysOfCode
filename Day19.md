
# Day 19-50 Days of Code

 Date: 03-02-2026

---

##  DSA Questions Solved
- [ Subarry sum equals k](https://leetcode.com/problems/subarray-sum-equals-k/)

####  C++ Code

Brute: [using 3rd loop iterating k from i to j]

Better:
```cpp
int subarraySum(vector<int>& nums, int k) {
        
        int sum=0;
        int cnt=0;
       for(int i=0;i<nums.size();i++){
            for(int j=i;j<nums.size();j++){
                sum+=nums[j];
                if(sum==k){
                    cnt++;
                }
            }
            sum=0;
       }
       return cnt;
    }
```

Optimal:

```cpp
int subarraySum(vector<int>& nums, int k) {
        unordered_map<int,int> mp;
        mp[0]=1;
        int prefsum=0,cnt=0;
        for(int i=0;i<nums.size();i++){
            prefsum+=nums[i];
            int remove=prefsum-k;
            cnt+=mp[remove];
            mp[prefsum]+=1;
        }
       return cnt;
    }
```