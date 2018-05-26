# Number of Islands
**Solution:** Using DFS to search for the possible islands and change the status into '0', using O(n) loop to search all the nodes in the vector. 

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```cpp
class Solution {
public:
    bool valid(int i,int border){
        if(i<border&&i>=0) return true;
        return false;
    }
    void clear_islands (vector<vector<char>>& grid, int n, int m, int x, int y){
        grid[x][y] = '0';
        if(valid(x+1,n))if(grid[x+1][y]=='1') clear_islands(grid,n,m,x+1,y);
        if(valid(x-1,n))if(grid[x-1][y]=='1') clear_islands(grid,n,m,x-1,y);
        if(valid(y-1,m))if(grid[x][y-1]=='1') clear_islands(grid,n,m,x,y-1);
        if(valid(y+1,m))if(grid[x][y+1]=='1') clear_islands(grid,n,m,x,y+1);
    }
    
    int search (vector<vector<char>>& grid,int n, int m) {
        int num_islands=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j] == '1'){
                    clear_islands(grid,n,m,i,j);
                    num_islands = num_islands+1;
                }
            }
        }
        return num_islands;
    }
    int numIslands(vector<vector<char>>& grid) {
        if(grid.size()==0) return 0;
        int n = grid.size();
        int m = grid[0].size();
        return search(grid,n,m);
    }
};
```