# 409.最长回文串
## 题目
给定一个包含大写字母和小写字母的字符串，找到通过这些字母构造成的最长的回文串。  

在构造过程中，请注意区分大小写。比如 "Aa" 不能当做一个回文字符串。  

注意:  
假设字符串的长度不会超过 1010。  

示例 1:  

输入:  
"abccccdd"  

输出:  
7  

解释:  
我们可以构造的最长的回文串是"dccaccd", 它的长度是 7。  
## 思路
把字符串遍历一遍，用set来存字符串，比较vector没有count这个功能。  
s里面每个字符都用c遍历一遍，如果t里面当前c的数量不是1，就把这个字符放进去。如果是，就去掉。  
t里面找出单数的个数，然后用字符串的大小去减掉单数的个数，再减掉1，就是结果。  
## 代码实现
```ruby
class Solution {
public:
    int longestPalindrome(string s) {
        set<char>t;
        for(char c:s)
        {
            if(t.count(c)!=1)
            {
                t.insert(c);
            }
            else
            {
                t.erase(c);
            }
        }
        int result=s.size()-max(0,(int)t.size()-1);
        return result;
    }
};
```
