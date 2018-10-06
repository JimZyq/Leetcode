# Rotate Image
**Solution:** fold the matrix up side down and across line.

**Time Complexity:** O(n)

**Space Complexity:** O(1)


```java
    public void rotate(int[][] matrix) {
        int n,tmp;
        n = matrix.length;
        //fold the matrix up side down
        for(int i=0;i<n/2;i++){
            for(int j=0;j<n;j++){
                tmp = matrix[i][j];
                matrix[i][j] = matrix[n-i-1][j];
                matrix[n-i-1][j] = tmp;
            }
        }
        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                tmp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = tmp;
            }
        }
        return;
    }
```