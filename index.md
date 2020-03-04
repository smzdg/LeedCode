# Binary Tree Level Order Traversal

Binary tree level order traversal is one of ways to traverse tree.Because of it`s characteristic traverse level by level,it is used frequently.

> ### Problem Description

Given a binary tree,return the level order traversal of its nodes` values.

> ### Example

Given a binary
`[3,9,20,null,null,15,7]`

        
          3
         / \
        9   20
           /  \
          15   7

Return its level order travelsal as:

  [
  [3],
  [9,20],
  [17,7],
  ]
  
  > ### Source
  
  [LeedCode Q102](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)
  
---
> ### Problem Analysis
* General Steps：Read nodes of each levels,and push its children which isn`t null into queue.
* Initial Steps：Push the root into queue.
* Final Steps：If queue is empty which meaning no next level,finish.
* Attention：The nodes are divided by level.

> ### Code

	class Solution {
	public:
		vector<vector<int>> levelOrder(TreeNode* root) {
			vector<vector<int>> ans;
			if(!root) return ans;
			vector<int> res;
			queue<TreeNode*> que;
			que.push(root);
			while(!que.empty()){
				int len=que.size();		//Notice these two lines of code
				for(int i=0;i<len;i++){		//divided nodes by leve
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
	
* Method of divided nodes


	  int len=que.size();
	  for(int i=0;i<len;i++){
		  ...
	  }


