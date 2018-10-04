# Remove Comments
**Solution:** set the flag for the comments(start and end), write the remaining string to the output.

**Time Complexity:** O(mn)

**Space Complexity:** O(mn)


```java
    public List<String> removeComments(String[] source) {
        boolean flag;
        int n;
        char c;
        List<String> output = new ArrayList<String>();
        String temp;
        flag = false;
        temp = "";
        for (int i=0;i<source.length;i++){
            for(int j=0;j<source[i].length();j++){
                c = source[i].charAt(j);
                //check if it's in comment area
                if(flag == true){
                    if(c == '*' && (j+1)<source[i].length()){
                        if(source[i].charAt(j+1)=='/'){
                            flag = false;
                            j = j+1;
                        }
                    }
                    continue;
                }
                //check if it meets the start of comment area "/*"
                if(c == '/' && (j+1)<source[i].length()){
                    if(source[i].charAt(j+1) == '/'){
                        break;
                    }
                    else if(source[i].charAt(j+1) == '*'){
                        flag = true;
                        j = j+1;
                        continue;
                    }
                }
                temp += c;
            }
            if(flag == false){
                if(temp != ""){
                    output.add(temp);
                }
                temp = "";
            }
        }
        return output;
    }
```