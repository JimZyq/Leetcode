# Container Most Water
**Solution:** I learned this method from the solution, it's really smart. The water size is only affected by the minimum number of the a<sub>i</sub> and a<sub>j</sub>. We know two facts: 1.The longer the range of the two side is better 2. The longer the minimum of the two edge在 is better. The initial state is the most range. Everytime moves the shorter edge one distance near the middle. Find the maximum size of this traversal. 

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```cpp
class Solution {
public:
    int min(int a, int b){
        int r;
        a<=b?r=a:r=b;
        return r;
    }
    int maxArea(vector<int>& height) {
        int n = height.size();
        int i=0,j=n-1,max=0,tmp;
        while(i<j){
            tmp = (j-i)*min(height[i],height[j]);
            min(max,tmp)==max?max=tmp:max=max;
            min(height[i],height[j])==height[i]?i++:j--;
        }
        return max;
    }
};
```