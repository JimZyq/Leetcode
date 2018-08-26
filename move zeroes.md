# move zeroes
**Solution:** The key idea of this question is to use the O(n) time to solve this prblem. just move the backward numbers froward and fill the rest part with zeroes.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
class Solution {
    public void moveZeroes(int[] nums) {
        if(nums == null) return;
        int n,z;  //z->size of nums; z->number of zeros in nums
        z = 0;
        n = nums.length;
        for(int i=0;i<n;i++){
            if(nums[i] == 0){
                z++;
            }
            else{
                nums[i-z] = nums[i];
            }
        }
        for(int i=(n-z);i<n;i++){
            nums[i] = 0;
        }
        return;
    }
}
```