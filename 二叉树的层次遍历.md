# 二叉树的层次遍历

二叉树的层次遍历在是二叉树遍历的四种遍历方法之一，因为其按照层进行遍历的特点使得其被经常使用。

> ### 问题描述

给定一个二叉树，返回其按照层次遍历的节点值

> ### 示例

给定二叉树 
`[3,9,20,null,null,15,7]`

        
          3
         / \
        9   20
           /  \
          15   7


返回其层次遍历的结果

  [
  [3],
  [9,20],
  [17,7],
  ]
  
  > ### 来源
  
  [LeedCode Q102](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)
  
---
> ### 问题分析
* 一般步骤：读取每一行的节点值，同时将其非空的左右孩子加入栈中
* 起始处理：将根节点加入队列中
* 结束情况：队列为空，即没有下一层
* 注意事项：这里要按照层对节点进行区分

> ### 代码

	class Solution {
	public:
		vector<vector<int>> levelOrder(TreeNode* root) {
			vector<vector<int>> ans;
			if(!root) return ans;
			vector<int> res;
			queue<TreeNode*> que;
			que.push(root);
			while(!que.empty()){
				int len=que.size();		//注意这两行代码
				for(int i=0;i<len;i++){		//使其按层进行区分
					root=que.front();
					que.pop();
					res.push_back(root->val);
					if(root->left!=NULL) que.push(root->left);
					if(root->right!=NULL) que.push(root->right);
				}
				ans.push_back(res);
				res.clear();
			}
			return ans;
		}
	};
	
* 区分层的方法



	  int len=que.size();
	  for(int i=0;i<len;i++){
		  ...
	  }
