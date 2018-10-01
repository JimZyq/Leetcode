# Missing Number
**Solution:** although this one is good, but we can simply sum them up and find the left one.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
    public int missingNumber(int[] nums) {
        if(nums == null) return 0;
        int n = nums.length;
        int output;
        boolean nflag;
        nflag = false;
        output = 0;
        for(int i=0;i<n;i++){
            if((nums[i]%(n+1))==n){
                 nflag = true;
            }
            else{
                nums[nums[i]%(n+1)] += (n+1);
            }
        }
        if(nflag == false) return n;
        for(int i=0;i<n;i++){
            if(nums[i]<(n+1)) output = i;
        }
        return output;
    }
```