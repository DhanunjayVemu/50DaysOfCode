# Day 43-50 Days of Code

 Date: 19-07-2026

---

##  DSA Questions Solved
(Stacks & Queues)
- [Min Stack](https://leetcode.com/problems/min-stack/)


### C++ Code 


[Min Stack] 
TC: O(1)
SC: O(2N) {because of pairs}
```cpp

class MinStack {
public:

    stack<pair<int,int>> st;
        int mini=INT_MAX;
    MinStack() {
        
    }
    
    void push(int value) {
       mini=min(value,mini);
        st.push({value,mini});
    }
    
    void pop() {
        st.pop();
        if(st.empty()) mini=INT_MAX;
        else mini=st.top().second;
    }
    
    int top() {
        return st.top().first;
    }
    
    int getMin() {
        pair<int,int> p = st.top();
        return p.second;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(value);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```