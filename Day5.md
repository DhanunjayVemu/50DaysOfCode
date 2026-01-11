# Day5 – 50 Days of Code

 Date: 11-01-2026

---

##  DSA Questions Solved
- [Missing number](https://leetcode.com/problems/missing-number/)
- [Max consecutive ones](https://leetcode.com/problems/max-consecutive-ones/)

####  C++ Code
[Missing number]

```cpp

 int missingNumber(vector<int>& nums) {
        int n =nums.size();
        int xor1=0,xor2=0;
        for(int i=0;i<n;i++){
            xor1=xor1^nums[i];
            xor2=xor2^(i+1);
        }
        return xor1^xor2;
    }
```

[ Max consecutive ones]

```cpp
 int findMaxConsecutiveOnes(vector<int>& nums) {
        int cnt1=0,cnt2=0;
        int n=nums.size();
        for(int i=0;i<n;i++){
            if(nums[i]==1) cnt1++;
            else { 
            if(cnt1>cnt2)
            cnt2=cnt1;
            cnt1=0;}
        }
        if(cnt1>cnt2) return cnt1;
        return cnt2;
    }
```