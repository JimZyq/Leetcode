# Valid Parentheses
**Solution:** when comes the '(' or '[' or '{', then push the elements in to the stack and waiting for a right parentheses to pop. If the stack is empty then return true, or otherwise return false.

p.s : the runtime is not good, because of the ascii arithmetic operations are slower.


**Time Complexity:** O(n)

**Space Complexity:** O(m)


```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> mystack;
        for(int i=0;i<s.length();i++){
            if(s[i]=='(' || s[i] == '[' || s[i] == '{'){
                mystack.push(s[i]);
            }
            else if(s[i] == ')' || s[i] == ']' || s[i] == '}'){
                if(mystack.empty()) return false;
                if(((s[i]-mystack.top()) != 1)&&((s[i]-mystack.top()) != 2)){
                    return false;
                }
                mystack.pop();
            }
        }
        if(mystack.empty()){
            return true;
        }
        return false;
    }
};
```