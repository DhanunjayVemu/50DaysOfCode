# Day 42-50 Days of Code

 Date: 18-07-2026

---

##  DSA Questions Solved
(Stacks & Queues)
- [Implementing stack using queue](https://leetcode.com/problems/implement-stack-using-queues/)
- [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)
- [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

### C++ Code 

[Implementing stack using queue]

```cpp
class MyStack {
public:
queue<int> q;
    MyStack() {
        
    }
    
    void push(int x) {
        int n = q.size();
        q.push(x);
        for(int i =0;i<n;i++){
            q.push(q.front());
            q.pop();
        }
    }
    
    int pop() {
        int x = q.front();
        q.pop();
        return x;
    }
    
    int top() {
        return q.front();
    }
    
    bool empty() {
        return q.empty();
    }
};

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack* obj = new MyStack();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->top();
 * bool param_4 = obj->empty();
 */
```

[Implement Queue using Stacks]
```cpp
class MyQueue {
public:
    stack<int> st1;
    stack<int> st2;
    MyQueue() {
        
    }
    
    void push(int x) {
        int n = st1.size();
           for(int i=0;i<n;i++){
            st2.push(st1.top());
            st1.pop();
           }
           st1.push(x);
           for(int i=0;i<n;i++){
            st1.push(st2.top());
            st2.pop();
           }
    }
    
    int pop() {
        int x = st1.top();
        st1.pop();
        return x;
    }
    
    int peek() {
        return st1.top();
    }
    
    bool empty() {
        return st1.empty();
    }
};

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue* obj = new MyQueue();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->peek();
 * bool param_4 = obj->empty();
 */
```


[Valid Parentheses]
```cpp
bool isValid(string s) {

        int n = s.size();
        stack <char> st;

        for(int i=0;i<n;i++){
            if(s[i]=='(' || s[i]=='[' ||s[i]== '{') 
                st.push(s[i]);
            else{
            if(st.empty()) return false;
            char ch=st.top();
            if((s[i]==')' && ch=='(') || (s[i]=='}' && ch=='{' ) ||
             (s[i]==']' && ch=='[')) st.pop();
            else return false;
            }
        }
        return st.empty();
    }
```