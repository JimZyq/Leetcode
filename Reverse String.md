# Reverse String
Solution: Loop n/2 times to swap the elements in the string, which take only one *int tmp* as additional space.

Time Complexity: O(n)

Space Complexity:O(1)


```cpp
class Solution {
public:
    string reverseString(string s) {
        int n = s.length();
        char tmp;
        string copy;
        for(int i=0;i<(n/2);i++){
            tmp = s[i];
            s[i] = s[n-1-i];
            s[n-1-i] = tmp;
        }
        return s;
    }
};
```