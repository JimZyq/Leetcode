#Valid Palidrome 
**Solution:** use the double pointer pointing to the front and rear of the string, compare only the alphenumeric charactors. If all match, then TRUE, otherwise false. NOTICE: the upper and lower cases result in the runtime.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
class Solution {
    public boolean isValid(char c){
        if(c >= 'a'&& c <= 'z'){
            return true;
        }
        else if (c >= '0'&&c <= '9'){
            return true;
        }
        return false;
    }
    public boolean isPalindrome(String s) {
        s = s.toLowerCase();
        int n,i,j;
        n = s.length();
        i = 0;
        j = n-1;
        while(i<j){
            if(isValid(s.charAt(i))){
                if(isValid(s.charAt(j))){
                    if(s.charAt(i)!=s.charAt(j)){
                        return false;
                    }
                    i++;
                    j--;
                }
                else {
                    j--;
                    continue;
                }
            }
            else{
                i++;
                continue;
            }
        }
        return true;
    }
}
```
