# Day11-50 Days of Code

 Date: 20-01-2026

---

##  DSA Questions Solved
- [Best time to buy and sell stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

####  C++ Code
Best time to buy and sell stock

```cpp
 int maxProfit(vector<int>& prices) {
        int n=prices.size();
        int mini=prices[0],profit=0,cost;
        for(int i=1;i<n;i++){
            cost=prices[i]-mini;
            profit=max(profit,cost);
            mini=min(mini,prices[i]);
        }  
        if(profit<0) return 0;
        return profit;
    }
```