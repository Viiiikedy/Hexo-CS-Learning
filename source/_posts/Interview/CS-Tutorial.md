---
title: CS Tutorial
tags: Interview
---
*<small>[Home](/Home/index.html) > [Interview](/tags/Interview/index.html) > **[CS Tutorial](/2023/09/11/Interview/CS-Tutorial/index.html)</small>***

In this series, I primarily update real-time records of solving problems from ["剑指Offer"](剑指Offer) (Sword Point to Offer) when recommending practice. It's recommended to use either C++ or Java, with a preference for Java.

<h2 id="swift-section">Question 1:Find the duplicate number </h2>
```
class Solution:
    def findRepeatNumber(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            # Iterate through the array from the beginning.
            while i != nums[i]:
                If the current index i and the value nums[i] are not equal, enter/continue the inner loop.
                j = nums[i]
                if nums[i] == nums[j]:
                    # Preconditions: i!=j so nums[i] and nums[j]are two numbers in the array, and they have equal values, indicating a duplicate number. 
                    return nums[i]
                # Swap two values so that nums[j] == j, allowing for further loop evaluation of i and the new nums[i].
                nums[i], nums[j] = nums[j], nums[i]
```

## Question 2:Given a binary tree, where leaf nodes point to adjacent leaf nodes. Find if the given node is a leaf node.
```
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def isLeafNode(node):
    # Check if a node has a left child and a right child.
    if node.left is None and node.right is None:
        return True
    
    # If a node has a left child or a right child, check if they are one of the adjacent leaf nodes.
    if node.left and node.left.right == node or node.right and node.right.left == node:
        return True
    
    return False

# Example
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