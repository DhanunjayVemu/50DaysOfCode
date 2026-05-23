# Day 1 – 50 Days of Code

 Date: 07-01-2026

---

##  DSA Questions Solved
- [Selection sort](https://www.geeksforgeeks.org/problems/selection-sort/1)
- [Bubble sort](https://www.geeksforgeeks.org/problems/bubble-sort/1)
- [Insertion sort](https://www.geeksforgeeks.org/problems/insertion-sort/1)
- [Merge sort](https://www.geeksforgeeks.org/problems/merge-sort/1)
- [Quick sort](https://www.geeksforgeeks.org/problems/quick-sort/1)

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
Insertion Sort:
``` cpp
void insertionSort(vector<int>& arr) {
        int n =arr.size();
        int j;
        for(int i=1;i<n;i++){
            j=i-1;
            int key=arr[i];
            while(j>=0 && arr[j]>key){
                arr[j+1]=arr[j];
                j--;
            }
            arr[j+1]=key;
        }
    }
```
or
``` cpp
void insertionSort(vector<int>& arr) {
        int n=arr.size();
        int j;
        for(int i=1;i<n;i++){
            int key=arr[i];
            for(j=i-1;j>=0 && arr[j]>key; j--){
                arr[j+1]=arr[j];
            }
            arr[j+1]=key;
        }
    }
```

Merge Sort:
```cpp
void mergeSort(vector<int>& arr, int l, int r) {
        if(l==r) return;
        int mid=(l+r)/2;
        mergeSort(arr, l, mid);
        mergeSort(arr, mid+1, r);
        merge(arr, l, mid, r);
    }
    
    void merge(vector<int> &arr, int l, int mid, int r){
        vector<int> temp;
        int left=l;
        int right=mid+1;
        
        while(left<=mid && right<=r){
            if(arr[left]<=arr[right]){
                temp.push_back(arr[left]);
                left++;
            }
            else {
                temp.push_back(arr[right]);
                right++;
            }
        }
        while(left<=mid){
            temp.push_back(arr[left]);
            left++;
        }
        while(right<=r){
            temp.push_back(arr[right]);
            right++;
        }
        
        for(int i=l; i<=r; i++){
            arr[i] = temp[i-l];
            }
    }
```

Quick sort:
```cpp

void quickSort(vector<int>& arr, int low, int high) {
        
        if(low<high){
            int pivotidx=partition(arr, low, high);
            quickSort(arr, low, pivotidx-1);
            quickSort(arr, pivotidx+1, high);
        }
    }

int partition(vector<int>& arr, int low, int high) {
        int pivot=arr[low];
        int i=low;
        int j=high;
        
    while(i<j){
    
        while(arr[i]<=pivot && i<high){
            i++;
        }
        
        while(arr[j]>pivot && j>low){
            j--;
        }
        if(i<j) swap(arr[i],arr[j]);
    }
        swap(arr[low], arr[j]);
        return j;
        
        
    }
```