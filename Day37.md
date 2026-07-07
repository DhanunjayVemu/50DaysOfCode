# Day 37-50 Days of Code

 Date: 07-07-2026

---

##  DSA Questions Solved
(Strings)
- [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/)
- [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)

### C++ Code 

[String to Integer (atoi)]
```cpp
int myAtoi(string s) {
        
        int n = s.size();
        
        long ans=0;
        int numflag=0;
        int neg=1;
        for(int i=0;i<n;i++){
            if(s[i]==' ' && !numflag) continue;
            else if(s[i]=='-' && !numflag) {
                neg*=-1;
                numflag=1;
                continue;
            }
            else if(s[i]=='+' && !numflag){
                numflag=1;
                continue;
            }
            
            if(s[i]-'0'<0 || s[i]-'0'>9){
                break;
            }
            ans=ans*10+(s[i]-'0');
            numflag=1;
            
            if(neg == 1 && ans > INT_MAX) return INT_MAX;
        if(neg == -1 && -ans < INT_MIN) return INT_MIN;

        }
        ans*=neg;
        if(ans>INT_MAX) return INT_MAX;
        if(ans<INT_MIN) return INT_MIN;
        return (int)ans;
    }
```

[Longest Palindromic Substring]
```cpp
int expand(string &s, int left, int right){
        while(left>=0 && right< s.size() && s[left]==s[right]){
            left--;
            right++;
        }
        return right-left-1;
    }

    string longestPalindrome(string s) {
        int n = s.size();
        int maxlen=0, start=0;
        for(int i=0;i<n;i++){
            int even = expand(s, i,i);
            int odd = expand(s,i, i+1);

            int length= max(even, odd);
            
            if(length>maxlen){
                maxlen=length;
                start=i;
            }
        }
        
        return s.substr(start-(maxlen-1)/2, maxlen);
    }
```

