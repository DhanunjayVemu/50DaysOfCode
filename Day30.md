# Day 30-50 Days of Code

 Date: 19-06-2026

---

##  DSA Questions Solved
(Binary search on answers)
- [Find the Smallest Divisor Given a Threshold](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/)


####  C++ Code

[Find the Smallest Divisor Given a Threshold]
```cpp

int fun(vector<int>& nums, int num){
        int total=0;
        for(int i: nums){
            total+=(i+num-1)/num;
        }
        return total;
    }

    int smallestDivisor(vector<int>& nums, int threshold) {
        
            int low=1;
            int high=*max_element(nums.begin(), nums.end());
            
            int ans;

            while(low<=high){
                int mid=(low+high)/2;
                int val=fun(nums, mid);
                if(val<=threshold){
                    ans=mid;
                    high=mid-1;
                }
                else {
                    low=mid+1;
                }
            }

        return ans;
    }

```