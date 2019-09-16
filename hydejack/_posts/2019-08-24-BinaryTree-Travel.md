---
title: BinaryTree Travel
image: /assets/img/blog/aa.jpg
description: >
   介绍二叉树的非递归方式
excerpt_separator: <!--more-->
---
[原文](https://blog.csdn.net/czy47/article/details/81254984)
<!--more-->

# 遍历

```cpp
void preorderTraversalNew(TreeNode *root, vector<int> &path)
{s
    stack< pair<TreeNode *, bool> > s;
    s.push(make_pair(root, false));
    bool visited;
    while(!s.empty())
    {
        root = s.top().first;
        visited = s.top().second;
        s.pop();
        if(root == NULL)
            continue;
        if(visited)
        {
            path.push_back(root->val);
        }
        else
        {
            s.push(make_pair(root->right, false));
            s.push(make_pair(root->left, false));
            s.push(make_pair(root, true));
        }
    }
}
```

>将else中的三行代码交换顺序，就可以实现二叉树的不同遍历方式

# 前序遍历简化版本

```cpp
void preorderTraversalNew(TreeNode *root, vector<int> &path)
{
    stack<TreeNode *> s;
    s.push(root);
    while(!s.empty())
    {
        root = s.top();
        s.pop();
        if(root == NULL)
        {
            continue;
        }
        else
        {
            path.push_back(root->val);
            s.push(root->right);
            s.push(root->left);
        }
    }
}
```