# 16. 最接近的三数之和
## 题目
给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。  
返回这三个数的和。假定每组输入只存在唯一答案。  

例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.  

与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).  

## 思路
这道题首先要把数组排序，找三数之和就比较有规律。  
然后从第二个数开始遍历数组，对于每一个nums[i]都进行一个while循环。  
设定左边最小值是最左边的值，右边最大值一开始是最右边的值。
在while循环里面，计算出一个当前的三数之和。  
如果当前值是比目标值大，右边的数再往左找一个小一点的值。  
如果当前值比目标值小，左边的数往右找一个大一点的值。  
每一次移动之后都用abs算一算当前的值和目标的差与之前的最小差，找到更接近的数就更新一下。  
如果左边或者右边的值以及没法移动又找不到，就退出这个循环。  
## 代码实现
```ruby
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int numssize=nums.size();
        int closest = 66666;
        int temp=0;
        sort(nums.begin(), nums.end());
        for (int i = 1; i < numssize - 1; i++)
        {
            int left = nums[0];
            int right = numssize - 1;
            while(left < i && right > i)
            {
                temp = nums[left] + nums[i] + nums[right];
                if(temp > target)
                    right--;
                else if(temp < target)
                    left++;
                if (temp == target)
                {
                    closest=target;
                    return closest;
                }
                if (abs(closest - target) >= abs(temp - target))
                {
                    closest = temp;
                }
            }
        }
        return closest;
    }
};
```
