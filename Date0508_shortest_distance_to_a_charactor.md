# 821. 字符的最短距离
## 题目
给定一个字符串 S 和一个字符 C。返回一个代表字符串 S 中每个字符到字符串 S 中的字符 C 的最短距离的数组。  

示例 1:  

输入: S = "loveleetcode", C = 'e'  
输出: [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]  
说明:  

字符串 S 的长度范围为 [1, 10000]。  
C 是一个单字符，且保证是字符串 S 里的字符。  
S 和 C 中的所有字母均为小写字母。  
## 思路
先遍历一次字符串，找出所有指定字符的位置。  
然后对result里面每个字符，用abs算出他们离每个指定字符的距离，发现更小的距离换一下。
最后返回result。
## 代码实现
```ruby
class Solution {
public:
    vector<int> shortestToChar(string S, char C) {
        vector<int> distance;
        for(int i = 0;i < S.size();i++)
        {
            if(S[i] == C)
                distance.push_back(i);
        }
        vector<int> result(S.size(),10000);
        for(int i = 0;i < distance.size();i++)
        {
            for(int j = 0;j < S.size();j++)
            {
                if(abs(j-distance[i])<result[j])
                    result[j] = abs(j-distance[i]);
            }
        }
        return result;
    }
};
```
