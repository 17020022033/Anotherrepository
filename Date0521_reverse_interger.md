# 7. 反转整数
## 题目
给定一个 32 位有符号整数，将整数中的数字进行反转。 

示例 1: 

输入: 123 
输出: 321 
 示例 2:  

输入: -123  
输出: -321  
示例 3:  

输入: 120  
输出: 21  
注意:  

假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−231,  231 − 1]。  
根据这个假设，如果反转后的整数溢出，则返回 0。  
## 思路
这道题其实用很普通的办法就可以AC了，也就是我想到的第一种办法。不过判断溢出还有别的思路→   
```
#define INTMAX (int)0x7fffffff 
#define INTMIN (int)0x80000000
```
这两行代码可以定义整型的最大值和最小值。所以其实可以判断一下输入的数和这两个最大最小值的大小关系，判断有没有溢出。  
## 代码实现
```ruby
class Solution {
public:
    int reverse(int x) {
        int result = 0;
        while (x) {
            int temp = result * 10 + x % 10;
            if (temp / 10 != result)
                return 0;
            result = temp;
            x /= 10;
        }
        return result;
    }
};
```
