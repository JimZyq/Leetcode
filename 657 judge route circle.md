# judge route circle
**Solution:** super eash

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```cpp
class Solution {
public:
    bool judgeCircle(string moves) {
        int ud=0,lr=0;
        for(int i=0;i<moves.length();i++){
            if(moves[i]=='U'){
                ud++;
            }
            else if(moves[i] == 'D'){
                ud--;
            }
            else if(moves[i] == 'L'){
                lr++;
            }
            else if(moves[i] == 'R'){
                lr--;
            }
        }
        if(ud==0&&lr==0) return true;
        return false;
    }
};
```