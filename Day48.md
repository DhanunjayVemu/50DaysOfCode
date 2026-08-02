# Day 48-50 Days of Code

 Date: 2-08-2026

---

##  DSA Questions Solved
(Stacks & Queues)
- [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
- [Remove K Digits](https://leetcode.com/problems/remove-k-digits/)

### C++ Code

[Largest Rectangle in Histogram]
Brute Force:
TC: O(N^2)
SC: O(1)
```cpp
         int largestRectangleArea(vector<int>& heights) {
        int n = heights.size();
        int maxi=0;
        int area=0;
        for(int i=0;i<n;i++){
            area=heights[i];
            for(int j=i;j<n;j++){
                area=min(area,heights[j]);
                maxi=max(maxi,area*((j-i)+1));
            }
        }
        return maxi;
    }
```
Better:
TC: 2*O(2N)+O(N)=O(5N) ~ O(N)
SC: O(2N)+O(N)=O(3N) [2 arrs, 1 stack] ~ O(N)

```cpp
int largestRectangleArea(vector<int>& heights) {
        
        int n = heights.size();
        stack <int> st;
        vector<int> nse(n);
        
        for(int i=n-1;i>=0;i--){    //O(N)
            while(!st.empty() && heights[i]<=heights[st.top()]){ //O(N)
                st.pop();
            }    
            nse[i]=st.empty()?n:st.top();
            st.push(i);
        }

        while(!st.empty()) st.pop();

        vector<int> pse(n);
        for(int i=0;i<n;i++){  //O(N)
            while(!st.empty() && heights[i]<=heights[st.top()]){ //O(N)
                st.pop();
            }    
            pse[i] = st.empty() ? -1 : st.top();
            st.push(i);
        }

        int maxi=0;
        for(int i=0;i<n;i++){ //O(N)
            int ns = nse[i];
            int ps = pse[i];

            maxi=max(maxi, (ns-ps-1)*heights[i]);            
        }
        return maxi;

    }
```

Optimal:
TC: O(2N) 
SC: O(N)

```cpp
int largestRectangleArea(vector<int>& h) {
        
        int n = h.size();
        stack <int> st;
        int ele, nse, pse;
        int maxi=0;
        for(int i=0; i<n; i++){  //O(N)
            while(!st.empty() && h[i]<h[st.top()]){ //O(N)
                ele=st.top(); 
                st.pop();
                nse = i;
                pse = st.empty()?-1: st.top();
                maxi=max(maxi, h[ele]*(nse-pse-1));
            }
            st.push(i);
        }

        while(!st.empty()){ //O(1)
            ele=st.top();
            st.pop();
            nse=n;
            pse=st.empty()?-1:st.top();
            maxi=max(maxi, h[ele]*(nse-pse-1)); 
        }
        return maxi;

    }
```


[Remove K Digits]
TC: O(2N) + O(k)
SC: O(N) + O(N)
```cpp
string removeKdigits(string num, int k) {
        
            int n = num.size();
            if(n==k) return "0";
            stack<char> st;
            int l=0;
            for(char i : num){
                while(!st.empty() && i<st.top() && l<k){
                    st.pop();
                    l++;
                }
                st.push(i);
            }
            while(l<k){
                st.pop();
                l++;
            }
            string ans;
            while(!st.empty()){
                ans+=st.top();
                st.pop();
            }
            while(ans.size()>0 && ans.back()=='0')
                ans.pop_back();
             reverse(ans.begin(), ans.end());
            if(ans.empty()) return "0";
            return ans;
    }
```