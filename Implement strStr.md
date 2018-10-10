# 
**Solution:** 

**Time Complexity:** O(n)

**Space Complexity:** O(1)



Stupid using the indexOf
```java
    public int strStr(String haystack, String needle) {
        if(needle.length()==0) return 0;
        return haystack.indexOf(needle);
    }
```