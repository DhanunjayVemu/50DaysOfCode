# Day10 – 50 Days of Code

 Date: 19-01-2026

---

##  DSA Questions Solved
- [Maximum subarry](https://leetcode.com/problems/maximum-subarray/)

####  C++ Code
Maximum subarry

Brute force approach
```cpp
int maxSubArray(vector<int>& nums) {
        int n=nums.size();
        int sum,max_sum=INT_MIN;
         for(int i=0;i<n;i++){
            sum=0;
            for(int j=i;j<n;j++){
                sum+=nums[j];
                if(sum>max_sum){
                    max_sum=sum;
                }
            }
         }
        return max_sum;
    }
```

Kadane's Algorithm
