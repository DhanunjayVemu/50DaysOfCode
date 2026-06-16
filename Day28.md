# Day 28-50 Days of Code

 Date: 16-06-2026

---

##  DSA Questions Solved
(Binary search on answers)
- [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)

####  C++ Code

[Koko Eating Bananas]

```cpp
long long fun(vector<int>& piles, int k) {
        long long time = 0;
        for (long long i : piles) {
            time += ceil((double)i / k);
        }
        return time;
    }

    int minEatingSpeed(vector<int>& piles, int h) {
        int n = piles.size();
        int ans = 0;
        int high = *max_element(piles.begin(), piles.end());
        int low=1;
        while(low<=high){
            int mid= low + (high-low)/2;
            long long time=fun(piles, mid);
            if(time<=h) {
                ans=mid;
                high=mid-1;
            }
            else low=mid+1;
        }
        return ans;
    }
```