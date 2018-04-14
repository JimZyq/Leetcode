# Single Number
**Solution:** I studied this one from the solutions, which is very clever. Use the binary operate XOR to calculate all the numbers in the vector. The number which appears twice will be gone(a XOR a = 0). The remaining number is the single number.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int n = nums.size();
        int a=0;
        for(int i=0;i<n;i++){
            a^=nums[i];
        }
        return a;
    }
};
```