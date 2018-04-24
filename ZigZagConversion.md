# ZigZagConversion
**Solution:** n = numRows; s = input_string. The key here is to ***press the zigzag*** into a table which has m columns and n rows. Insert the element from the string from left to right and top to down. Just need to separate the first row and last which only contains one element. In this way, I only go throught the string once, use addition space as same as the input_string.
| Columns1  | C1(Cont) | Columns2  | C2(Cont) | ...  | Columns m |
| :------: | :----:  | :---------:| :-----: |:---------:| :-------:|
|   s[0]   |         |   s[2n-2]  |         |    ...    |          |
|   s[1]   | s[2n-3] |   s[2n-1]  |   ...   |    ...    |   ...    | 
|   ...    |  ...    |    ...     |   ...   |    ...    |   ...    |
|  s[n-2]  | s[n]    |     ...    | s[3n-2] |    ...    |   ...    | 
|  s[n-1]  |         |   s[3n-3]  |         |     ...   |          |


**Time Complexity:** O(n)

**Space Complexity:** O(n)

```cpp
class Solution {
public:
    string convert(string s, int numRows) {
        int interval;
        numRows>1?interval=2*numRows-2:interval=1;
        string result; //same length result string
        int n = s.length(),m;//n:string length - m:number of big columns
        n%numRows==0?m=(n/numRows):m=(n/numRows+1);
        for(int j=0;j<numRows;j++){//search the search rows
            for(int i=0;i<m;i++){//search columns
                if((j+i*interval)<n){
                    result += s[j+i*interval];
                    if(j!=0&&j!=(numRows-1)&&((i+1)*interval-j)<n){
                        result += s[(i+1)*interval-j];
                    }
                }
            }
        }
        return result;
    }
};
```