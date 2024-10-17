# Range Sum of BST
## https://leetcode.com/problems/range-sum-of-bst

Given the root node of a binary search tree, return the sum of values of all nodes with value between L and R (inclusive).

The binary search tree is guaranteed to have unique values.

!["BST"](range-sum-bst.png?raw=true)
```
Example 1:

Input: root = [10,5,15,3,7,null,18], L = 7, R = 15
Output: 32

Example 2:

Input: root = [10,5,15,3,7,13,18,1,null,6], L = 6, R = 10
Output: 23
``` 

**Note:**
1. The number of nodes in the tree is at most 10000.
2. The final answer is guaranteed to be less than 2^31.

## Implementation : Considering the input as just Binary Tree
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int rangeSumBST(TreeNode root, int low, int high) {
        int[] result = new int[1];
        rangeSum(root, low, high, result);
        return result[0];
    }

    private void rangeSum(TreeNode node, int low, int high, int[] result) {
        if(node.val >= low && node.val <= high)
           result[0] += node.val;
        if(node.left != null)
           rangeSum(node.left, low, high, result);
        if(node.right != null)
           rangeSum(node.right, low, high, result);
    }
}
```

## Implementation 2 : Utilizing the fact that we are given a BST, reducing the search space
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int rangeSumBST(TreeNode root, int low, int high) {
        int[] result = new int[1];
        rangeSum(root, low, high, result);
        return result[0];
    }

    private void rangeSum(TreeNode node, int low, int high, int[] result) {
        if(node.val >= low && node.val <= high)
           result[0] += node.val;
        if(node.left != null && node.val > low)
           rangeSum(node.left, low, high, result);
        if(node.right != null && node.val < high)
           rangeSum(node.right, low, high, result);
    }
}
```

# References :
https://www.youtube.com/watch?v=SIdrJwWp3H0
