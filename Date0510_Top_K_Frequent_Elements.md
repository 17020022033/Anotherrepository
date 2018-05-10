# 347. 前K个高频元素
## 题目
给定一个非空的整数数组，返回其中出现频率前 k 高的元素。  

例如，  

给定数组 [1,1,1,2,2,3] , 和 k = 2，返回 [1,2]。  

注意：  

你可以假设给定的 k 总是合理的，1 ≤ k ≤ 数组中不相同的元素的个数。  
你的算法的时间复杂度必须优于 O(n log n) , n 是数组的大小。  
## 思路
先遍历一次nums，把nums[i]的数据放进frequent里面。用for循环找出前k个数，循环里用迭代器遍历frequent。   
如果找到了最大的，就把它的索引放进结果里，然后把当前这个最大值还原为0，再找下一个数。  
## 代码实现
```ruby
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
		vector<int> result;
		map<int,int> frequent;
		for (int i = 0; i < size; i++) 
     {
			frequent[nums[i]]++;
		}
        int max;
		int index;
		int size = nums.size();
		for (int i = 0; i < k; i++) 
        {
			max = 0; 
            index = NULL;
			for (map<int, int>::iterator it = frequent.begin(); it != frequent.end(); it++) {
				if ((*it).second > max) 
                {
					max = (*it).second;
					index = (*it).first;
				}
					
			}
			result.push_back(index);
			frequent[index] = 0;
		}
		return result;

    }
};
```
