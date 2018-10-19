# longest palidromic substring
**Solution:** I modify the code three times from 244ms to 12ms, which I think is good enough. The main effor is to find the longest palindrome in the string. And to reduce the time, just have as less as possible character operations. Always update the start and end point of the substring.

**Time Complexity:** O(n^2)

**Space Complexity:** O(1)


```java
    public int countLen(String s,int left,int right){
        int res;
        res = (left==right)?-1:0;
        while(left>=0&&right<s.length()&&s.charAt(left)==s.charAt(right)){
            left--;
            right++;
            res += 2;
        }
        return res;
    }
    public String longestPalindrome(String s) {
        int res;
        int tmp,start, end;
        res = 0;
        start = 0;
        end = 0;
        for(int i=0;i<s.length();i++){
            //even length string
            tmp = countLen(s,i,i);
            if(tmp>res){
                start = i-(tmp-1)/2;
                end = i+(tmp-1)/2+1;
                res = tmp;
            }
            //odd length string
            tmp = countLen(s,i,i+1);
            if(tmp>res){
                res = tmp;
                start = i-tmp/2+1;
                end = i+tmp/2+1;
            }
        }
        return s.substring(start,end);
    }
```