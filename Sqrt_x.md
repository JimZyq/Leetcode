# Sqrt(x)
**Solution:** using the existing Math methods to solve 

**Time Complexity:** O(1)

**Space Complexity:** O(1)


```java
    public int mySqrt(int x) {
        double result;
        result = Math.sqrt(x);
        int y = (int)result;
        return y;
    }
```