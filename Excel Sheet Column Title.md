# Excel Sheet Column Title
**Solution:** The key point is to translate decimal into 26th number. Have to deal with the 26th char is 'z' and decrease 1.

**Time Complexity:** O(logn)

**Space Complexity:** O()


```java
    public String convertToTitle(int n) {
        int cur;
        StringBuilder sb = new StringBuilder();
        while(n>0){
            cur = n%26;
            n = n/26;
            if(cur == 0){
                cur = 26;
                n = n-1;
            }
            sb.append((char)(cur-1+'A'));
        }
        return sb.reverse().toString();
    }
```