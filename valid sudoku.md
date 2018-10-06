# Valid Sudoku
**Solution:** remember to import the hashtable function, and see the character is number or not.

**Time Complexity:** O(n)

**Space Complexity:** O(n)


```java
    public boolean isNum (char c){
        if(c<='9' && c>='0'){
            return true;
        }
        return false;
    }
    public boolean isValidSudoku(char[][] board) {
        Hashtable<Character,Integer> collumn_table = new Hashtable<Character,Integer>(); 
        Hashtable<Character,Integer> row_table = new Hashtable<Character,Integer>();     
        Hashtable<Character,Integer> block_table = new Hashtable<Character,Integer>();
        
        for(int i=0;i<9;i++){
            for(int j=0;j<9;j++){
                if(collumn_table.get(board[i][j]) != null ||
                        row_table.get(board[j][i]) != null
                                    ){
                    //System.out.println("cr false");
                    return false;
                }
                else{
                    if(isNum(board[i][j])==true){
                        collumn_table.put(board[i][j],1);
                    }
                    if(isNum(board[j][i])==true){
                        row_table.put(board[j][i],1);
                    }
                }
            }
            collumn_table.clear();
            row_table.clear();
        }
        for(int i=0;i<9;i=i+3){
            for(int j=0;j<9;j=j+3){
                for(int m=0;m<3;m++){
                    for(int n=0;n<3;n++){
                        char c = board[i+m][j+n];
                        if(block_table.get(c) != null){
                            //System.out.println(c);
                            //System.out.println("block false");
                            return false;
                        }
                        else{
                            if(isNum(c)==true){
                                block_table.put(c,1);
                            }
                        }
                    }
                }
                block_table.clear();
            }
        }
        return true;
    }
```