# 204. 计数质数
## 题目
统计所有小于非负数整数 n 的质数的数量。  
 
示例:  

输入: 10  
输出: 4  
解释: 小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。  
## 思路
首先处理掉输入2和3的情况，然后从3开始遍历数组。
然后就用厄拉多塞筛法解决。就比如说有一个数表，先把2的倍数全部划去，再把3的倍数划去等等。
如果当你要划去的质数的平方大于 i 时，那么后面没有划去的数都是质数。
## 代码实现
```ruby
class Solution {
public:
    int countPrimes(int n) {
        if (n <= 2) return 0;
        else if (n <= 3) return 1;
        else{
            int count = 1;
            for (int i = 3; i < n; i ++){
                if (i % 2 == 0) 
                continue;
                int j = 2;
                for (; j * j <= i; j ++){
                    if(i % j == 0) 
                    break;
                }
                if (j * j > i) 
                count ++;
            }
            return count;
        }
    }
};
```
