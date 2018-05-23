# 35. 搜索插入位置
## 题目
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。  

你可以假设数组中无重复元素。  

示例 1:  

输入: [1,3,5,6], 5  
输出: 2  
示例 2:  

输入: [1,3,5,6], 2  
输出: 1  
示例 3:  

输入: [1,3,5,6], 7  
输出: 4  
示例 4:  

输入: [1,3,5,6], 0  
输出: 0  
## 思路
可以先遍历一次看看能不能直接找到。如果不能，就把目标放进去，然后再排序，再找出目标的索引返回。
后来发现直接用二分法会快一点…
## 代码实现
```ruby
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int i;
        for( i=0;i<nums.size();i++)
        {
            if(nums[i]==target)
                return i;
            
        }
        if(i==nums.size())
        {
            nums.push_back(target);
            sort(nums.begin(),nums.end());
            for(int j=0;j<nums.size();j++)
                if(nums[j]==target)
                    return j;
        }

    }
};
```
