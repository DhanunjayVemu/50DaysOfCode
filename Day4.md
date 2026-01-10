# Day 4 – 50 Days of Code

 Date: 10-01-2026

---

##  DSA Questions Solved
- [Union of arrays](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1)
- [Intersection of arrays](https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-array-1587115620/1)

####  C++ Code
[Union of arrays]

```cpp
vector<int> findUnion(vector<int> &a, vector<int> &b) {
      vector<int> uni;
      int pt1, pt2;
      int m=a.size();
      int n=b.size();
      int i=0,j=0;
      
      while(i<m && j<n){
          if(a[i]<b[j]){
              if(uni.empty() || uni.back()!=a[i])
              uni.push_back(a[i]);
              i++;
          }
          else if(a[i]>b[j]){
              if(uni.empty() || uni.back()!=b[j])
              uni.push_back(b[j]);
              j++;
          }
          else {
              if(uni.empty() || uni.back()!=a[i])
              uni.push_back(a[i]);
              i++; j++;
          }
          
      }
      
      while(i<m){
          if(uni.empty() || uni.back()!=a[i]) 
          uni.push_back(a[i]);
              i++;
      }
      while(j<n){
          if(uni.empty() || uni.back()!=b[j])
          uni.push_back(b[j]);
              j++;
      }
      
      return uni;
      
    }
    ```

    [Intersection of two arrays]
    ```cpp
     vector<int> intersection(vector<int> &arr1, vector<int> &arr2) {
        vector<int> v;    
        int ai=0,bi=0;
        int an=arr1.size(),bn=arr2.size();
        while(ai<an && bi<bn){
            if(arr1[ai]==arr2[bi]){
                if(v.empty() || v.back()!=arr1[ai])
                v.push_back(arr1[ai]);
                ai++; bi++;
            }
            
            else if(arr1[ai]>arr2[bi]) bi++;
            else ai++;
        }
        return v;
    }

    ```