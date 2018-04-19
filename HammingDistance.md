
# Hamming Distance
**Solution:** use XOR to differentiate x and y, use logn times to sum up the bits.

**Time Complexity:** O(logn)

**Space Complexity:** O(1)


```cpp
class Solution {
public:
    int hammingDistance(int x, int y) {
        int result=0;
        x ^= y;
        if(x<1){
            return 0;
        }
        while(x>1) {
            result += x%2;
            x /= 2;
        }
        return (result+1);
    }
};
```
