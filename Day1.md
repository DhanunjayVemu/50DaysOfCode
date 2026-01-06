# Day X – 50 Days of Code

 Date: 06-01-2026

---

##  DSA Questions Solved
- [Selection sort](https://www.geeksforgeeks.org/problems/selection-sort/1)
- [Bubble sort](https://www.geeksforgeeks.org/problems/bubble-sort/1)
- [Insertion sort] - 


####  C++ Code
Selection Sort:
```cpp
    void selectionSort(vector<int> &arr) {
        int n=arr.size();
        int min_idx, temp;
        for(int i=0;i<n-1;i++){
            min_idx=i;
            for(int j=i;j<n;j++){
                if(arr[j]<arr[min_idx]) min_idx=j;
            }
            temp=arr[min_idx];
            arr[min_idx]=arr[i];
            arr[i]=temp;
        }
    }
```

Bubble Sort:
``` cpp
void bubbleSort(vector<int>& arr) {
        int n = arr.size();
        int temp;
        for(int i=0;i<n;i++){
            for(int j=0;j<n-i-1;j++){
                if(arr[j+1]<arr[j]){
                   temp=arr[j+1];
                   arr[j+1]=arr[j];
                   arr[j]=temp;
                }
            }
        }
    }
```
