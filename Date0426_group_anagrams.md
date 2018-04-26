# 49. 字母异位词分组
## 题目
给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。  

示例:  

输入: ["eat", "tea", "tan", "ate", "nat", "bat"],  
输出:  
[  
  ["ate","eat","tea"],  
  ["nat","tan"],  
  ["bat"]  
]  
说明：  

所有输入均为小写字母。  
不考虑答案输出的顺序。  

## 思路
这道题思路算比较好想的，特别是在学了map和迭代器之后√
先把string用sort整理一下，这样他们就能按大小排序，也就是说字母异位词因为大小相同会连在一起。  
然后建立两个容器，map用来存每一种字母异位词。
然后就只要遍历一次strs，把字母异位词分别放进去。每次放进去之前都要把temp1排序一下，这样map里面的key才不受字母顺序影响。  
最后用新学的迭代器把每一个子串放进去。  
## 代码实现
```ruby
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        sort(strs.begin(),strs.end());
        vector<vector<string>> result;
        map<string,vector<string>> temp;
        int a=strs.size();
        for(int i=0;i<a;i++)
        {
            string temp1 = strs[i];
            sort(temp1.begin(), temp1.end());
            temp[temp1].push_back(strs[i]);
        }
        map<string, vector<string> >::iterator iter = temp.begin();
        for(int i=0;i<temp.size();i++)
        {
            result.push_back(iter->second);
            iter++;
        }
        return result;
    }
};
```
