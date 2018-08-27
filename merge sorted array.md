# merge sorted array
**Solution:** Use O(n) time to start from the biggest number to the smallest.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        if(n == 0){
            return;
        }
        int i,j; //i->iter of nums1, j->iter of nums2
        i=m-1;
        j=n-1;
        if(m == 0){
            while(j>=0) {
                nums1[j] = nums2[j];
                j--;
            }
            return;
        }
        while(i>=0 && j>=0){
            if(nums1[i]>nums2[j]){
                nums1[i+j+1]=nums1[i];
                i--;
            }
            else{
                nums1[i+j+1]=nums2[j];
                j--;
            }
        }
        if(i < 0){
            while(j>=0){
                nums1[j]=nums2[j];
                j--;
            }
        }
        return;
    }
}
```