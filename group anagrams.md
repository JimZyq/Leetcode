#Group Anagrams 
**Solution:** Use the hash to store the in-order strings, and output using the List<string>.

**Time Complexity:** O(n)

**Space Complexity:** O(n)


```java
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String,List<String>> map = new HashMap<String, List<String>>();
        List<String> l;
        String s;
        List<List<String>> output = new ArrayList<List<String>>();
        
        for(int i=0;i<strs.length;i++){
            char[] tmp = strs[i].toCharArray();
            Arrays.sort(tmp);
            s = String.valueOf(tmp);
            l = map.get(s);
            if(l == null){
                l = new ArrayList<String>();
            }
            l.add(strs[i]);
            map.put(s,l);
        }
        for(String key : map.keySet()){
            output.add(map.get(key));
        }
        return output;
    }
```
