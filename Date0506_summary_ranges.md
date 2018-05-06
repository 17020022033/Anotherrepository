# 228. 汇总区间
## 题目
给定一个无重复元素的有序整数数组，返回数组中区间范围的汇总。  

示例 1:  

输入: [0,1,2,4,5,7]  
输出: ["0->2","4->5","7"]  
示例 2:  

输入: [0,2,3,4,6,8,9]  
输出: ["0","2->4","6","8->9"]  
## 思路
这道题一开始美滋滋地想用一个二维数组，然后像”0->2"这样就拆成0 -> 2这样三个string放进去。  
写完了报错说返回值有问题，定睛一看才发现要用vector<string>才可以。  
这道题就遍历一下，看看区间的首尾之间隔了多少个，因为vector可以随机查找，就比较方便的放进result就行。  
数组大小是0和1的时候遍历有点麻烦，就当特殊情况处理了。  
## 代码
```ruby
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        int j=0;
        vector<string> result;
        if(nums.size()==0)
            return result;
        if(nums.size()==1)
        {
            result.push_back(to_string(nums[0]));
            return result;
        }
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]+1!=nums[i+1])
            {
                result.push_back(to_string(nums[i]));
            }
            else
            {
                int j=1;
                for(j=i;j<nums.size()&&nums[j]-nums[i]==j-i;j++)
                {
                    continue;
                }
                result.push_back(to_string(nums[i])+"->"+to_string(nums[j-1]));
            i=j-1;
            }
        }
        return result;
    }
};
```
