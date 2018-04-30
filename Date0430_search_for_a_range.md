# 34. 搜索范围
## 题目
给定一个按照升序排列的整数数组 nums，和一个目标值 target。  
找出给定目标值在数组中的开始位置和结束位置。  

你的算法时间复杂度必须是 O(log n) 级别。  

如果数组中不存在目标值，返回 [-1, -1]。  

示例 1:  

输入: nums = [5,7,7,8,8,10], target = 8  
输出: [3,4]  
示例 2:  

输入: nums = [5,7,7,8,8,10], target = 6  
输出: [-1,-1]  

## 思路
这道题用两次二分法实现。  
首先用一次二分法找到目标值开始的地方。  
然后用目标值+1去找目标值结束的地方。  
最后返回就好了。  
比较难想的点大概是怎么去找目标值结束的地方，用目标值+1的话不管目标值结束的下一个数是比它大多少都可以，判断的时候能用就行。  
## 代码实现
```ruby
 class Solution {
 public:
	 vector<int> searchRange(vector<int>& nums, int target) {
     int min = 0, max = nums.size() - 1;
		 while (min <= max) 
		 {
			 int mid = (max + min) / 2;
			 if (nums[mid] < target)
				 min = mid + 1;
			 else
				 max= mid - 1;
		 }
		 int left=min;
         min = 0;
         max = nums.size() - 1;
		 while (min <= max) 
		 {
			 int mid = (max + min) / 2;
			 if (nums[mid] < target+1)
				 min = mid + 1;
			 else
				 max= mid - 1;
		 }
		 int right =min - 1; 
		 if (left < nums.size() && nums[left] == target)
			 return{ left, right };
		 else
			 return{ -1, -1 };
	 }
	 
 };
```
