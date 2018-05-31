# 263. 丑数
## 题目
编写一个程序判断给定的数是否为丑数。  

丑数就是只包含质因数 2, 3, 5 的正整数。  

示例 1:  

输入: 6  
输出: true  
解释: 6 = 2 × 3  
示例 2:  

输入: 8  
输出: true  
解释: 8 = 2 × 2 × 2  
示例 3:  

输入: 14  
输出: false   
解释: 14 不是丑数，因为它包含了另外一个质因数 7。  
说明：  

1 是丑数。  
## 思路
丑数一定是正整数，那先排除0和负数。
依次把输入的数除2，3，5直到不能再除，如果这时候这个数是1，就是丑数，不是就不是丑数。
## 代码实现
```ruby
class Solution {
public:
    bool isUgly(int num) {
        if(num<=0) 
            return false;   
        while(num>=2 && num%2==0) 
            num/=2;  
        while(num>=3 && num%3==0) 
            num/=3;  
        while(num>=5 && num%5==0) 
            num/=5;  
        if(num==1) 
            return true;
        else return false;
    }
};
```
