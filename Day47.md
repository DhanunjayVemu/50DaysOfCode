# Day 47-50 Days of Code

 Date: 1-08-2026

---

##  DSA Questions Solved
(Stacks & Queues)
- [Trapping Rain water](https://leetcode.com/problems/trapping-rain-water/)
- [Sum of Subarray Minimums](https://leetcode.com/problems/sum-of-subarray-minimums/)
- [Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)

### C++ Code


Trapping Rain water
TC: O(3N)~ O(N)
SC: O(2N)
(This is not the optimal solution)

```cpp

int trap(vector<int>& height) {
        
        int n = height.size();
        vector<int> prefixMax(n);
        vector<int> suffixMax(n);

        prefixMax[0] = height[0];

    for(int i = 1; i < n; i++) {
        prefixMax[i] = max(prefixMax[i-1], height[i]);
    }
        
        suffixMax[n-1] = height[n-1];
        for(int i = n-2; i >= 0; i--) {
            suffixMax[i] = max(suffixMax[i+1], height[i]);
        }

        int total = 0;
        for(int i=0;i<n;i++){
            if(prefixMax[i]>height[i] && height[i]<suffixMax[i]){
                total+=min(prefixMax[i],suffixMax[i])-height[i];
            }
        }
        return total;
    }
```


Sum of Subarray Minimums

Brute Force
TC: O(N^2)
SC: O(1)
```cpp
  int sumSubarrayMins(vector<int>& arr) {
        
        int mod=pow(10,9)+7;
        int n = arr.size();
        long long summ=0;
        for(int i=0; i<n; i++ ){
            for(int j=i; j<n ; j++){
                summ+=*min_element(arr.begin()+i, arr.begin()+j+1);
            }
        }
        return (int)summ%mod;
    }
```

Optimal
TC: O(N)
SC: O(N)

```cpp
    int sumSubarrayMins(vector<int>& arr) {
        
            int n = arr.size();
            vector<int> nse, psee;

            nse= fnse(arr);
            psee=fpsee(arr);

            long long total=0;
            const int MOD=1e9+7;

            for(int i=0;i<n;i++){
                int left = i - psee[i];
                int right = nse[i] - i;
            
                total=(total+1LL*left*right * arr[i])% MOD;
            }
        return (int)total;
    }
```

[Asteroid Collision]

```cpp

vector<int> asteroidCollision(vector<int>& ast) {
        
        stack<int> st;
        int n = ast.size();

        for(int i=0;i<n;i++){
            if(st.empty()){
             st.push(ast[i]);
             continue;
            }
            if(ast[i]>0) st.push(ast[i]);

            else{
                
                while(!st.empty() && st.top()>0 && abs(ast[i])>st.top()) 
                    st.pop();

                if(!st.empty() && abs(ast[i])==st.top()) 
                    st.pop();
                else if( st.empty() || st.top()<0)
                    st.push(ast[i]);

            }
        }
        int m = st.size();
        vector<int> ans;
        while(m--){
            ans.push_back(st.top());
            st.pop();
        }

        reverse(ans.begin(), ans.end());
        return ans;
    }
```