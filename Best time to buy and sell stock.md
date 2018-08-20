# Best time to buy and sell stock
**Solution:** 
Commonly use the O(n^2) to search for the largest profit in all pairs. But in a smarter way, just use the O(n) time to search for the minimum of the previous array and record the maximum profit.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
class Solution {
    public int maxProfit(int[] prices) {
        int l = prices.length;
        if(prices == null || l <= 1) {
            return 0;
        }
        int max,min;
        max = Integer.MIN_VALUE;
        min = Integer.MAX_VALUE;
        for(int i=0;i<l;i++){
            max = Math.max(max,(prices[i]-min));
            min = Math.min(min,prices[i]);
        }
        return max>0?max:0;
    }
}
```