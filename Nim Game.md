# Nim Game
Solution: The key is to find the regulation of the result. Only when number is 4 that player loses.

| round |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | ... |
|  ---  | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  T/F  |  T  |  T  |  T  |  F  |  T  |  T  |  T  |  F  |  T  | ... |

Time Complexity: O(1)

Space Complexity:O(1)
```cpp
class Solution {
public:
    bool canWinNim(int n) {
        if((n%4)==0) return false;
        else return true;
    }
};
```