# 137. 只出现一次的数字 II
## 题目
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现了三次。找出那个只出现了一次的元素。  

说明：  

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？  

示例 1:  

输入: [2,2,3,2]  
输出: 3  
示例 2:  

输入: [0,1,0,1,0,1,99]  
输出: 99  
## 思路
以前只出现一次的数字一的时候，题目里是每个元素出现两次，找出只出现一次的，就可以用异或解出来。  
但是这道题出现三次，感觉位运算没那么好做，就用了传统一点的普通遍历。
整理一下数组，然后先看看第一个数和最后一个数是不是符合要求的，如果不是，就进去遍历找。  
不过最后提交通过了之后在样例里面看到了位运算的解法。很妙。&~在代码里是先取反，再与。
## 代码实现
```ruby
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int result=0;
        sort(nums.begin(), nums.end());
        if(nums[0] != nums[1]||nums.size()==1) 
            return nums[0];
        if (nums[nums.size() - 1] != nums[nums.size() - 2])
        {
            return nums[nums.size() - 1];
        }
        for (int i=0; i < nums.size(); i++) {
            if (
                (nums[i] != nums[i - 1] && nums[i] != nums[i + 1]))
            {
                result=nums[i];
                break;
            }
        }
        return result;
    }
};
## 代码实现
```ruby
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int ones = 0, twos = 0;
    for(int i = 0; i < nums.size(); i++){
        ones = (ones ^ nums[i]) & ~twos;
        twos = (twos ^ nums[i]) & ~ones;
    }
    return ones;
    }
};
```
```
