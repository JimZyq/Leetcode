# generate parenthesis
**Solution:** use the DFS to search for all the possible result for the question, add it to the result.

**Time Complexity:** O(nlogn)

**Space Complexity:** O(nlogn)


```cpp
    void solve (vector<string> &output, string out_string, int left, int right,int n){
        string new_s;
        if(left == n && right ==n){
            output.push_back(out_string);
            return;
        }
        if(left>right && left<n){
            new_s = out_string+'(';
            solve(output, new_s,left+1,right,n);
            new_s = out_string+')';
            solve(output, new_s, left, right+1,n);
        }
        else if(left==right && left<n){
            new_s = out_string+'(';
            solve(output, new_s,left+1,right,n);
        }
        else if(left==n && right<n){
            new_s = out_string+')';
            solve(output, new_s, left, right+1,n);            
        }
    }
    vector<string> generateParenthesis(int n) {
        vector<string> output;
        string out_string = "(";
        if(n == 0) return output;
        solve(output, out_string, 1, 0,n);
        return output;
    }
```