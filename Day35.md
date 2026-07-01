# Day 35-50 Days of Code

 Date: 25-06-2026

---

##  DSA Questions Solved
(Strings)
- [Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)
- [Reverse words in a string](https://leetcode.com/problems/reverse-words-in-a-string/) ⭐
- [Longest common prefix](https://leetcode.com/problems/longest-common-prefix/)
- [Isomorphic strings](https://leetcode.com/problems/isomorphic-strings/)
- [Rotate String](https://leetcode.com/problems/rotate-string/)

### C++ Code

[Remove Outermost Parentheses] 

```cpp
string removeOuterParentheses(string s) {
        
        string result="";
        int level=0;

        for(char ch : s){
            if(ch == '('){
                if(level>0) result+=ch;
                level++;
            }
            else if(ch==')'){
                level--;
                if(level>0) result+=ch;
            }
        }
        return result;
    }
```

[Reverse words in a string]
```cpp
string reverseWords(string s) {

        int n = s.size();
        string result= "";
        
        int i=n-1;
        int start, end;
        while(i>=0){

            while(i>=0 && s[i]==' '){
                i--;
            }
            if(i<0) break;
            end=i;

            while(i>=0 && s[i]!=' '){
                i--;
            }

             start=i+1;
        
            string str= s.substr(start, end-start+1);
            str+=' ';
            result+=str;
            
        }
        result.erase(result.size()-1,1);
        return result;
    }
```

[Longest common prefix]
TC: nlogn 
```cpp

string longestCommonPrefix(vector<string>& strs) {
        
        sort(strs.begin(), strs.end());

        string first=strs[0];
        int n =strs.size();
        string last=strs[n-1];

        int p = min(strs[0].size(), strs[n-1].size());
        string result="";
        for(int i=0;i<p;i++){
            if(first[i]!=last[i]) break;
            result+=first[i];
        }

        return result;
    }
```

[Isomorphic strings]

Good:
TC: O(n)
SC: O(n)
```cpp
 bool isIsomorphic(string s, string t) {
        
        unordered_map<char,char> mp;
        unordered_map<char,char> mp1;

        int n = s.size();

        for(int i=0; i<n ;i++){
            if(mp.find(s[i])!=mp.end()){
                if(mp[s[i]]!=t[i]) return false;
            }
            mp[s[i]]=t[i];

            if(mp1.find(t[i])!=mp1.end()){
                if(mp1[t[i]]!=s[i]) return false;
            }
            mp1[t[i]]=s[i];
        }
        
        return true;

    }
```

Optimal:
TC: O(n)
SC: O(1)
```cpp
bool isIsomorphic(string s, string t) {
        
        int m1[256] = {0};
        int m2[256] = {0};

        int n = s.size();

        for(int i=0; i<n ;i++){
            if(m1[s[i]] != m2[t[i]]) return false;
            m1[s[i]]=i+1;
            m2[t[i]]=i+1;
        }
        
        return true;

    }
```

[Rotate string]

Brute:
TC: O(N^2) 
SC: O(1)
```cpp
bool rotateString(string s, string goal) {
        int n =s.size();
        for(int i=0;i<=n-1; i++){
            rotate(s.begin(), s.begin()+1,s.end());
            if(s.compare(goal)==0){
                return true;
            }
        }
        return false;
    }
```

Optimal:
TC: O(N)
SC: O(1)

```cpp
bool rotateString(string s, string goal) {        
        s+=s;
        int m=goal.size();
        int n=s.size();
        int k=0;
        for(int i=0;i<n;i++){
            while(goal[k]==s[i]){
                k++;
            }
            if(k==m) return true;
        }
        
        return false;

    }
```