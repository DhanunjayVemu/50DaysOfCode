# Day7 – 50 Days of Code

 Date: 13-01-2026

---

##  DSA Questions Solved
- [Longest subarry with sum k](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)


####  C++ Code
[Longest subarry with sum k]

 ```cpp
 int longestSubarray(vector<int>& arr, int k) {
        int n=arr.size();
        int sum,len=0;
        for(int i=0;i<n;i++){
            sum=0;
            for(int j=i;j<n;j++){
                sum+=arr[j];
                if(sum==k){
                    len=max(j-i+1,len);
                }
            }
        }
        return len;

    }
```