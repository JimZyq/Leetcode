# Lowest Common Ancestor of a Binary Search Tree
**Solution:** it's a binary search tree, only have to compare the value with the root value.

**Time Complexity:** O(logn)

**Space Complexity:** O(1)


```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root.val<p.val && root.val<q.val) return lowestCommonAncestor(root.right,p,q);
        if(root.val>p.val && root.val>q.val) return lowestCommonAncestor(root.left,p,q);
        return root;
    }
```