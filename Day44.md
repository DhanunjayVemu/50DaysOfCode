# Day 43-50 Days of Code

 Date: 25-07-2026

---

##  DSA Questions Solved
(Stacks & Queues)
- [Infix to postfix](https://www.geeksforgeeks.org/problems/infix-to-postfix-1587115620/1)
- []()

### C++ Code 

[Infix to postfix]
```cpp

    int prec(char c){
        if(c=='^') return 3;
        if(c=='*' || c=='/') return 2;
        if (c=='+' || c=='-') return 1;
        
        return 0;
    }
  
    string infixToPostfix(string& s) {
        // code here
        
            stack<char> st;
            string output="";
            
            for(char ch : s){
                
                //operand
                if((ch>='A' && ch<='Z') || (ch>='a' && ch<='z') || (ch>='0' && ch<='9')){
                    output+=ch;
                }
                
                //brackets
                else if(ch=='(') st.push(ch);
                
                else if(ch==')') {
                    
                    while(!st.empty() && st.top()!='('){
                        output+=st.top();
                        st.pop();
                    }
                    
                    if(!st.empty()){
                        st.pop(); //remove '('
                    }
                        
                }
                
                //operator
                else{
                    
                    while(!st.empty() && st.top()!='(' && (prec(st.top())>prec(ch) ||
                    (prec(st.top())==prec(ch) && ch!='^') )){
                        output+=st.top();
                        st.pop();
                    }
                    
                    st.push(ch);
                    
                }
            }
            
            while(!st.empty()){
                output+=st.top();
                st.pop();
            }
            
            return output;
    }

```