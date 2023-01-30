---
title: 【刷题DAY16】.md
date: 2023-01-30 01:01:30
tags: [刷题] 
categories: [二叉树]
mathjax: true 
---

### 0x00 104.二叉树的最大深度
题目链接：   
104.二叉树的最大深度 https://leetcode.cn/problems/maximum-depth-of-binary-tree/
559.n叉树的最大深度 https://leetcode.cn/problems/maximum-depth-of-n-ary-tree/

#### 0x1 看到题目的第一想法   


#### 0x2 自己实现过程中遇到哪些困难  
- n叉树的最大深度，孩子怎么处理


#### 0x3 今日学习的文章链接，或者视频链接
- https://programmercarl.com/0104.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E5%A4%A7%E6%B7%B1%E5%BA%A6.html

#### 0x4 看完代码随想录之后的想法 
- 二叉树的最大深度    
     - 前序遍历
     - 左右子树的高度较大值+1
```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        
        def getDepth(root):
            if not root:
                return 0
            return 1 + max(getDepth(root.left), getDepth(root.right))
        
        depth = getDepth(root)
        return depth
```
- n叉树的最大深度 
```python
class Solution:
    def maxDepth(self, root: 'Node') -> int:
        if not root:
            return 0
        depth = 0
        for i in range(len(root.children)):
            depth = max(depth, self.maxDepth(root.children[i]))
        return depth + 1
```

#### 0x5 今日收获，记录一下自己的学习时长
- 二叉树的最大深度
     - 前序遍历、层序遍历
- 45min

--- 

### 111. 二叉树的最小深度
题目链接：https://leetcode.cn/problems/minimum-depth-of-binary-tree/

#### 0x1 看到题目的第一想法   

#### 0x2 自己实现过程中遇到哪些困难  


#### 0x3 今日学习的文章链接，或者视频链接
- https://programmercarl.com/0111.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E5%B0%8F%E6%B7%B1%E5%BA%A6.html

#### 0x4 看完代码随想录之后的想法 
- 递归
     - 如果左子树为空，右子树不为空，说明最小深度是 1 + 右子树的深度；反之，右子树为空，左子树不为空，最小深度是 1 + 左子树的深度；如果左右子树都不为空，返回左右子树深度最小值 + 1 。
```python
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        
        if not root:
            return 0
        if not root.left and root.right:
            return 1 + self.minDepth(root.right)
        elif root.left and not root.right:
            return 1 + self.minDepth(root.left)
        elif not root.left and not root.left:
            return 1
        else:
            return 1 + min(self.minDepth(root.right), self.minDepth(root.left))    
```

#### 0x5 今日收获，记录一下自己的学习时长
- 二叉树的最小深度
     - 和最大深度不一样噢！有坑
- 45min

--- 

### 222. 完全二叉树的节点个数
题目链接：https://leetcode.cn/problems/count-complete-tree-nodes/

#### 0x1 看到题目的第一想法   


#### 0x2 自己实现过程中遇到哪些困难  


#### 0x3 今日学习的文章链接，或者视频链接
- https://programmercarl.com/0222.%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E8%8A%82%E7%82%B9%E4%B8%AA%E6%95%B0.html

#### 0x4 看完代码随想录之后的想法 
- 和111. 二叉树的最小深度类似，考虑不用节点的状况，分类讨论
```python
class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        if not root.left and root.right:
            return 1 + self.countNodes(root.right)
        elif root.left and not root.right:
            return 1 + self.countNodes(root.left)
        elif not root.left and not root.right:
            return 1
        else:
            return 1 + self.countNodes(root.right) + self.countNodes(root.left)

```

#### 0x5 今日收获，记录一下自己的学习时长
- 对称二叉树
     - 递归
- 30min

### 待重点复习   
559, 111* , 222

### 总结   
- 递归
     - 二（n）叉树的最大深度
     - 二叉树的最小深度，有坑，分类讨论
     - 完全二叉树的节点个数，分类讨论
