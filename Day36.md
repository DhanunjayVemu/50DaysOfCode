# Day 36-50 Days of Code

 Date: 02-07-2026

---

##  DSA Questions Solved
(Strings)
- 

### C++ Code 
- [Valid Anagram](https://leetcode.com/problems/valid-anagram/)
- [Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)
- [Roman to Integer](https://leetcode.com/problems/roman-to-integer/)

[Valid Anagram]
```cpp
bool isAnagram(string s, string t) {
        
        int arr[256] ={0};
        int m = s.size(), n = t.size();
 
        for(char c : s) arr[c]++;
        for(char c : t) arr[c]--;

        for(int i=0;i<256; i++){
            if(arr[i]!=0) return false;
        }

        return true;

    }
```

[Sort characters by frequency]
Brute O(n^2)
```cpp
string frequencySort(string s) {
        
        unordered_map<char,int> mp;

        for(char c : s){
            mp[c]++;
        }
        string result="";

        int maxi, maxikey;
        int n=mp.size();
        while(n--){
            maxi=INT_MIN;
        for(auto it: mp){
            if(it.second>maxi){
              maxi=it.second;
              maxikey=it.first;  
            } 
        }
        while(maxi--) result+=maxikey;
        mp.erase(maxikey);
     }
        return result;
    
    }
```

Optimal O(nlogn)

```cpp
string frequencySort(string s) {
        
        unordered_map<char,int> mp;

        for(char c : s){
            mp[c]++;
        }
        string result="";

        vector<pair<char, int>> v(mp.begin(), mp.end());

        sort(v.begin(), v.end(), [](auto &a, auto &b){
            return a.second>b.second;
        });

        for(auto it: v){
            result.append(it.second, it.first);
        }
        return result;
    }
```

[Roman to Integer]
```cpp
int romanToInt(string s) {
        
        unordered_map<char, int> mp;

        mp.emplace('I',1);
        mp.emplace('V',5);
        mp.emplace('X',10);
        mp.emplace('L',50);
        mp.emplace('C',100);
        mp.emplace('D',500);
        mp.emplace('M',1000);

        int n = s.size();
        
        int ans=0;
        for(int i=0;i<n-1;i++){
            if(mp[s[i+1]]<=mp[s[i]]) ans+=mp[s[i]];
            else{
                ans-=mp[s[i]];
            }
        }
        ans+=mp[s[n-1]];
        return ans;
    }
```