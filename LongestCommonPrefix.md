# LongestCommonPrefix
**Solution:** The key problem is to check whether the vector is empty or not.
 - Initialize the prefix with value of the first string
 - Loop comparing it with rest strings in the set, only keep the common prefix


**Time Complexity:** O(n)

**Space Complexity:** O(1)


```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string prefix;
        if(strs.size()==0) return "";
        prefix = strs[0];
        string tmp="",cmp="";
        for(int i=1;i<strs.size();i++){
            tmp = "";
            int j=0;
            while(j<strs[i].size()&&j<prefix.size()){
                cmp = strs[i];
                if(prefix[j]==cmp[j]){
                    tmp += prefix[j];
                    j++;
                }
                else 
                    break;
            }
            prefix = tmp;               
        }
        return prefix;
    }
};
```