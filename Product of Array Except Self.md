# Product of Array except Self
**Solution:** multiple the sum from the left and from the right.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
    public int[] productExceptSelf(int[] nums) {
        int sum,tmp;
        sum = 1;
        int n = nums.length;
        int[] output = new int[n];
        for(int i=0;i<nums.length;i++){
            output[i] = sum;
            sum *= nums[i];
        }
        sum = 1;
        for(int i=nums.length-1;i>=0;i--){
            output[i] *= sum;
            sum *= nums[i];
        }
        return output;
    }
```