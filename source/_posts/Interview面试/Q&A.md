---
title: Q&A常问题目
tags: Interview面试

---
在这个系列里面，我主要更新面试常问题目

## Question 1:Given a binary tree, where leaf nodes point to adjacent leaf nodes, and vice versa. Find if the given node is a leaf node.
## 问题 1：给定一个二叉树, 其中叶节点指向相邻的叶节点, 反之亦然。查找给定节点是否为叶节点。

```
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def isLeafNode(node):
    # 检查节点是否有左子节点和右子节点
    if node.left is None and node.right is None:
        return True
    
    # 如果节点有左子节点或右子节点，检查它们是否是相邻叶节点之一
    if node.left and node.left.right == node or node.right and node.right.left == node:
        return True
    
    return False

# 示例用法
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)
root.right.left = root.left.right
root.right.right = TreeNode(6)

print(isLeafNode(root.left.left))  # True
print(isLeafNode(root.left.right))  # True
print(isLeafNode(root.right))  # True
print(isLeafNode(root))  # False
```