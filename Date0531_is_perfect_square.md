# 367. 有效的完全平方数
## 题目
给定一个正整数 num，编写一个函数，如果 num 是一个完全平方数，则返回 True，否则返回 False。  

注意：不要使用任何内置的库函数，如  sqrt。  

示例 1：  

输入： 16  

输出： True  
 

示例 2：  

输入： 14  

输出： False  
## 思路
这道题里面我使用了遍历的解法。后来看了下二分法其实更快。  
遍历的话就把num从1开始遍历，遍历到num的一半大假如还没有出现那个对的数，那后面也不可能出现了。那就返回false。  
出现的话就在出现的时候返回true。  
## 代码实现
```ruby
class Solution {
public:
    bool isPerfectSquare(int num) {
        int count = 0;
        if(num==1)
        {
            return true;
        }
        for(int i=0;i<=num/2;i++)
        {
            if(i*i==num)
            {
                return true;
            }
        }
        if(count==0)
        {
            return false;
        }
    }
};
```
