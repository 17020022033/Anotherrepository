# 39. 组合总和
## 题目
给定一个无重复元素的数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。  

candidates 中的数字可以无限制重复被选取。  

说明：  

所有数字（包括 target）都是正整数。  
解集不能包含重复的组合。   
示例 1:  

输入: candidates = [2,3,6,7], target = 7,  
所求解集为:  
[  
  [7],  
  [2,2,3]  
]  
示例 2:  

输入: candidates = [2,3,5], target = 8,  
所求解集为:  
[  
  [2,2,2,2],  
  [2,3,3],  
  [3,5]  
]  
## 思路
这道题可以用回溯算法。  
可以设想，有一个给定数组2，3，5，target是5.  
寻找的时候，就先从2开始找，因为2比target小，所以要继续找第二个元素。  
第二个元素如果是2，那就要找第三个元素。用回溯的时候发现2，3，5都会大于target，那就都return了。  
第二个元素如果是3，那刚刚好，就把它放进结果里再return，然后不找第三个元素了。  
第二个元素如果是5，那7就比5大了，就直接return。  
然后再从3开始找。3的path里面只考虑3和5这两个数。  
5的path里面只考虑5这个数。  
然后用一个递归实现。  
## 代码实现
```ruby
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> result;
        vector<int> path;
        sort(candidates.begin(),candidates.end());
        helper(candidates,0,0,target,path,result);
        return result;
    }

void helper(vector<int> &nums,int temp,int base,int target,vector<int>& path,vector<vector<int>> & result)
    {
        if(base==target)
        {
            result.push_back(path);
            return ;
        }
        if(base>target)
            return ;
        for(int i=temp;i<nums.size();i++)
        {
            path.push_back(nums[i]);
            helper(nums,i,base+nums[i],target,path,result);
            path.pop_back();
        }
    }
};
```
