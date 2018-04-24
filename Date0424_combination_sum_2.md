# 40. 组合总和 II
## 题目
给定一个数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。

candidates 中的每个数字在每个组合中只能使用一次。

说明：

所有数字（包括目标数）都是正整数。
解集不能包含重复的组合。 
示例 1:

输入: candidates = [10,1,2,7,6,1,5], target = 8,
所求解集为:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
示例 2:

输入: candidates = [2,5,2,1,2], target = 5,
所求解集为:
[
  [1,2,2],
  [5]
]
## 思路
我一开始想的是用set容器把所有可能的结果都放进去，还可以避免重复结果，感觉很方便。
但是要求返回的是动态数组，感觉把结果都放进set再放进vector太…麻烦了。
所以就用了另外一种查重的办法。
这道题首先要准备好三个容器，并且先从小到大排序。
两个动态二维数组：一个用来放所有可能出结果的子集。一个放结果。
再准备一个动态数组来放每一个子集。
放可能出结果的子集要初始化一下，先放一个空的元素进去这样才能进后面的while循环。
用一个for循环遍历candidate里面的每个元素。
如果当前元素比target大，就跳出循环。
否则就先数当前元素有多少个重复的，进for循环。
把每一个可能出结果的子集遍历一次，如果可以就把当前元素放进去。
计算每一个加了之后的子集的sum，如果和target相等，就加进结果里。
## 代码
```ruby
class Solution {
public:
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(),candidates.end());
        vector<vector<int>> result;
        vector<vector<int>> tempresult;
        vector<int> empty;
        tempresult.push_back(empty);
        for(int i=0;i<candidates.size();)
        {
            if(candidates[i]>target)
                break;
            int sameelement=0;
            int temp = candidates[i];
            while(temp==candidates[i])
            {
                i++;
                sameelement++;
            }
            for(int j=0;j<tempresult.size();j++)
            {
                int temp2 = sameelement;
                vector<int> tempsub = tempresult[j];
                while(temp2--)
                {
                    tempsub.push_back(temp);
                    int total = accumulate(tempsub.begin(), tempsub.end(), 0);
                    if(total == target)
                    {
                        result.push_back(tempsub);
                        tempresult.push_back(tempsub);
                    }
                    if(total < target)
                        tempresult.push_back(tempsub);
                }
            }
        }
        return result;
    }
};
```
