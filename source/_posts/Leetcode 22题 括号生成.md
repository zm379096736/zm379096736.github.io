title: Leetcode 22题 括号生成
author: Morphling
tags:
  - 回溯
categories:
  - leetcode
date: 2020-03-14 14:42:00
---
#### 内容来自 [liweiwei1419](https://leetcode-cn.com/problems/generate-parentheses/solution/hui-su-suan-fa-by-liweiwei1419)
> 1. 回溯算法本质上是树形问题的深度优先遍历，深度优先遍历有回退的过程，就需要状态重置 (就是回溯) ；
> 2. 但如果状态变量是字符串的时候，因为字符串的不可变性，在拼接过程中会产生新的字符串，因此每一个状态 (树中的每一个节点) 都是新的字符串，可以不用显式回溯；
> 3. 深度优先遍历用递归去实现的原因：
   (1) 树形结构本身就是递归定义的
   (2) 深度优先遍历要用到 stack, 但可以用函数的栈，把需要的节点状态变量设置为函数的参数，这样就不用再写一个节点类去完成深度优先遍历。
---
![upload successful](/images/pasted-0.png)
---
{% codeblock [深度优先遍历 做减法] [lang:python] [url] [link text] %}
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        cut_str = ""
        res = []
        def dfs(cur_str, left, right): # 输入当前字符串内容, 剩余左括号数量, 剩余右括号数量
        	if left == 0 and right == 0:
            	res.append(cur_str)
                return
            if left > right:
            	return
            if left > 0:
            	dfs(cur_str + "(", left - 1, right)
            if right > 0:
            	dfs(cur_str + ")", ledt, right - 1)
        dfs(cur_str, n, n)
        return res
{% endcodeblock %}