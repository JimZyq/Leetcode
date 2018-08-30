#remove duplicate from sorted array 
**Solution:** set a current pointer to store the last same number until it matches a new one. use the counter to store how many duplicates in this index position and write it to the front.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums == null || nums.length == 0) return 0;
        int cur,output,count;
        count = 0;
        cur = nums[0];
        output = 1;
        for(int i=1;i<nums.length;i++){
            if(nums[i]!=cur){
                nums[i-count] = nums[i];
                cur = nums[i];
                output++;
            }
            else {
                count++;
            }
        }
        return output;
    }
}
```
