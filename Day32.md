# Day 32-50 Days of Code

 Date: 21-06-2026

---

##  DSA Questions Solved
(Binary search on answers)
- [Aggressive Cows](https://www.geeksforgeeks.org/problems/aggressive-cows/1)
- []()

### C++ Code

[Aggressive Cows]   

```cpp
bool fun(vector<int> &stalls, int mindist, int k){
        int numCows=1;
        int prevCow=stalls[0];
        int n = stalls.size();
        int flag=0;
        for(int i=1;i<n;i++){
            if((stalls[i]-prevCow)>=mindist){
                prevCow=stalls[i];
                numCows++;
            }
            if(numCows==k){
                flag=1;
                break;
            } 
        }
        if(flag==1) return true;
        return false;
    }
    
    int aggressiveCows(vector<int> &stalls, int k) {
        // code here
        sort(stalls.begin(), stalls.end());
        int low=1;
        int high=*max_element(stalls.begin(), stalls.end())-*min_element(stalls.begin(), stalls.end());           
        int ans=-1;
            
        while(low<=high){
            int mid=(low+high)/2;
            
            if(fun(stalls, mid, k)){
                ans=mid;
                low=mid+1;   
            }
            else high=mid-1;;
                
        }
        return ans;
        
    }
```