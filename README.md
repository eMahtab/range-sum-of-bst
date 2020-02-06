# Range Sum of BST
## https://leetcode.com/problems/range-sum-of-bst

Given the root node of a binary search tree, return the sum of values of all nodes with value between L and R (inclusive).

The binary search tree is guaranteed to have unique values.

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

## Implementation :

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int rangeSumBST(TreeNode root, int L, int R) {
        if(root == null)
            return 0;
        int sum[] = new int[1];
        rangeSum(root, L, R, sum);
        return sum[0];
    }
    
    public void rangeSum(TreeNode root, int L, int R, int[] sum){
        if(root != null){
            rangeSum(root.left, L, R, sum);
            if(root.val >= L && root.val <= R)
                sum[0] += root.val;
            rangeSum(root.right, L, R, sum);
        }
    }
}
```

# References :
https://www.youtube.com/watch?v=SIdrJwWp3H0
