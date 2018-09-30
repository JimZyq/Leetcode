# pow(x,n)
**Solution:** The key point of this question is to find the boundary of the result, use the divide &conquer in O(logn) time to power the x. And the result is too small, it should output 0.0. 

**Time Complexity:** O(logn)

**Space Complexity:** O(1)


```java
    public double myPow(double x, int n) {
        double output;
        output = 1;
        int carry;
        carry =0;
        if(n<0){
            if(n>Integer.MIN_VALUE) n = 0-n;
            else {
                carry = 1;
                n = Integer.MAX_VALUE;
            }
            x = 1/x;
        }
        while(n>0){
            if(carry ==1) {
                output *= x;
                carry--;
            }
            if(n%2!=0){
                output *= x;
            }
            x *= x;
            n /= 2;
            if(output>0 && output <0.00001) return 0;
        }
        
        return output;
    }
```