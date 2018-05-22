# 9. 回文数
## 题目
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。  

示例 1:  

输入: 121  
输出: true  
示例 2:  

输入: -121  
输出: false  
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。  
示例 3:  

输入: 10  
输出: false  
解释: 从右向左读, 为 01 。因此它不是一个回文数。  
进阶:  

你能不将整数转为字符串来解决这个问题吗？  
## 思路
首先，从示例就可以看出回文数一定不是负数。就先排除负数的情况。  
然后再把数字翻转，如果是回文数，就和最初的数相等。  
## 代码实现
```ruby
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0)
            return false;
        int result = 0;
        int result2=x;
        while (x) {
            int temp = result * 10 + x % 10;
            if (temp / 10 != result)
                return 0;
            result = temp;
            x /= 10;
        }
        if(result2==result)
            return true;
        else return false;
    }
};
```
