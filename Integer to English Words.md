# Integer to English Words
**Solution:** just split the number and read it. There could be a further solution to use the iterator to reduce the computing times.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
    private String[] UnderTwenty = {"One ","Two ","Three ","Four ","Five ","Six ","Seven ", "Eight ", "Nine ", "Ten "
                                    , "Eleven ", "Twelve ","Thirteen ","Fourteen ","Fifteen ","Sixteen ","Seventeen ",
                                   "Eighteen ","Nineteen "};
    private String[] UnderHundred = {"Twenty ", "Thirty ", "Forty ", "Fifty ","Sixty ","Seventy ", "Eighty ","Ninety "};
    
    public String readIt(int n){
        int tmp=0;
        String res ="";
        if(n>=100){
            tmp = n/100;
            n = n%100;
            res += UnderTwenty[tmp-1];
            res += "Hundred ";
        }
        if(n>=20){
            tmp = n/10;
            n = n%10;
            res += UnderHundred[tmp-2];
            if(n>0){
                res += UnderTwenty[n-1];
            }
        }
        else{
            if(n>0)
                res += UnderTwenty[n-1];
        }
        return res;
    }
    public String numberToWords(int num) {
        if(num == 0) return "Zero";
        int billion, million, thousand, remain;
        String res = "";
        billion = num/1000000000;
        remain = num%1000000000;
        
        million = remain/1000000;
        remain = remain%1000000;
        
        thousand = remain/1000;
        remain = remain%1000;
        if(billion>0){
            res += readIt(billion);
            res += "Billion ";
        }
        if(million>0){
            res += readIt(million);
            res += "Million ";
        }
        if(thousand>0){
            res += readIt(thousand);
            res += "Thousand ";
        }
        res += readIt(remain);
        return res.substring(0,res.length()-1);
    }
```