# Day 22-50 Days of Code

 Date: 08-06-2026

---

##  DSA Questions Solved
- [Floor in a sorted array](https://www.geeksforgeeks.org/problems/floor-in-a-sorted-array-1587115620/1)
- [Ceil in a sorted array](https://www.geeksforgeeks.org/problems/ceil-in-a-sorted-array/1)

####  C++ Code
[Floor in a sorted array] - Floor of a number is the largest number lesser than that number in the array. 

```cpp

   int findFloor(vector<int>& arr, int x) {
		// code here
		int low=0;
		int high=arr.size()-1;
		int ans=-1;
		
		while(low<=high){
		    int mid=(low+high)/2;
		    
		    if(arr[mid]<=x){
		        ans=mid;
		        low=mid+1;
		    }
		    else high=mid-1;
		}
		return ans;
	}

```

[Ceil in a sorted array] - Ceil of a number is the smallest number greater than that number in the array.
i.e., ceil is just the lowerbound of the number.

```cpp
int findCeil(vector<int>& arr, int x) {
        // code here
        
        int lb= lower_bound(arr.begin(), arr.end(), x)-arr.begin();
        if(lb==arr.size()) return -1;
        else return lb;
    }
```