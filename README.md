# Leetcode_Day86
# Day 86: Symmetric Tree

**LeetCode Problem:** 101. Symmetric Tree  
**Difficulty:** Easy  
**Language:** Java  
**Topics:** Binary Tree, Recursion, Tree Traversal

## Problem Statement

Given the root of a binary tree, determine whether the tree is symmetric around its center.

A tree is symmetric if its left and right subtrees are mirror images of each other.

## Approach: Recursion

I solved this problem using recursion to compare the left and right subtrees.

### Steps

1. Start by comparing the root's left and right children.
2. If both nodes are `null`, they are symmetric, so return `true`.
3. If only one node is `null`, return `false`.
4. If the values of the two nodes are different, return `false`.
5. Recursively compare:
   - The left child of the left subtree with the right child of the right subtree.
   - The right child of the left subtree with the left child of the right subtree.
6. Return `true` only if both comparisons are successful.

## Java Solution

```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        return check(root.left, root.right);
    }

    public boolean check(TreeNode left, TreeNode right) {
        if (left == null && right == null) {
            return true;
        }

        if (left == null || right == null) {
            return false;
        }

        if (left.val != right.val) {
            return false;
        }

        return check(left.left, right.right)
            && check(left.right, right.left);
    }
}
```

## Example

**Input:**
```text
root = [1,2,2,3,4,4,3]
```

**Output:**
```text
true
```

**Explanation:**

The left and right subtrees are mirror images of each other.

- Both children of the root have value `2`.
- The outermost nodes have value `3`.
- The innermost nodes have value `4`.

Therefore, the tree is symmetric.

## Complexity Analysis

Let `n` be the number of nodes in the tree.

- **Time Complexity:** O(n) — Each node is visited at most once.
- **Space Complexity:** O(h) — The recursive call stack depends on the height `h` of the tree. In the worst case, it can be O(n).

## What I Learned

- How to compare two binary subtrees recursively.
- How to handle `null` nodes correctly.
- Why mirror comparisons require checking opposite children.
- How recursion simplifies problems involving tree structures.

## Key Observation

For a tree to be symmetric, matching node values alone is not enough. Their positions must also be mirrored.

The left child of one subtree must match the right child of the other, and vice versa.

## Takeaway

This problem taught me that sometimes the best way to solve a problem is to break it into smaller, similar problems. Recursion makes that possible by solving each comparison step by step.
