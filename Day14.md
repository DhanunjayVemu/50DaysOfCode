# Day 14-50 Days of Code

 Date: 26-01-2026

---

##  DSA Questions Solved
- [Leaders in an array](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1)

####  C++ Code

[Brute Approach] 

Used two loops to compare each element with all elements to its right and check if its the maximum number among the numbers to its right, also appended the last number at the end. 

```cpp
vector<int> leaders(vector<int>& arr) {
        // code here
        
        int n =arr.size();
        vector<int> result;
        int max;
        for(int i=0;i<n-1;i++){
            max=arr[i];
            for(int j=i+1;j<n;j++){
                if(arr[j]>max) max=arr[j]; 
            }
            if(max==arr[i]) result.push_back(arr[i]);
        }
        
        result.push_back(arr[n-1]);
        return result;
    }
```

[Better approach]
I checked the kept on updating the maximum value as I iterated from the right end of the array, and checked with each element is it's greater than it and appended to the resultant array accordingly.

```cpp
vector<int> leaders(vector<int>& arr) {
        // code here
        
        int n =arr.size();
        vector<int> result;
        
        if(n == 0) return result;  
        
        int maxi=arr[n-1];
        result.push_back(arr[n-1]);
        
        for(int i=n-2;i>=0;i--){
            if(arr[i]>=maxi){
                result.push_back(arr[i]);
                maxi=arr[i];
            } 
        }
        reverse(result.begin(),result.end());
        return result;
    }
```
