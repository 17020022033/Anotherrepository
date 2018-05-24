# 100. 相同的树
## 题目
给定两个二叉树，编写一个函数来检验它们是否相同。  

如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。  

示例 1:  

输入:       1         1  
          / \       / \  
         2   3     2   3  

        [1,2,3],   [1,2,3]  

输出: true  
示例 2:  

输入:      1          1  
          /           \  
         2             2  

        [1,2],     [1,null,2]  

输出: false  
示例 3:  

输入:       1         1  
          / \       / \  
         2   1     1   2  

        [1,2,1],   [1,1,2]  

输出: false  
## 思路
用递归去实现二叉树的遍历。如果p或者q同时到达终点，就是相同的树。
如果p和q一方先到了终点，就是不同的树。
## 代码实现
```ruby
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (p == NULL && q == NULL) {
            return true;
        } else if (p == NULL && q != NULL) {
            return false;
        } else if (p != NULL && q == NULL) {
            return false;
        } else if(p->val != q->val) {
            return false;
        }
        
        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
```
