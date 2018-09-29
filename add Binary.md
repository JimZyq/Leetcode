#Add Binary
**Solution:** The key point of this question is the char to int, learn StringBuilder class which is very helpfull in the java string problems;

**Time Complexity:** O(n)

**Space Complexity:** O(n)

My method
```java
    public String addBinary(String a, String b) {
        int n,m,c;
        int a_cur,b_cur;
        String output = new String();
        String tmp;
        c = 0;
        n = a.length()-1;
        m = b.length()-1;
        while(n>=0 || m>=0){
            tmp = "";
            if(n>=0){
                a_cur = (a.charAt(n)-'0');  
            }
            else {
                a_cur = 0;
            }
            if(m>=0){
                b_cur = (b.charAt(m)-'0');
            }
            else {
                b_cur = 0;
            }
            tmp += (char)((a_cur+b_cur+c)%2+'0');
            tmp += output;
            output = tmp;
            c = ((a_cur+b_cur+c)/2);
            n--;
            m--;
        }
        if(c != 0){
            output = '1' + output;
        }
        return output;
    }
```
better way
```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int l1 = a.length() - 1, l2 = b.length() - 1, carry = 0;
        while(l1 >= 0 || l2 >= 0) {
            int sum = carry;
            if(l1 >= 0) sum += a.charAt(l1--) - '0';
            if(l2 >= 0) sum += b.charAt(l2--) - '0';
            sb.append(sum % 2);
            carry = sum / 2;
        }
        if(carry != 0) sb.append(carry);
        return sb.reverse().toString();
    }
}
```
