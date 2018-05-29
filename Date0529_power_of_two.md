# 231. 2的幂
## 题目

给定一个整数，写一个函数来判断它是否是 2 的幂次方。  

示例 1:  

输入: 1  
输出: true  
示例 2:  

输入: 16  
输出: true  
示例 3:  

输入: 218  
输出: false  
## 思路
先排除输入是1或者0的情况。
然后定义一个temp用来存n的余数。如果余数一直是0，就继续把n除2.
当余数不是0的时候跳出循环，判断满不满足n是2的余数的条件，返回结果。
## 代码实现
```ruby
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n==1)return true;
        if(n==0)return false;
        int temp=0;
        while(temp==0){
            temp=n%2;
            n=n/2;
        }
        if(n==0 && temp==1){
            return true;
        }
        else return false;
    }
};
```
